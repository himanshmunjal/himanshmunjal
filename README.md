<h1 align="center">Hi 👋, I'm Himansh Munjal</h1>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?color=00C2FF&size=28&center=true&vCenter=true&width=900&lines=Backend+%26+Distributed+Systems;LLM+Inference+%2B+RAG+Systems;Java+%2B+Go+%2B+Python+%2B+SQL;" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=himanshmunjal&label=Profile%20views&color=0e75b6&style=flat" alt="himanshmunjal" />
</p>

---

## 🧠 About Me

🎓 B.Tech CSE (Data Science) @ VIT Vellore — CGPA 8.47, 2023–2027
💼 Full Stack Intern @ Beryl Systems — shipped 5 production Go REST APIs for ~500 daily users and cut p95 latency ~7x (850 ms → 110 ms)
🚀 Building backend and distributed systems, and applied ML / LLM systems
🎯 Ship production-grade software end to end, and measure it until the numbers hold up

---

## 🚀 Featured Projects

### 🗄️ JCache — Redis-Compatible Distributed Cache Server
Java cache server (~18K LOC, 6 Maven modules) with O(1) LRU, LFU and self-tuning ARC eviction.
- 3 pluggable concurrency modes (global RW lock, 16-way striping, lock-free reads), benchmarked with JMH
- Non-blocking Netty server speaking a custom protocol and RESP (works with redis-cli/Jedis): **~65K ops/s at p99 ≈ 0.2 ms**
- Hit rates on a 256-entry cache, 1,000 Zipf keys: LRU 74.2%, LFU 81.0%, ARC 76.6%; LFU 61.7% vs. LRU 51.0% on scan-heavy loads
- Client-side consistent hashing (150 virtual nodes) moves only ~1/N of keys on node join/leave; append-only log + atomic snapshots
- 500+ JUnit tests, CI/CD, Docker image, 3-node compose cluster

**Tech:** Java 17, Netty, JMH, Docker, GitHub Actions
[GitHub](https://github.com/himanshmunjal/JCache) · `docker pull himanshmunjal/jcache`

---

### 🔗 LinkPlus — URL Shortener, QR Code & Analytics Platform
Full-stack Go (Gin) shortener with a layered handler/service/repository design.
- Redis cache-aside redirects + goroutine click tracking (device, GeoIP, hashed IP) with no added redirect latency
- QR codes encode a hidden short URL, so every scan flows through the redirect pipeline; scan log and counter commit in one DB transaction
- Atomic sliding-window rate limiter as a Redis Lua script that fails open
- JWT auth with bcrypt and rotating refresh tokens stored only as SHA-256 hashes

**Tech:** Go, Gin, PostgreSQL, Redis, React, Tailwind CSS
[GitHub](https://github.com/himanshmunjal/LinkPlus)

---

### 🧮 Adaptive Token-Aware KV Cache Compression for LLM Inference
Mixed-precision KV cache (FP16/INT8/INT4) that moves tokens between tiers by importance instead of dropping them. A drop-in `transformers.Cache`.
- **~40% KV memory saved at ≤0.16% perplexity loss** on Qwen2.5-1.5B and Phi-3-mini; up to 56% at 0.20% (1.94 GB → 1.15 GB, 8K context)
- Per-channel key / per-token value INT4 quantization cut key reconstruction error 17.3%
- 3 importance scorers (H2O, VATP, KeyDiff); ~1.8x faster adaptive decoding (12 → 22 tok/s)
- Leak-proof eval (perplexity, Needle-in-a-Haystack, LongBench); matched FP16 retrieval in 17 of 18 cells

**Tech:** Python, PyTorch, HuggingFace Transformers
[GitHub](https://github.com/himanshmunjal/Adaptive-KV-Cache)

---

### 📊 ARS-Stack — Adaptive Resampler Selection for Imbalanced Classification
Picks SMOTE, ADASYN, SMOTE-Tomek or SMOTE-ENN per minority-class cluster, feeding a confidence-weighted RF + XGBoost + LightGBM ensemble.
- Leakage-free study on **28 datasets, 9 variants, 3,780 CV folds** (Friedman/Nemenyi, Holm-corrected Wilcoxon, Bayesian equivalence tests)
- Beats SMOTE-ENN (Bayesian P ≥ 0.96) but is practically equivalent to plain SMOTE; resampling mainly helps at ≤75 minority samples
- Found and fixed 5 evaluation flaws that inflate new methods; IEEE-format paper draft
- Reproducible MLOps stack (DVC, MLflow, Prefect, FastAPI, Docker) with 130+ pytest tests in CI

**Tech:** Python, scikit-learn, XGBoost, LightGBM, MLflow, DVC, Docker
[GitHub](https://github.com/himanshmunjal/ARS-Stack)

---

### 🤖 CodeSense — AI-Powered Codebase Intelligence Engine
Hybrid RAG over source code for file/line-cited Q&A and blast-radius impact analysis.
- Tree-sitter AST parsing across 5 languages, dual-vector Qdrant index (semantic + node2vec call-graph) and cross-encoder reranking
- Diagnosed a retrieval failure by measuring embedding quality directly, swapped in a contrastively trained model and recalibrated the confidence gate
- Async Celery/Redis ingestion; audited on gin, gson, fastapi and react-use, fixing 20+ parsing and grounding bugs

**Tech:** Python, FastAPI, Qdrant, Tree-sitter, Celery, React, Docker
[GitHub](https://github.com/himanshmunjal/CodeSense-AI)

---

### 📈 OSS Contributor Activation & Retention — Survival Analysis on GitHub Events
8-stage DuckDB SQL pipeline over **13M GitHub Archive events** (1.14M PRs) modeling first-touch to second-PR for 17K contributors across 297 repos.
- 35% of first-time contributors return within 30 days (29% if the first PR merged vs. 17% if not)
- Fast first response is a repo-level effect, not a PR-level one: pooled Cox HR 1.69 drops to 0.99 within repos
- Power analysis for a repo-randomized experiment (~663 repos per arm to detect +5 pp)

**Tech:** Python, DuckDB, SQL, lifelines, statsmodels, FastAPI, Streamlit
[GitHub](https://github.com/himanshmunjal)

---

## ⚙️ Tech Stack

**Languages:** `Java` `Go` `Python` `SQL` `JavaScript` `R`
**AI / ML:** `PyTorch` `HuggingFace` `scikit-learn` `XGBoost` `LightGBM` `RAG` `Qdrant` `ChromaDB`
**Backend & Systems:** `Netty` `Gin` `FastAPI` `REST` `WebSockets` `JWT` `Consistent Hashing` `Multithreading`
**Data & MLOps:** `PostgreSQL` `Redis` `BigQuery` `DuckDB` `MLflow` `DVC` `Prefect` `Celery` `Docker` `GitHub Actions`
**Frontend:** `React` `Tailwind CSS`

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=himanshmunjal&show_icons=true&theme=tokyonight&hide_border=true" />
  <img src="https://streak-stats.demolab.com?user=himanshmunjal&theme=tokyonight&hide_border=true" />
</p>

---

## 🏆 Experience & Leadership

- 💼 **Full Stack Intern, Beryl Systems** — 5 production REST APIs (Go, JWT, RBAC) for ~500 daily users; p95 latency 850 ms → 110 ms; fixed 4 security vulnerabilities (OWASP)
- 🎯 **Manager, General Enquiry Team, VIT** — led a 15-member team resolving 500+ student queries
- 🧩 **200+ problems solved on LeetCode**, 50 Days Badge

---

## 🎯 Currently

- 🏃 Finishing benchmarks and significance testing for a Spectral-Gated Dual-Attention BiGRU for human activity recognition
- 📚 Learning Apache Kafka, Airflow, and BigQuery for data engineering

---

## 🌐 Portfolio & Contact

🔗 Portfolio: [himansh-portfolio.vercel.app](https://himansh-portfolio.vercel.app/)
💼 LinkedIn: [linkedin.com/in/himansh-munjal](https://www.linkedin.com/in/himansh-munjal/)
📧 Email: munjalhimansh2211@gmail.com

---

> I build systems that work under real load, from lock-free caches to retrieval-augmented pipelines, and I test them until the numbers hold up.
