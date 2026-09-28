<h1 align="center">Hi 👋, I'm Himansh Munjal</h1>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?color=00C2FF&size=28&center=true&vCenter=true&width=900&lines=Backend+Engineering+%7C+Distributed+Systems;Machine+Learning+%2B+LLM+Systems;Java+%2B+Go+%2B+Python+%2B+System+Design;" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=himanshmunjal&label=Profile%20views&color=0e75b6&style=flat" alt="himanshmunjal" />
</p>

---

## 🧠 About Me

🎓 B.Tech CSE (Data Science) @ VIT Vellore — CGPA 8.47, 2023–2027
💼 Full Stack Intern @ Beryl Systems — cut p95 API latency 7x (850 ms → 110 ms) on production Go services
🚀 Building distributed systems, backend infrastructure, and applied ML / LLM systems
⚙️ Focus areas: concurrency & system design, retrieval-augmented systems, LLM inference optimization
🎯 Mission: ship production-grade software end to end — from system design to deployment

---

## 🚀 Featured Projects

### 🗄️ JCache — Distributed In-Memory Cache Server
Redis-style distributed cache in Java (~28K lines, 7 Maven modules) with LRU/LFU/ARC eviction and TTL expiry.
- 3 interchangeable concurrency modes: global lock, 16-way lock striping, lock-free (ConcurrentHashMap + CAS)
- Lock striping gave 4.4x single-lock throughput at 16 threads; lock-free mode hit 6.2M ops/sec (JMH, Zipfian workload)
- Non-blocking Netty TCP server, custom protocol, ~95K ops/sec across 8 clients, sub-ms p99
- Client-side consistent hashing (MD5, 150 virtual nodes/server), crash-safe via append-only log + atomic snapshots
- 319 JUnit tests, GitHub Actions CI/CD, Docker image + 3-node docker-compose cluster

**Tech:** Java 17, Netty, Multithreading, Consistent Hashing, JMH, Docker, GitHub Actions
[GitHub](https://github.com/himanshmunjal) · `docker pull himanshmunjal/jcache`

---

### 🔗 LinkPlus — URL Shortener, QR Code & Analytics Platform
Full-stack URL shortener in Go (Gin) with a layered handler/service/repository design.
- Redis cache-aside redirects + goroutine-based click tracking (device, GeoIP, hashed IP) with zero added latency
- QR codes route every scan through the redirect pipeline for accurate analytics
- Atomic sliding-window rate limiter as a Redis Lua script, fails open if Redis is down
- JWT (HS256) auth with bcrypt + rotating refresh tokens; per-user analytics dashboards on tuned Postgres schemas

**Tech:** Go, Gin, GORM, PostgreSQL, Redis, React, Tailwind CSS, Recharts
[GitHub](https://github.com/himanshmunjal)

---

### 🔒 Ephemeral Share — End-to-End Encrypted Temporary Sharing
Cross-device file/text sharing platform with real-time Shared Workspace mode and 5-minute session expiry.
- Browser-side AES-256-GCM encryption; decryption keys never touch the server, shared only via URL fragments
- Redis TTL + keyspace-event cleanup for expired S3 objects and live WebSocket connections
- Go/Gin REST APIs + React workflows for encrypted drag-and-drop uploads and live content feeds

**Tech:** Go, Gin, React, Redis, PostgreSQL, WebSockets, S3/MinIO
[GitHub](https://github.com/himanshmunjal)

---

### 🤖 CodeSense — AI-Powered Codebase Intelligence Engine
Hybrid retrieval-augmented system over source code for grounded, file/line-cited code Q&A.
- Tree-sitter AST parsing across 5 languages + dual-vector Qdrant index (semantic + node2vec call-graph embeddings)
- Diagnosed a retrieval failure by measuring embedding quality directly, swapped in a contrastively-trained model, and recalibrated confidence gating against real score distributions
- Async Celery/Redis ingestion pipeline; audited against real repos (gin, gson, fastapi, react-use), fixing 20+ parsing/grounding bugs

**Tech:** Python, FastAPI, Qdrant, Tree-sitter, Redis/Celery, React, Docker
[GitHub](https://github.com/himanshmunjal)

---

### 🧮 Adaptive Token-Aware KV Cache Compression for LLM Inference
Mixed-precision KV cache (FP16/INT8/INT4) that moves tokens between tiers by importance instead of dropping them.
- Drop-in `transformers.Cache`: ~40% KV memory reduction at ≤0.16% perplexity loss on Qwen2.5-1.5B and Phi-3-mini
- Up to 56% memory savings at 0.20% perplexity loss (1.94 GB → 1.15 GB on Phi-3-mini, 8K context)
- Three importance scorers (H2O, VATP, KeyDiff); ~1.8x faster adaptive decoding (12 → 22 tok/s)
- Leak-proof eval suite (perplexity, Needle-in-a-Haystack, LongBench); matched FP16 retrieval in 17/18 test cells

**Tech:** Python, PyTorch, HuggingFace Transformers
[GitHub](https://github.com/himanshmunjal)

---

### 📊 ARS-Stack — Adaptive Resampler-Selection Ensemble *(in progress — training & scoring pending)*
Framework for imbalanced classification that picks a resampling strategy per minority-class region instead of globally.
- Cluster-level diagnostics (k-NN overlap, density) select among SMOTE/ADASYN/SMOTE-Tomek/SMOTE-ENN with interpretable rules
- Confidence-weighted RF + XGBoost + LightGBM ensemble; leak-free, fold-local fitting of scaling, resampling, weights & thresholds
- Full MLOps stack: DVC, MLflow, Prefect, FastAPI, Docker, GitHub Actions CI; publication-grade stats protocol (Wilcoxon, Holm correction, Friedman tests) implemented, benchmark runs in progress

**Tech:** Python, scikit-learn, imbalanced-learn, XGBoost, LightGBM, FastAPI, MLflow, DVC, Prefect, Docker
[GitHub](https://github.com/himanshmunjal)

---

### ⚡ GridSense — Smart Grid Demand Forecasting & Anomaly Detection
Multi-zone electricity demand forecasting with uncertainty-aware modeling.
- 2-layer LSTM + Monte Carlo Dropout, 10 engineered features (temporal encodings, lags, rolling stats)
- 21.9–36.9 kWh MAE / 32.0–53.8 kWh RMSE across 4 grid zones
- Unsupervised anomaly detection via LSTM Autoencoder trained only on normal consumption windows

**Tech:** Python, PyTorch, FastAPI, React, LSTM, Time-Series Forecasting
[GitHub](https://github.com/himanshmunjal)

---

### 🏗️ Customer 360 Data Warehouse — Incremental ETL on Real E-Commerce Data
Production-style incremental warehouse on the real Olist dataset (99K orders, 96K customers).
- Incremental SCD Type 2 merge, verified byte-identical across day-by-day, batch, and random-order loads
- 30+ statement idempotent SQL pipeline, ported to partitioned/clustered BigQuery with automated cross-engine parity checks
- Leakage-safe ML model with forward-chaining validation; 19 SQL integrity assertions + 12 pytest scenarios; CI with Postgres service container; Streamlit dashboard

**Tech:** Python, PostgreSQL, BigQuery, scikit-learn, GitHub Actions, Streamlit
[GitHub](https://github.com/himanshmunjal)

---

## ⚙️ Tech Stack

### 👨‍💻 Languages
`Java` `Go` `Python` `SQL` `JavaScript`

### 🧠 AI / ML / DL
`PyTorch` `HuggingFace Transformers` `scikit-learn` `XGBoost` `LightGBM` `NLP` `RAG` `Vector DBs (Qdrant)`

### 🌐 Backend & Systems
`Netty` `Gin` `FastAPI` `REST APIs` `WebSockets` `TCP/IP` `Multithreading` `Consistent Hashing` `JWT` `RBAC`

### 🗄️ Databases & MLOps
`PostgreSQL` `Redis` `MongoDB` `BigQuery` `MLflow` `DVC` `Prefect` `Celery` `Docker` `GitHub Actions`

### 📊 Data & Analytics
`NumPy` `Pandas` `SciPy` `Matplotlib` `Power BI` `Tableau`

### 🎨 Frontend
`React.js` `Tailwind CSS`

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=himanshmunjal&show_icons=true&theme=tokyonight&hide_border=true" />
  <img src="https://streak-stats.demolab.com?user=himanshmunjal&theme=tokyonight&hide_border=true" />
</p>

---

## 🏆 Experience & Leadership

- 💼 Full Stack Intern, Beryl Systems Pvt. Ltd. — built and deployed 5 production REST APIs (Go, JWT, RBAC) for ~500 daily active users; cut p95 latency 850 ms → 110 ms
- 🎯 Creative Head, Matrix — The Multimedia Club, VIT — led logistics for 6+ events, mentored juniors, raised feedback scores 30%
- 🧩 200+ problems solved on LeetCode (global rank under 850K)

---

## 🎯 Current Focus

- Distributed systems & backend infrastructure (Java, Go)
- LLM inference optimization & retrieval-augmented systems
- Data engineering (Airflow, Kafka, BigQuery)
- DSA

## 🌐 Portfolio & Contact

🔗 Portfolio: [himansh-portfolio.vercel.app](https://himansh-portfolio.vercel.app/)
📂 GitHub: [github.com/himanshmunjal](https://github.com/himanshmunjal)
💼 LinkedIn: [linkedin.com/in/himansh-munjal](https://www.linkedin.com/in/himansh-munjal/)
📧 Email: munjalhimansh2211@gmail.com

---

> I build systems that work under real load — from lock-free caches to retrieval-augmented pipelines — and I test them until the numbers hold up.

⭐️ *If you're building something exciting in backend, distributed systems, or applied ML — let's connect.*
