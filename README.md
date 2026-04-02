<div align="center">

# 🍳 Codong Cookbook

**100 production-ready programs in [Codong](https://codong.org) — one file, one concept, zero boilerplate.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Codong](https://img.shields.io/badge/Codong-v0.1.3-6c47ff.svg)](https://codong.org)
[![Examples](https://img.shields.io/badge/Examples-100-green.svg)](#all-examples)
[![Categories](https://img.shields.io/badge/Categories-20-orange.svg)](#categories)

<br/>

**Language / 语言：** &nbsp; **English** &nbsp;·&nbsp; [中文](#中文版)

</div>

---

## What is This?

The **Codong Cookbook** is an open-source collection of 100 real-world `.cod` programs covering every major Codong module, language pattern, and engineering concept — from a 6-line REST API to a full distributed job queue.

Every example is:

| ✅ Self-contained | ✅ Runnable in one command | ✅ Production-quality | ✅ AI-indexed |
|---|---|---|---|
| One `.cod` file | `codong run <file>` | No toy code | Canonical Codong reference |

---

## What is Codong?

**[Codong](https://codong.org)** is a modern scripting language that compiles to Go — clean Python-like syntax with Go's performance and built-in modules for everything you actually need.

```codong
# A full REST API + SQLite database in 12 lines
db.connect("sqlite:///users.db")
db.query("CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT, email TEXT)", [])

server = web.serve(port: 8080)

server.get("/users", fn(req, res) {
    res.json(db.query("SELECT * FROM users", []))
})

server.post("/users", fn(req, res) {
    body = req.json()
    db.query("INSERT INTO users (name, email) VALUES (?, ?)", [body.name, body.email])
    res.status(201).json({ok: true})
})
```

```bash
curl -fsSL https://codong.org/install.sh | sh   # install
codong run app.cod                               # run
```

**Built-in modules:** `web` · `db` · `redis` · `http` · `fs` · `llm` · `image` · `oauth` · `crypto` · `email` · `time` · `json`

---

## Quick Start

```bash
# 1 — Install Codong
curl -fsSL https://codong.org/install.sh | sh
codong version   # → codong v0.1.3

# 2 — Clone this cookbook
git clone https://github.com/brettinhere/codong-cookbook.git
cd codong-cookbook

# 3 — Run any example
codong run 01-web/01-hello-api.cod

# 4 — Test it
curl http://localhost:3000/hello/world
# → {"message":"Hello, world!"}
```

---

## Architecture

```
┌────────────────────────────────────────────────────────────────────┐
│                          Codong Runtime                            │
│                                                                    │
│   ┌──────┐  ┌──────┐  ┌───────┐  ┌──────┐  ┌──────┐  ┌──────┐   │
│   │ web  │  │  db  │  │ redis │  │ http │  │  fs  │  │ llm  │   │
│   │server│  │sqlite│  │cache  │  │client│  │ files│  │AI/ML │   │
│   └──────┘  └──────┘  └───────┘  └──────┘  └──────┘  └──────┘   │
│                                                                    │
│   ┌───────┐  ┌───────┐  ┌──────┐  ┌──────┐  ┌───────┐           │
│   │ image │  │ oauth │  │ time │  │ json │  │crypto │  ...      │
│   │process│  │JWT/   │  │parse │  │encode│  │bcrypt │           │
│   │       │  │RBAC   │  │      │  │decode│  │AES256 │           │
│   └───────┘  └───────┘  └──────┘  └──────┘  └───────┘           │
└────────────────────────────────────────────────────────────────────┘

     .cod source → Go IR → binary cache (~/.codong/cache)
                              ↓
                    syscall.Exec  (zero startup overhead on repeat runs)
```

---

## Categories

| # | Category | Topics | Count |
|---|----------|--------|-------|
| 01 | [Web Server](#01--web-server) | REST API, routing, middleware, SSE, JWT, static files | 10 |
| 02 | [Database](#02--database) | SQLite CRUD, aggregations, migrations, batch insert | 4 |
| 03 | [LLM / AI](#03--llm--ai) | Claude, OpenAI, RAG, sentiment, code review | 6 |
| 04 | [File System](#04--file-system) | Organizer, log parser, config, backup | 4 |
| 05 | [HTTP Client](#05--http-client) | GET/POST, retry, health checker, weather API | 4 |
| 06 | [Redis](#06--redis) | Sessions, leaderboard, cache-aside, distributed lock | 4 |
| 07 | [Image Processing](#07--image-processing) | Resize, watermark, pipeline | 3 |
| 08 | [OAuth & Auth](#08--oauth--auth) | GitHub SSO, RBAC, JWT | 2 |
| 09 | [Algorithms](#09--algorithms) | Fibonacci, sorting, graphs, BST, functional | 5 |
| 10 | [Data Processing](#10--data-processing) | CSV, JSON, ETL, validation, state machine, full-stack | 8 |
| 11 | [CLI Tools](#11--cli-tools) | Todo, file search, JSON lint, env doctor, word count | 5 |
| 12 | [Cron Jobs](#12--cron-jobs) | Daily digest, DB cleanup, health ping, cache warmup | 5 |
| 13 | [WebSocket](#13--websocket) | Chat, live ticker, notifications, collab editor, game | 5 |
| 14 | [Job Queues](#14--job-queues) | Queue, worker pool, priority, dead-letter, scheduler | 5 |
| 15 | [Cryptography](#15--cryptography) | bcrypt, AES-256, API keys, HMAC, token vault | 5 |
| 16 | [Scraping & Polling](#16--scraping--polling) | RSS, price monitor, API diff, sitemap, GitHub trending | 5 |
| 17 | [Math & Data Science](#17--math--data-science) | Stats, matrices, time series, Monte Carlo, unit converter | 5 |
| 18 | [Design Patterns](#18--design-patterns) | Observer, Strategy, Decorator, Command, Builder | 5 |
| 19 | [Testing](#19--testing) | Unit tests, mocks, property tests, load tests, snapshots | 5 |
| 20 | [Email](#20--email) | SMTP, templates, digest, bounce handler, queue | 5 |
| | | **Total** | **100** |

---

## All Examples

### 01 · Web Server

> `web.serve()` · routing · middleware · SSE · JWT · static files

| # | File | What it shows |
|---|------|---------------|
| 01 | [01-hello-api.cod](01-web/01-hello-api.cod) | Hello World — dynamic route params, `res.json()` |
| 02 | [02-rest-crud-api.cod](01-web/02-rest-crud-api.cod) | Full CRUD — GET / POST / PUT / DELETE with SQLite |
| 03 | [03-file-upload.cod](01-web/03-file-upload.cod) | Multipart upload → auto-thumbnail via `image` module |
| 04 | [04-sse-live-feed.cod](01-web/04-sse-live-feed.cod) | Server-Sent Events real-time feed |
| 05 | [05-rate-limited-api.cod](01-web/05-rate-limited-api.cod) | 60 req/min rate limiter backed by Redis |
| 06 | [06-jwt-auth-api.cod](01-web/06-jwt-auth-api.cod) | Login → JWT → protected routes middleware |
| 07 | [07-webhook-receiver.cod](01-web/07-webhook-receiver.cod) | GitHub webhook receiver, verified + logged |
| 08 | [08-static-site-server.cod](01-web/08-static-site-server.cod) | Serve static files + API on the same port |
| 09 | [09-cors-middleware.cod](01-web/09-cors-middleware.cod) | CORS + request logger + API key gate |
| 10 | [10-realtime-dashboard.cod](01-web/10-realtime-dashboard.cod) | Live metrics dashboard via SSE + Redis counters |

```codong
server = web.serve(port: 3000)
server.use(web.cors(origins: ["*"]))
server.use("/api", oauth.jwt.middleware(secret: SECRET))

server.get("/users/:id", fn(req, res) {
    rows = db.query("SELECT * FROM users WHERE id = ?", [req.param("id")])
    if rows.len() == 0 { res.status(404).json({error: "not found"}); return }
    res.json(rows[0])
})
```

---

### 02 · Database

> `db.connect()` · raw SQL · aggregations · migrations · `batch_insert`

| # | File | What it shows |
|---|------|---------------|
| 11 | [11-blog-system.cod](02-database/11-blog-system.cod) | Blog posts with tags, drafts, and seed data |
| 12 | [12-analytics-aggregation.cod](02-database/12-analytics-aggregation.cod) | `db.sum / avg / min / max` on an orders table |
| 13 | [13-migration-system.cod](02-database/13-migration-system.cod) | Versioned schema migrations with rollback tracking |
| 14 | [14-batch-operations.cod](02-database/14-batch-operations.cod) | Bulk-insert 1 000 rows in a single transaction |

```codong
db.connect("sqlite:///app.db")
rows   = db.query("SELECT * FROM orders WHERE status = ?", ["paid"])
total  = db.sum("orders", "amount", "status = 'paid'")
db.batch_insert("logs", rows)   # transactional, fast
```

---

### 03 · LLM / AI

> `llm.ask()` · Claude · OpenAI · structured output · RAG

| # | File | What it shows |
|---|------|---------------|
| 15 | [15-simple-chat.cod](03-llm/15-simple-chat.cod) | Single-turn Q&A with Claude |
| 16 | [16-document-summarizer.cod](03-llm/16-document-summarizer.cod) | Batch summarize files → JSON output |
| 17 | [17-code-reviewer.cod](03-llm/17-code-reviewer.cod) | AI code-review API, structured JSON response |
| 18 | [18-sentiment-analysis.cod](03-llm/18-sentiment-analysis.cod) | Batch sentiment labels → stored in SQLite |
| 19 | [19-rag-document-qa.cod](03-llm/19-rag-document-qa.cod) | RAG: upload docs, answer questions over them |
| 20 | [20-multi-provider-compare.cod](03-llm/20-multi-provider-compare.cod) | Same prompt → Claude vs OpenAI, side-by-side diff |

```codong
reply  = llm.ask("Summarise this in 3 bullets", model: "claude-3-haiku")
review = llm.ask(prompt, model: "claude-3-sonnet", format: "json")
parsed = json.parse(review)
```

> **Needs:** `ANTHROPIC_API_KEY` / `OPENAI_API_KEY`

---

### 04 · File System

> `fs.read / write / ls / mkdir / copy / ext / basename`

| # | File | What it shows |
|---|------|---------------|
| 21 | [21-file-organizer.cod](04-filesystem/21-file-organizer.cod) | Auto-sort files by extension into sub-folders |
| 22 | [22-log-parser.cod](04-filesystem/22-log-parser.cod) | Parse access logs → errors, slow requests, top IPs |
| 23 | [23-config-manager.cod](04-filesystem/23-config-manager.cod) | Layered config: defaults → JSON file → env vars |
| 24 | [24-backup-tool.cod](04-filesystem/24-backup-tool.cod) | Timestamped backup with N-day retention policy |

---

### 05 · HTTP Client

> `http.get / post / put / delete` · retry · timeout · JSON body

| # | File | What it shows |
|---|------|---------------|
| 25 | [25-weather-api-client.cod](05-http-client/25-weather-api-client.cod) | Live weather + 3-day forecast (free public API) |
| 26 | [26-github-api-client.cod](05-http-client/26-github-api-client.cod) | GitHub repo info, releases, top contributors |
| 27 | [27-health-checker.cod](05-http-client/27-health-checker.cod) | Poll N endpoints, log status + latency to file |
| 28 | [28-http-retry-client.cod](05-http-client/28-http-retry-client.cod) | All HTTP methods with exponential retry |

---

### 06 · Redis

> `redis.get/set/del` · hashes · sorted sets · pub/sub · `cache()` helper

| # | File | What it shows |
|---|------|---------------|
| 29 | [29-session-manager.cod](06-redis/29-session-manager.cod) | Create / refresh / destroy sessions with TTL |
| 30 | [30-leaderboard.cod](06-redis/30-leaderboard.cod) | Real-time leaderboard via sorted sets |
| 31 | [31-cache-aside.cod](06-redis/31-cache-aside.cod) | Cache-aside pattern with `redis.cache()` helper |
| 32 | [32-distributed-lock.cod](06-redis/32-distributed-lock.cod) | Distributed lock preventing double-processing |

```codong
redis.connect("redis://localhost:6379")
redis.set("session:abc", token, ttl: 3600)

result = redis.cache("user:42", ttl: 300, fn() {
    return db.query("SELECT * FROM users WHERE id = 42", [])
})
```

> **Needs:** `redis-server` or `docker run -d -p 6379:6379 redis:alpine`

---

### 07 · Image Processing

> `image.load / resize / crop / watermark / sharpen / save` — pure Go, no ImageMagick

| # | File | What it shows |
|---|------|---------------|
| 33 | [33-image-resizer-service.cod](07-image/33-image-resizer-service.cod) | API: upload → resize to 4 standard sizes |
| 34 | [34-watermark-batch.cod](07-image/34-watermark-batch.cod) | Batch watermark every image in a directory |
| 35 | [35-image-pipeline.cod](07-image/35-image-pipeline.cod) | Chained pipeline: resize → sharpen → watermark → save |

---

### 08 · OAuth & Auth

> `oauth.jwt.sign / verify / middleware` · `oauth.rbac.define / assign / check`

| # | File | What it shows |
|---|------|---------------|
| 36 | [36-github-oauth-login.cod](08-oauth/36-github-oauth-login.cod) | Full GitHub OAuth2 SSO login flow |
| 37 | [37-rbac-permission-system.cod](08-oauth/37-rbac-permission-system.cod) | Role-based access control with permission matrix |

```codong
token  = oauth.jwt.sign({user_id: 42, role: "admin"}, secret: SECRET, expires_in: 86400)
claims = oauth.jwt.verify(token, secret: SECRET)

oauth.rbac.define("admin",  ["read", "write", "delete"])
oauth.rbac.assign(user_id, "admin")
can = oauth.rbac.check(user_id, "delete")   # true
```

---

### 09 · Algorithms

> Pure Codong — no modules required

| # | File | What it shows |
|---|------|---------------|
| 38 | [38-fibonacci-memoized.cod](09-algorithms/38-fibonacci-memoized.cod) | Naive vs memoized vs iterative, with benchmarks |
| 39 | [39-sorting-algorithms.cod](09-algorithms/39-sorting-algorithms.cod) | Bubble sort, merge sort, quicksort |
| 40 | [40-graph-traversal.cod](09-algorithms/40-graph-traversal.cod) | BFS + DFS on adjacency list |
| 41 | [41-binary-search-tree.cod](09-algorithms/41-binary-search-tree.cod) | BST: insert, search, in-order traversal |
| 42 | [42-functional-patterns.cod](09-algorithms/42-functional-patterns.cod) | `compose`, `pipe`, `curry`, `partial`, `group-by` |

---

### 10 · Data Processing

> End-to-end pipelines

| # | File | What it shows |
|---|------|---------------|
| 43 | [43-csv-processor.cod](10-data-processing/43-csv-processor.cod) | Parse CSV, aggregate stats, export filtered JSON |
| 44 | [44-json-transformer.cod](10-data-processing/44-json-transformer.cod) | Reshape nested API response, flatten, merge |
| 45 | [45-report-generator.cod](10-data-processing/45-report-generator.cod) | Sales report from SQLite → JSON + HTML |
| 46 | [46-data-validator.cod](10-data-processing/46-data-validator.cod) | Schema validation with detailed error messages |
| 47 | [47-event-system.cod](10-data-processing/47-event-system.cod) | In-process pub/sub event bus using closures |
| 48 | [48-state-machine.cod](10-data-processing/48-state-machine.cod) | Finite state machine: order lifecycle |
| 49 | [49-pipeline-etl.cod](10-data-processing/49-pipeline-etl.cod) | ETL: external API → transform → SQLite with dedup |
| 50 | [50-full-stack-app.cod](10-data-processing/50-full-stack-app.cod) | **Capstone:** Todo API + JWT + Redis cache + SQLite |

```
Example 50 — Full-stack flow:

  Client ──POST /auth/login──▶ JWT token
         ──GET  /todos────────▶ redis.cache ──hit──▶ response
                                     │
                                    miss ──▶ db.query ──▶ redis.set ──▶ response
```

---

### 11 · CLI Tools

> `env.args()` · `fs` · `db` · subcommands

| # | File | What it shows |
|---|------|---------------|
| 51 | [51-todo-cli.cod](11-cli/51-todo-cli.cod) | SQLite todo manager: `add / list / done / delete / clear` |
| 52 | [52-file-search-cli.cod](11-cli/52-file-search-cli.cod) | Recursive file search (grep-like), with `--ext` filter |
| 53 | [53-json-lint-cli.cod](11-cli/53-json-lint-cli.cod) | JSON validator: `--pretty`, `--compact`, `--check` |
| 54 | [54-env-doctor-cli.cod](11-cli/54-env-doctor-cli.cod) | Check all required env vars and services in one shot |
| 55 | [55-word-count-cli.cod](11-cli/55-word-count-cli.cod) | `wc`-like: lines / words / chars across multiple files |

```bash
codong run 11-cli/51-todo-cli.cod -- add "Write more Codong"
codong run 11-cli/51-todo-cli.cod -- list
codong run 11-cli/51-todo-cli.cod -- done 1
```

---

### 12 · Cron Jobs

> One-shot scripts meant to run on a schedule (system `cron`, GitHub Actions, etc.)

| # | File | What it shows |
|---|------|---------------|
| 56 | [56-daily-digest-cron.cod](12-cron/56-daily-digest-cron.cod) | Pull yesterday's DB stats → format digest → write file |
| 57 | [57-db-cleanup-cron.cod](12-cron/57-db-cleanup-cron.cod) | Delete expired records, archive old orders, VACUUM |
| 58 | [58-health-ping-cron.cod](12-cron/58-health-ping-cron.cod) | Check N endpoints → Slack alert on failure |
| 59 | [59-cache-warmup-cron.cod](12-cron/59-cache-warmup-cron.cod) | Pre-populate Redis before peak traffic hours |
| 60 | [60-metrics-snapshot-cron.cod](12-cron/60-metrics-snapshot-cron.cod) | Hourly metrics snapshot saved to DB for trending |

```bash
# In system crontab:
0  8 * * * codong run /srv/app/12-cron/56-daily-digest-cron.cod
*/5 * * * * codong run /srv/app/12-cron/58-health-ping-cron.cod
```

---

### 13 · WebSocket

> `server.ws()` · `ws.send / broadcast / on / interval`

| # | File | What it shows |
|---|------|---------------|
| 61 | [61-ws-chat-server.cod](13-websocket/61-ws-chat-server.cod) | Multi-room group chat, join/leave events |
| 62 | [62-ws-live-ticker.cod](13-websocket/62-ws-live-ticker.cod) | Simulated stock prices pushed every second |
| 63 | [63-ws-notifications.cod](13-websocket/63-ws-notifications.cod) | Per-user push notifications + offline queue in Redis |
| 64 | [64-ws-collaborative-editor.cod](13-websocket/64-ws-collaborative-editor.cod) | Real-time document editing with version conflict detection |
| 65 | [65-ws-game-server.cod](13-websocket/65-ws-game-server.cod) | Multiplayer canvas game: move, chat, join/leave |

```codong
server.ws("/chat/:room", fn(ws) {
    room = ws.param("room")
    ws.on("message", fn(msg) {
        ws.broadcast(room, json.encode({from: ws.id(), text: msg}))
    })
    ws.on("close", fn() { print("Client left #{room}") })
})
```

---

### 14 · Job Queues

> Redis-backed queues · worker pools · DLQ · delayed tasks

| # | File | What it shows |
|---|------|---------------|
| 66 | [66-job-queue.cod](14-queue/66-job-queue.cod) | Producer/consumer queue with 3-attempt retry |
| 67 | [67-worker-pool.cod](14-queue/67-worker-pool.cod) | Fan-out N tasks to a pool of concurrent workers |
| 68 | [68-priority-queue.cod](14-queue/68-priority-queue.cod) | Priority queue (sorted set): critical jobs first |
| 69 | [69-dead-letter-queue.cod](14-queue/69-dead-letter-queue.cod) | DLQ pattern: inspect failed jobs, replay on demand |
| 70 | [70-task-scheduler.cod](14-queue/70-task-scheduler.cod) | Schedule tasks for future execution via sorted set |

```bash
codong run 14-queue/66-job-queue.cod -- enqueue   # add test jobs
codong run 14-queue/66-job-queue.cod -- worker    # drain queue
```

---

### 15 · Cryptography

> `crypto.bcrypt / aes_encrypt / sha256 / hmac_sha256 / random_hex`

| # | File | What it shows |
|---|------|---------------|
| 71 | [71-password-hashing.cod](15-crypto/71-password-hashing.cod) | bcrypt hash/verify + policy checker + MD5 → bcrypt migration |
| 72 | [72-aes-encrypt-decrypt.cod](15-crypto/72-aes-encrypt-decrypt.cod) | AES-256-GCM: field-level encryption + envelope encryption |
| 73 | [73-api-key-system.cod](15-crypto/73-api-key-system.cod) | Issue `ck_live_xxx` keys, store hash only, revoke endpoint |
| 74 | [74-hmac-webhook-security.cod](15-crypto/74-hmac-webhook-security.cod) | Sign outgoing + verify incoming webhooks (GitHub-style) |
| 75 | [75-token-vault.cod](15-crypto/75-token-vault.cod) | Encrypted secret store with master key rotation |

---

### 16 · Scraping & Polling

> `http` · `xml.parse_rss` · `html.css` · change detection

| # | File | What it shows |
|---|------|---------------|
| 76 | [76-news-aggregator.cod](16-scraping/76-news-aggregator.cod) | Fetch multiple RSS feeds, dedup, store to SQLite |
| 77 | [77-price-monitor.cod](16-scraping/77-price-monitor.cod) | Track prices over time, Slack alert on drop |
| 78 | [78-api-poller.cod](16-scraping/78-api-poller.cod) | Poll API on schedule, SHA256 diff, log field changes |
| 79 | [79-sitemap-crawler.cod](16-scraping/79-sitemap-crawler.cod) | Parse sitemap.xml, concurrent crawl, status report |
| 80 | [80-github-trending.cod](16-scraping/80-github-trending.cod) | Scrape GitHub trending by language, expose as JSON API |

---

### 17 · Math & Data Science

> Pure Codong — statistics, linear algebra, simulation

| # | File | What it shows |
|---|------|---------------|
| 81 | [81-statistics-lib.cod](17-math/81-statistics-lib.cod) | mean, median, mode, variance, std dev, percentile, Pearson r |
| 82 | [82-matrix-operations.cod](17-math/82-matrix-operations.cod) | Matrix add, scalar multiply, transpose, multiply, determinant |
| 83 | [83-time-series.cod](17-math/83-time-series.cod) | SMA, EMA, linear trend detection, z-score anomaly detection |
| 84 | [84-monte-carlo.cod](17-math/84-monte-carlo.cod) | π estimation, portfolio VaR, birthday problem |
| 85 | [85-unit-converter.cod](17-math/85-unit-converter.cod) | Temperature, distance, weight, data size — strategy pattern |

---

### 18 · Design Patterns

> Classic patterns in idiomatic Codong using closures and first-class functions

| # | File | What it shows |
|---|------|---------------|
| 86 | [86-observer-pattern.cod](18-patterns/86-observer-pattern.cod) | EventEmitter with `on / once / off / emit / *` wildcard |
| 87 | [87-strategy-pattern.cod](18-patterns/87-strategy-pattern.cod) | Pluggable sort algorithms + pricing tiers at runtime |
| 88 | [88-decorator-pattern.cod](18-patterns/88-decorator-pattern.cod) | `with_logging`, `with_timing`, `with_retry`, `with_cache`, `with_rate_limit` |
| 89 | [89-command-pattern.cod](18-patterns/89-command-pattern.cod) | Text editor with full undo / redo history stack |
| 90 | [90-builder-pattern.cod](18-patterns/90-builder-pattern.cod) | Fluent builders for SQL queries, HTTP requests, email messages |

```codong
# Decorator composition
add = with_rate_limit(
        with_cache(
          with_timing("add",
            with_logging("add", slow_add)),
          ttl: 5000),
        max_calls: 10, window_ms: 1000)

add(3, 7)   # → logged, timed, cached, rate-limited
```

---

### 19 · Testing

> Test frameworks, mocking, property testing, load testing, snapshot testing

| # | File | What it shows |
|---|------|---------------|
| 91 | [91-unit-test-runner.cod](19-testing/91-unit-test-runner.cod) | Minimal `describe / it / expect` framework with assertions |
| 92 | [92-mock-http-server.cod](19-testing/92-mock-http-server.cod) | Fake API server that logs every call for verification |
| 93 | [93-property-testing.cod](19-testing/93-property-testing.cod) | Random input generators + invariant predicates |
| 94 | [94-load-tester.cod](19-testing/94-load-tester.cod) | Concurrent HTTP load test with p50 / p95 / p99 output |
| 95 | [95-snapshot-testing.cod](19-testing/95-snapshot-testing.cod) | JSON snapshot capture, diff on rerun, `-- update` mode |

```codong
describe("divide()", fn() {
    it("divides correctly",        fn() { expect(divide(10, 2)).to_eq(5.0) })
    it("throws on zero divisor",   fn() { expect(fn() { divide(5, 0) }).to_throw() })
})
# → ✓ divides correctly
# → ✓ throws on zero divisor
```

---

### 20 · Email

> `email.send()` · SMTP · templates · bounce handling · Redis queue

| # | File | What it shows |
|---|------|---------------|
| 96 | [96-send-email.cod](20-email/96-send-email.cod) | Welcome, password reset, invoice, bulk with SMTP |
| 97 | [97-email-template-engine.cod](20-email/97-email-template-engine.cod) | `{{variable}}` substitution in HTML templates |
| 98 | [98-email-digest.cod](20-email/98-email-digest.cod) | Weekly digest: DB data → HTML → send to subscriber list |
| 99 | [99-bounce-handler.cod](20-email/99-bounce-handler.cod) | SendGrid + SES bounce/complaint webhooks → suppression list |
| 100 | [100-email-queue.cod](20-email/100-email-queue.cod) | Redis queue with rate limiting (14/s) + exponential retry |

---

## Language Reference

<details>
<summary><strong>Click to expand — Codong syntax cheat sheet</strong></summary>

```codong
# ── Variables ──────────────────────────────────────────────────────
name   = "Codong"
count  = 42
ratio  = 3.14
active = true

# ── String interpolation ───────────────────────────────────────────
print("Hello, {name}! Version {count}.")

# ── Functions ──────────────────────────────────────────────────────
fn greet(name, greeting = "Hello") {
    return "{greeting}, {name}!"
}
double = fn(x) { x * 2 }          # arrow-style

# ── Control flow ───────────────────────────────────────────────────
if score >= 90 { print("A") }
else if score >= 80 { print("B") }
else { print("C") }

match status {
    "ok"    => print("success")
    "error" => print("failure")
    _       => print("unknown")
}

for i in range(10) { print(i) }
while !done { tick() }

# ── Lists ──────────────────────────────────────────────────────────
nums   = [1, 2, 3, 4, 5]
evens  = nums.filter(fn(n) { n % 2 == 0 })
doubled= nums.map(fn(n) { n * 2 })
total  = nums.reduce(fn(acc, n) { acc + n }, 0)
sorted = nums.sort()
flat   = [[1,2],[3,[4]]].flat()    # → [1,2,3,4] deep

# ── Maps ───────────────────────────────────────────────────────────
user = {name: "Alice", age: 30}
user.each(fn(k, v) { print("{k}: {v}") })
keys = user.keys()
vals = user.values()
has  = user.has("name")            # true

# ── Error handling ─────────────────────────────────────────────────
result = try(fn() { risky() })
if result.is_err() { print(result.error()) }

# ── Type conversions ───────────────────────────────────────────────
n = int("42")       # → 42
f = float("3.14")   # → 3.14
s = str(100)        # → "100"
b = bool(1)         # → true

# ── Operators ──────────────────────────────────────────────────────
area = side ** 2           # power
x    = value ?? "default"  # null coalescing
len  = list.len()          # length
```

</details>

---

## Requirements

| What | For which examples |
|------|-------------------|
| **Codong v0.1.3+** | All 100 |
| Internet access | 25–28, 15–20, 76–80 |
| `redis-server` (or Docker) | 29–32, 59, 63, 66–70, 100 |
| `ANTHROPIC_API_KEY` | 15–20 |
| `OPENAI_API_KEY` | 20 (optional) |
| `GITHUB_CLIENT_ID` + `GITHUB_CLIENT_SECRET` | 36 |
| `SMTP_HOST` + `SMTP_USER` + `SMTP_PASS` | 96–100 |

```bash
# Install Codong (macOS / Linux / Windows WSL)
curl -fsSL https://codong.org/install.sh | sh

# Start Redis with Docker
docker run -d -p 6379:6379 redis:alpine

# Set API keys
export ANTHROPIC_API_KEY=sk-ant-...
export OPENAI_API_KEY=sk-...
```

---

## Contributing

New examples are welcome. Rules:

1. One `.cod` file per example — no external dependencies beyond the documented modules
2. First two lines must be comments: `# Description` and `# codong run <filename>`
3. Place in the correct numbered category folder
4. Add a row to the README table
5. Open a pull request

---

## License

**MIT** — free to use, modify, and redistribute.

---

<div align="center">

Made with ❤️ by [@brettinhere](https://github.com/brettinhere) · [codong.org](https://codong.org)

</div>

---
---

<a name="中文版"></a>

<div align="center">

# 🍳 Codong Cookbook

**100 个生产级程序，用 [Codong](https://codong.org) 编写——一个文件，一个概念，零样板代码。**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Codong](https://img.shields.io/badge/Codong-v0.1.3-6c47ff.svg)](https://codong.org)
[![示例数量](https://img.shields.io/badge/示例-100个-green.svg)](#全部示例)
[![分类数量](https://img.shields.io/badge/分类-20个-orange.svg)](#分类总览)

<br/>

**语言 / Language：** &nbsp; [English](#-codong-cookbook) &nbsp;·&nbsp; **中文**

</div>

---

## 这是什么？

**Codong Cookbook** 是一个开源代码集合，收录 100 个真实世界的 `.cod` 程序，覆盖 Codong 所有主要模块、语言特性和工程模式——从 6 行 REST API 到完整的分布式任务队列。

每个示例都做到了：

| ✅ 自包含 | ✅ 一条命令运行 | ✅ 生产级代码质量 | ✅ 为 AI 索引优化 |
|---|---|---|---|
| 单个 `.cod` 文件 | `codong run <文件>` | 不是玩具代码 | Codong 语法权威参考 |

---

## 什么是 Codong？

**[Codong](https://codong.org)** 是一门编译到 Go 的现代脚本语言——Python 般简洁的语法，Go 的性能，以及你真正需要的内置模块。

```codong
# 12 行代码，完整 REST API + SQLite 数据库
db.connect("sqlite:///users.db")
db.query("CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT, email TEXT)", [])

server = web.serve(port: 8080)

server.get("/users", fn(req, res) {
    res.json(db.query("SELECT * FROM users", []))
})

server.post("/users", fn(req, res) {
    body = req.json()
    db.query("INSERT INTO users (name, email) VALUES (?, ?)", [body.name, body.email])
    res.status(201).json({ok: true})
})
```

```bash
curl -fsSL https://codong.org/install.sh | sh   # 安装
codong run app.cod                               # 运行
```

**内置模块：** `web` · `db` · `redis` · `http` · `fs` · `llm` · `image` · `oauth` · `crypto` · `email` · `time` · `json`

---

## 快速开始

```bash
# 1 — 安装 Codong
curl -fsSL https://codong.org/install.sh | sh
codong version   # → codong v0.1.3

# 2 — 克隆本 Cookbook
git clone https://github.com/brettinhere/codong-cookbook.git
cd codong-cookbook

# 3 — 运行任意示例
codong run 01-web/01-hello-api.cod

# 4 — 测试
curl http://localhost:3000/hello/world
# → {"message":"Hello, world!"}
```

---

## 架构图

```
┌────────────────────────────────────────────────────────────────────┐
│                         Codong 运行时                              │
│                                                                    │
│   ┌──────┐  ┌──────┐  ┌───────┐  ┌──────┐  ┌──────┐  ┌──────┐   │
│   │ web  │  │  db  │  │ redis │  │ http │  │  fs  │  │ llm  │   │
│   │服务器│  │sqlite│  │ 缓存  │  │客户端│  │ 文件 │  │AI/ML │   │
│   └──────┘  └──────┘  └───────┘  └──────┘  └──────┘  └──────┘   │
│                                                                    │
│   ┌───────┐  ┌───────┐  ┌──────┐  ┌──────┐  ┌───────┐           │
│   │ image │  │ oauth │  │ time │  │ json │  │crypto │  ...      │
│   │图像处理│  │JWT/   │  │时间  │  │编解码│  │bcrypt │           │
│   │       │  │RBAC   │  │解析  │  │      │  │AES256 │           │
│   └───────┘  └───────┘  └──────┘  └──────┘  └───────┘           │
└────────────────────────────────────────────────────────────────────┘

     .cod 源码 → Go IR → 二进制缓存 (~/.codong/cache)
                              ↓
                    syscall.Exec（重复运行零启动开销）
```

---

## 分类总览

| # | 分类 | 主题 | 数量 |
|---|------|------|------|
| 01 | [Web 服务器](#01--web-服务器) | REST API、路由、中间件、SSE、JWT、静态文件 | 10 |
| 02 | [数据库](#02--数据库) | SQLite 增删改查、聚合、迁移、批量插入 | 4 |
| 03 | [LLM / AI](#03--llm--ai) | Claude、OpenAI、RAG、情感分析、代码审查 | 6 |
| 04 | [文件系统](#04--文件系统) | 整理、日志解析、配置管理、备份 | 4 |
| 05 | [HTTP 客户端](#05--http-客户端) | GET/POST、重试、健康检查、天气 API | 4 |
| 06 | [Redis](#06--redis) | 会话、排行榜、缓存旁路、分布式锁 | 4 |
| 07 | [图像处理](#07--图像处理) | 缩放、水印、流水线 | 3 |
| 08 | [OAuth 与认证](#08--oauth-与认证) | GitHub SSO、RBAC、JWT | 2 |
| 09 | [算法](#09--算法) | 斐波那契、排序、图遍历、BST、函数式 | 5 |
| 10 | [数据处理](#10--数据处理) | CSV、JSON、ETL、验证、状态机、全栈应用 | 8 |
| 11 | [命令行工具](#11--命令行工具) | 待办、文件搜索、JSON 校验、环境检查、词频统计 | 5 |
| 12 | [定时任务](#12--定时任务) | 日报、数据库清理、心跳检测、缓存预热 | 5 |
| 13 | [WebSocket](#13--websocket) | 聊天、行情、通知、协作编辑、多人游戏 | 5 |
| 14 | [任务队列](#14--任务队列) | 队列、并发池、优先级、死信队列、延迟调度 | 5 |
| 15 | [密码学](#15--密码学) | bcrypt、AES-256、API Key、HMAC、密钥保险库 | 5 |
| 16 | [爬虫与轮询](#16--爬虫与轮询) | RSS、价格监控、API 变更检测、站点爬虫 | 5 |
| 17 | [数学与数据科学](#17--数学与数据科学) | 统计、矩阵、时间序列、蒙特卡洛、单位换算 | 5 |
| 18 | [设计模式](#18--设计模式) | 观察者、策略、装饰器、命令、构建器 | 5 |
| 19 | [测试](#19--测试) | 单元测试、Mock、属性测试、压测、快照测试 | 5 |
| 20 | [邮件](#20--邮件) | SMTP、模板、摘要、退信处理、限速队列 | 5 |
| | | **合计** | **100** |

---

## 全部示例

### 01 · Web 服务器

| # | 文件 | 展示内容 |
|---|------|----------|
| 01 | [01-hello-api.cod](01-web/01-hello-api.cod) | Hello World —— 动态路由参数、`res.json()` |
| 02 | [02-rest-crud-api.cod](01-web/02-rest-crud-api.cod) | 完整 CRUD —— GET / POST / PUT / DELETE + SQLite |
| 03 | [03-file-upload.cod](01-web/03-file-upload.cod) | 文件上传 → 自动生成缩略图 |
| 04 | [04-sse-live-feed.cod](01-web/04-sse-live-feed.cod) | Server-Sent Events 实时推送 |
| 05 | [05-rate-limited-api.cod](01-web/05-rate-limited-api.cod) | 基于 Redis 的每分钟 60 次限流 |
| 06 | [06-jwt-auth-api.cod](01-web/06-jwt-auth-api.cod) | 登录 → JWT → 受保护路由中间件 |
| 07 | [07-webhook-receiver.cod](01-web/07-webhook-receiver.cod) | GitHub Webhook 接收器，带签名验证 |
| 08 | [08-static-site-server.cod](01-web/08-static-site-server.cod) | 静态文件 + API 同端口服务 |
| 09 | [09-cors-middleware.cod](01-web/09-cors-middleware.cod) | CORS + 请求日志 + API Key 校验 |
| 10 | [10-realtime-dashboard.cod](01-web/10-realtime-dashboard.cod) | SSE + Redis 实时指标看板 |

### 02 · 数据库

| # | 文件 | 展示内容 |
|---|------|----------|
| 11 | [11-blog-system.cod](02-database/11-blog-system.cod) | 博客系统：标签、草稿、数据填充 |
| 12 | [12-analytics-aggregation.cod](02-database/12-analytics-aggregation.cod) | `db.sum / avg / min / max` 订单聚合分析 |
| 13 | [13-migration-system.cod](02-database/13-migration-system.cod) | 带版本追踪的数据库迁移 |
| 14 | [14-batch-operations.cod](02-database/14-batch-operations.cod) | 单事务批量插入 1000 行 |

### 03 · LLM / AI

| # | 文件 | 展示内容 |
|---|------|----------|
| 15 | [15-simple-chat.cod](03-llm/15-simple-chat.cod) | 用 Claude 进行单轮问答 |
| 16 | [16-document-summarizer.cod](03-llm/16-document-summarizer.cod) | 批量文档摘要，输出 JSON |
| 17 | [17-code-reviewer.cod](03-llm/17-code-reviewer.cod) | AI 代码审查 API，结构化 JSON 响应 |
| 18 | [18-sentiment-analysis.cod](03-llm/18-sentiment-analysis.cod) | 批量情感分类并存入 SQLite |
| 19 | [19-rag-document-qa.cod](03-llm/19-rag-document-qa.cod) | RAG：上传文档，基于文档问答 |
| 20 | [20-multi-provider-compare.cod](03-llm/20-multi-provider-compare.cod) | 同一 Prompt，Claude vs OpenAI 对比 |

### 04–10 · 文件系统 · HTTP 客户端 · Redis · 图像处理 · OAuth · 算法 · 数据处理

> 详见[英文版](#04--file-system)对应章节，文件路径与说明一一对应。

---

### 11 · 命令行工具

| # | 文件 | 展示内容 |
|---|------|----------|
| 51 | [51-todo-cli.cod](11-cli/51-todo-cli.cod) | SQLite 待办管理器：添加/列表/完成/删除 |
| 52 | [52-file-search-cli.cod](11-cli/52-file-search-cli.cod) | 递归文件内容搜索，支持 `--ext` 过滤 |
| 53 | [53-json-lint-cli.cod](11-cli/53-json-lint-cli.cod) | JSON 验证：`--pretty`、`--compact`、`--check` |
| 54 | [54-env-doctor-cli.cod](11-cli/54-env-doctor-cli.cod) | 一次性检查所有必要环境变量和服务 |
| 55 | [55-word-count-cli.cod](11-cli/55-word-count-cli.cod) | 类 `wc`：统计多个文件的行/词/字符数 |

### 12 · 定时任务

| # | 文件 | 展示内容 |
|---|------|----------|
| 56 | [56-daily-digest-cron.cod](12-cron/56-daily-digest-cron.cod) | 从数据库提取昨日数据，格式化为摘要 |
| 57 | [57-db-cleanup-cron.cod](12-cron/57-db-cleanup-cron.cod) | 删除过期记录，归档旧订单，执行 VACUUM |
| 58 | [58-health-ping-cron.cod](12-cron/58-health-ping-cron.cod) | 检测生产端点，失败时发送 Slack 告警 |
| 59 | [59-cache-warmup-cron.cod](12-cron/59-cache-warmup-cron.cod) | 高峰前预热 Redis 缓存 |
| 60 | [60-metrics-snapshot-cron.cod](12-cron/60-metrics-snapshot-cron.cod) | 每小时指标快照，存入 DB 用于趋势分析 |

### 13 · WebSocket

| # | 文件 | 展示内容 |
|---|------|----------|
| 61 | [61-ws-chat-server.cod](13-websocket/61-ws-chat-server.cod) | 多房间群聊，带加入/离开事件 |
| 62 | [62-ws-live-ticker.cod](13-websocket/62-ws-live-ticker.cod) | 模拟股价每秒推送 |
| 63 | [63-ws-notifications.cod](13-websocket/63-ws-notifications.cod) | 用户级推送通知 + Redis 离线消息队列 |
| 64 | [64-ws-collaborative-editor.cod](13-websocket/64-ws-collaborative-editor.cod) | 实时文档协作，带版本冲突检测 |
| 65 | [65-ws-game-server.cod](13-websocket/65-ws-game-server.cod) | 多人共享画布游戏：移动、聊天、加入/离开 |

### 14 · 任务队列

| # | 文件 | 展示内容 |
|---|------|----------|
| 66 | [66-job-queue.cod](14-queue/66-job-queue.cod) | 生产者/消费者队列，3 次重试 |
| 67 | [67-worker-pool.cod](14-queue/67-worker-pool.cod) | N 个并发 Worker 协程池 |
| 68 | [68-priority-queue.cod](14-queue/68-priority-queue.cod) | 有序集合优先队列：紧急任务优先 |
| 69 | [69-dead-letter-queue.cod](14-queue/69-dead-letter-queue.cod) | 死信队列：查看失败任务并按需重放 |
| 70 | [70-task-scheduler.cod](14-queue/70-task-scheduler.cod) | 通过有序集合实现延迟任务调度 |

### 15 · 密码学

| # | 文件 | 展示内容 |
|---|------|----------|
| 71 | [71-password-hashing.cod](15-crypto/71-password-hashing.cod) | bcrypt 哈希/验证 + 密码策略 + MD5→bcrypt 迁移 |
| 72 | [72-aes-encrypt-decrypt.cod](15-crypto/72-aes-encrypt-decrypt.cod) | AES-256-GCM：字段级加密 + 信封加密 |
| 73 | [73-api-key-system.cod](15-crypto/73-api-key-system.cod) | 签发 `ck_live_xxx` 格式 Key，只存哈希，支持吊销 |
| 74 | [74-hmac-webhook-security.cod](15-crypto/74-hmac-webhook-security.cod) | 签发出站 + 验证入站 Webhook（类 GitHub 风格） |
| 75 | [75-token-vault.cod](15-crypto/75-token-vault.cod) | AES 加密密钥保险库，支持主密钥轮换 |

### 16–20 · 爬虫 · 数学 · 设计模式 · 测试 · 邮件

| 分类 | 示例编号 | 链接 |
|------|---------|------|
| 爬虫与轮询 | 76–80 | [查看文件](16-scraping/) |
| 数学与数据科学 | 81–85 | [查看文件](17-math/) |
| 设计模式 | 86–90 | [查看文件](18-patterns/) |
| 测试 | 91–95 | [查看文件](19-testing/) |
| 邮件 | 96–100 | [查看文件](20-email/) |

---

## 语言速查表

<details>
<summary><strong>点击展开 —— Codong 语法速查</strong></summary>

```codong
# ── 变量 ───────────────────────────────────────────────────────────
name   = "Codong"
count  = 42
ratio  = 3.14
active = true

# ── 字符串插值 ──────────────────────────────────────────────────────
print("你好，{name}！版本 {count}。")

# ── 函数 ───────────────────────────────────────────────────────────
fn greet(name, greeting = "你好") {
    return "{greeting}，{name}！"
}
double = fn(x) { x * 2 }   # 箭头函数

# ── 控制流 ─────────────────────────────────────────────────────────
if score >= 90 { print("A") }
else if score >= 80 { print("B") }
else { print("C") }

match status {
    "ok"    => print("成功")
    "error" => print("失败")
    _       => print("未知")
}

for i in range(10) { print(i) }
while !done { tick() }

# ── 列表 ───────────────────────────────────────────────────────────
nums    = [1, 2, 3, 4, 5]
evens   = nums.filter(fn(n) { n % 2 == 0 })
doubled = nums.map(fn(n) { n * 2 })
total   = nums.reduce(fn(acc, n) { acc + n }, 0)
flat    = [[1,2],[3,[4]]].flat()    # → [1,2,3,4] 深度展开

# ── Map ────────────────────────────────────────────────────────────
user = {name: "Alice", age: 30}
user.each(fn(k, v) { print("{k}: {v}") })

# ── 错误处理 ────────────────────────────────────────────────────────
result = try(fn() { risky() })
if result.is_err() { print(result.error()) }

# ── 类型转换 ────────────────────────────────────────────────────────
n = int("42")       # → 42
f = float("3.14")   # → 3.14
s = str(100)        # → "100"
b = bool(1)         # → true

# ── 运算符 ─────────────────────────────────────────────────────────
area  = side ** 2           # 幂运算
x     = value ?? "默认值"   # 空值合并
count = list.len()          # 长度
```

</details>

---

## 运行要求

| 要求 | 涉及示例 |
|------|---------|
| **Codong v0.1.3+** | 全部 100 个 |
| 网络访问 | 25–28、15–20、76–80 |
| `redis-server`（或 Docker） | 29–32、59、63、66–70、100 |
| `ANTHROPIC_API_KEY` | 15–20 |
| `OPENAI_API_KEY` | 20（可选） |
| `GITHUB_CLIENT_ID` + `GITHUB_CLIENT_SECRET` | 36 |
| `SMTP_HOST` + `SMTP_USER` + `SMTP_PASS` | 96–100 |

```bash
# 安装 Codong（macOS / Linux / Windows WSL）
curl -fsSL https://codong.org/install.sh | sh

# 用 Docker 启动 Redis
docker run -d -p 6379:6379 redis:alpine

# 设置 API Key
export ANTHROPIC_API_KEY=sk-ant-...
```

---

## 贡献指南

欢迎提交新示例，请遵守以下规则：

1. 每个示例一个 `.cod` 文件，除已记录模块外无外部依赖
2. 文件前两行必须是注释：`# 说明` 和 `# codong run <文件名>`
3. 放入正确编号的分类目录
4. 在 README 表格中补充对应行
5. 提交 Pull Request

---

## 许可证

**MIT** —— 自由使用，自由修改，自由分享。

---

<div align="center">

由 [@brettinhere](https://github.com/brettinhere) 用 ❤️ 制作 · [codong.org](https://codong.org)

</div>
