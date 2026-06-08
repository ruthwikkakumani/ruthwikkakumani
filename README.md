<div align="center">

# Ruthwik Kakumani

**Backend Engineer · Distributed Systems · Go**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-ruthwikkakumani-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/ruthwikkakumani)
[![LeetCode](https://img.shields.io/badge/LeetCode-Rating_1652-FFA116?style=flat-square&logo=leetcode&logoColor=white)](https://leetcode.com/u/ruthwikkakumani/)
[![Portfolio](https://img.shields.io/badge/Portfolio-ruthwik.vercel.app-000?style=flat-square&logo=vercel)](https://ruthwik-portfolio.vercel.app/)
[![Email](https://img.shields.io/badge/Email-ruthwikkakumani@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:ruthwikkakumani@gmail.com)

</div>

---

I build systems where correctness and performance are non-negotiable — payment infrastructure that can't lose a transaction, redirect engines that have to respond before a human blinks. My work lives at the intersection of distributed architecture, event-driven design, and measurable performance — the kind of engineering where a wrong decision compounds under concurrency.

Currently finishing B.Tech CS (lateral entry after 3-year Diploma). Actively seeking **backend / distributed systems roles** — internships and full-time, India and remote.

---

## What I've Built

### ⚡ [High-Performance URL Redirection Engine](https://github.com/ruthwikkakumani/redirection-engine) — live at [rdrt.dev](https://rdrt.dev)

> Go · Redis · PostgreSQL · Kafka · Docker · Railway

A 4-service distributed system (API Gateway, Auth, Redirect, Analytics) — solo-architected, deployed across **23 live replicas** on Railway, and load-tested to its limits.

| Metric | Value |
|--------|-------|
| Peak throughput | **17,843 RPS** |
| Median latency | **111ms** at 10,000 concurrent users |
| Total requests served | **4.28M** in a single k6 run |
| Success rate | **99.99%** |
| Redis cache hit rate | **99.9%** |
| Redirect-service replicas | **12 active** |

**Key engineering decisions that produced these numbers:**

- Redis over in-process caching → shared cache coherence across 12 replicas; O(1) lookup without DB amplification
- Kafka event pipeline for analytics → zero analytics overhead on the redirect hot-path; paths are fully decoupled
- Removed intra-cluster Nginx after `pprof` profiling → 25% reduction in per-request context-switch overhead
- Two PostgreSQL instances (primary + read replica) → redirect reads never contend with URL writes

---

### 💳 [Fault-Tolerant Idempotent Payment Ledger](https://github.com/ruthwikkakumani/payment-ledger)

> Go · PostgreSQL · Kafka · Redis · Prometheus · Grafana

A fintech-grade payment processing system — because money cannot be lost, duplicated, or partially applied, even under network partitions and broker restarts.

| Metric | Value |
|--------|-------|
| P99 latency reduction | **2,300ms → 120ms** (95% improvement) |
| Duplicate payments processed | **Zero** — validated across broker restart scenarios |
| Dropped payment events | **Zero** across all stress-test runs |

**Hard problems solved:**

- Two-phase idempotency (Redis + Kafka consumer re-check) enforcing exactly-once semantics across partitions and retries
- Double-entry ledger with PostgreSQL `SERIALIZABLE` isolation and row-level locking — system balance nets to zero at all times
- Append-only ledger design — immutable audit trail, no compensating writes, full point-in-time recovery
- Dead-Letter Queue pipeline for poison-pill events — zero silent drops, full recovery path

---

## Technical Stack

**Languages:** Go (primary), C++, Java, Python, SQL

**Backend:** Microservices, Event-Driven Architecture, REST APIs, Distributed Systems

**Data:** PostgreSQL (MVCC, WAL, index tuning), Redis (Caching, Pub/Sub), MongoDB, Apache Kafka

**Infrastructure:** Docker, Kubernetes, AWS, Nginx, Railway, CI/CD

**Observability:** Prometheus, Grafana, Loki, `pprof`, Structured Logging

**Core CS:** Database Internals, Concurrency Control, OS, System Design, DSA

---

## Currently Working On

- OpenTelemetry distributed tracing across both projects (API → Kafka → Worker, end-to-end spans)
- GitHub Actions CI: `go test -race ./...` + `golangci-lint` + Docker build on every PR
- Studying distributed consensus (Raft) and system design for FAANG interviews

---

<div align="center">

**Open to backend / distributed systems / infrastructure roles — India and remote.** ruthwikkakumani@gmail.com · [LinkedIn](https://linkedin.com/in/ruthwikkakumani)

</div>
