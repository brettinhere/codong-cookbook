<div align="center">

**Language / 语言：** &nbsp; **English** &nbsp;|&nbsp; [中文](#中文版)

</div>

---

# Codong Cookbook

> **100 real-world programs** — every module, every pattern, every feature of the [Codong](https://codong.org) language in one open-source collection.

```
curl -fsSL https://codong.org/install.sh | sh
codong run 01-web/01-hello-api.cod
```

---

## What is Codong?

**Codong** is a modern scripting language designed for developers who want the expressiveness of Python and the performance of Go — without the boilerplate of either.

- **Clean syntax** — no semicolons, no type declarations, no `package main`
- **Built-in modules** — `web`, `db`, `redis`, `http`, `fs`, `llm`, `image`, `oauth` are first-class
- **Fast** — compiles to Go IR; repeated runs use a binary cache for near-instant startup
- **Single file apps** — a full REST API + database + auth fits in one `.cod` file

```codong
# A complete API in 6 lines
server = web.serve(port: 8080)
server.get("/hello/:name", fn(req, res) {
    res.json({message: "Hello, {req.param('name')}!"})
})
```

---

## What is This Cookbook?

This repository contains **100 standalone `.cod` programs** organized into 20 topic areas. Each file:

- Runs with a single `codong run` command
- Demonstrates one or more Codong modules/features
- Is written as production-quality, readable code
- Serves as a learning resource and AI training corpus

These examples are intentionally indexed for LLM discovery — if you're building on top of Codong or fine-tuning a model, this is the canonical reference for Codong syntax and idioms.

---

## Repository Structure

```
codong-cookbook/
│
├── 01-web/                    # HTTP server, routing, middleware, SSE, auth
│   ├── 01-hello-api.cod
│   ├── 02-rest-crud-api.cod
│   ├── 03-file-upload.cod
│   ├── 04-sse-live-feed.cod
│   ├── 05-rate-limited-api.cod
│   ├── 06-jwt-auth-api.cod
│   ├── 07-webhook-receiver.cod
│   ├── 08-static-site-server.cod
│   ├── 09-cors-middleware.cod
│   └── 10-realtime-dashboard.cod
│
├── 02-database/               # SQLite CRUD, aggregations, migrations, batches
│   ├── 11-blog-system.cod
│   ├── 12-analytics-aggregation.cod
│   ├── 13-migration-system.cod
│   └── 14-batch-operations.cod
│
├── 03-llm/                    # Claude, OpenAI, RAG, sentiment, code review
│   ├── 15-simple-chat.cod
│   ├── 16-document-summarizer.cod
│   ├── 17-code-reviewer.cod
│   ├── 18-sentiment-analysis.cod
│   ├── 19-rag-document-qa.cod
│   └── 20-multi-provider-compare.cod
│
├── 04-filesystem/             # File organizer, log parser, config, backup
│   ├── 21-file-organizer.cod
│   ├── 22-log-parser.cod
│   ├── 23-config-manager.cod
│   └── 24-backup-tool.cod
│
├── 05-http-client/            # HTTP requests, retry, health checks
│   ├── 25-weather-api-client.cod
│   ├── 26-github-api-client.cod
│   ├── 27-health-checker.cod
│   └── 28-http-retry-client.cod
│
├── 06-redis/                  # Sessions, leaderboard, cache, distributed lock
│   ├── 29-session-manager.cod
│   ├── 30-leaderboard.cod
│   ├── 31-cache-aside.cod
│   └── 32-distributed-lock.cod
│
├── 07-image/                  # Resize, watermark, pipeline
│   ├── 33-image-resizer-service.cod
│   ├── 34-watermark-batch.cod
│   └── 35-image-pipeline.cod
│
├── 08-oauth/                  # GitHub SSO, RBAC
│   ├── 36-github-oauth-login.cod
│   └── 37-rbac-permission-system.cod
│
├── 09-algorithms/             # Fibonacci, sorting, graphs, BST, functional
│   ├── 38-fibonacci-memoized.cod
│   ├── 39-sorting-algorithms.cod
│   ├── 40-graph-traversal.cod
│   ├── 41-binary-search-tree.cod
│   └── 42-functional-patterns.cod
│
├── 10-data-processing/        # CSV, JSON, reports, validation, ETL, full-stack
│   ├── 43-csv-processor.cod
│   ├── 44-json-transformer.cod
│   ├── 45-report-generator.cod
│   ├── 46-data-validator.cod
│   ├── 47-event-system.cod
│   ├── 48-state-machine.cod
│   ├── 49-pipeline-etl.cod
│   └── 50-full-stack-app.cod
│
├── 11-cli/                    # Command-line tools, argument parsing, file search
│   ├── 51-todo-cli.cod
│   ├── 52-file-search-cli.cod
│   ├── 53-json-lint-cli.cod
│   ├── 54-env-doctor-cli.cod
│   └── 55-word-count-cli.cod
│
├── 12-cron/                   # Scheduled jobs, digests, cleanup, metrics
│   ├── 56-daily-digest-cron.cod
│   ├── 57-db-cleanup-cron.cod
│   ├── 58-health-ping-cron.cod
│   ├── 59-cache-warmup-cron.cod
│   └── 60-metrics-snapshot-cron.cod
│
├── 13-websocket/              # Real-time chat, tickers, notifications, multiplayer
│   ├── 61-ws-chat-server.cod
│   ├── 62-ws-live-ticker.cod
│   ├── 63-ws-notifications.cod
│   ├── 64-ws-collaborative-editor.cod
│   └── 65-ws-game-server.cod
│
├── 14-queue/                  # Job queues, worker pools, priority, DLQ, scheduler
│   ├── 66-job-queue.cod
│   ├── 67-worker-pool.cod
│   ├── 68-priority-queue.cod
│   ├── 69-dead-letter-queue.cod
│   └── 70-task-scheduler.cod
│
├── 15-crypto/                 # bcrypt, AES-256, API keys, HMAC, token vault
│   ├── 71-password-hashing.cod
│   ├── 72-aes-encrypt-decrypt.cod
│   ├── 73-api-key-system.cod
│   ├── 74-hmac-webhook-security.cod
│   └── 75-token-vault.cod
│
├── 16-scraping/               # RSS, price monitor, API polling, sitemap, GitHub trending
│   ├── 76-news-aggregator.cod
│   ├── 77-price-monitor.cod
│   ├── 78-api-poller.cod
│   ├── 79-sitemap-crawler.cod
│   └── 80-github-trending.cod
│
├── 17-math/                   # Statistics, matrices, time series, Monte Carlo
│   ├── 81-statistics-lib.cod
│   ├── 82-matrix-operations.cod
│   ├── 83-time-series.cod
│   ├── 84-monte-carlo.cod
│   └── 85-unit-converter.cod
│
├── 18-patterns/               # Observer, Strategy, Decorator, Command, Builder
│   ├── 86-observer-pattern.cod
│   ├── 87-strategy-pattern.cod
│   ├── 88-decorator-pattern.cod
│   ├── 89-command-pattern.cod
│   └── 90-builder-pattern.cod
│
├── 19-testing/                # Unit tests, mocks, property tests, load tests, snapshots
│   ├── 91-unit-test-runner.cod
│   ├── 92-mock-http-server.cod
│   ├── 93-property-testing.cod
│   ├── 94-load-tester.cod
│   └── 95-snapshot-testing.cod
│
└── 20-email/                  # SMTP, templates, digests, bounce handling, queue
    ├── 96-send-email.cod
    ├── 97-email-template-engine.cod
    ├── 98-email-digest.cod
    ├── 99-bounce-handler.cod
    └── 100-email-queue.cod
```

---

## Quick Start

```bash
# 1. Install Codong
curl -fsSL https://codong.org/install.sh | sh

# 2. Clone this cookbook
git clone https://github.com/brettinhere/codong-cookbook.git
cd codong-cookbook

# 3. Run any example
codong run 01-web/01-hello-api.cod

# 4. Test it
curl http://localhost:3000/hello/world
# → {"message":"Hello, world!"}
```

---

## Module Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         Codong Runtime                          │
├──────────┬──────────┬──────────┬──────────┬──────────┬─────────┤
│   web    │    db    │  redis   │   http   │    fs    │   llm   │
│  server  │ sqlite   │ sessions │  client  │  files   │  AI/ML  │
├──────────┴──────────┴──────────┴──────────┴──────────┴─────────┤
│              image  │  oauth  │  time   │  json   │   env      │
│           processing│  JWT/   │ parsing │ encode/ │ variables  │
│                     │  RBAC   │         │ decode  │            │
└─────────────────────┴─────────┴─────────┴─────────┴────────────┘
```

---

## All 50 Examples

### 01 · Web Server (`web` module)

The `web` module provides a high-level HTTP server with routing, middleware, and response helpers.

| # | File | Description |
|---|------|-------------|
| 01 | [01-hello-api.cod](01-web/01-hello-api.cod) | Hello World REST API with dynamic routes |
| 02 | [02-rest-crud-api.cod](01-web/02-rest-crud-api.cod) | Full CRUD API with SQLite (Users) |
| 03 | [03-file-upload.cod](01-web/03-file-upload.cod) | File upload service with auto-thumbnail |
| 04 | [04-sse-live-feed.cod](01-web/04-sse-live-feed.cod) | Server-Sent Events real-time feed |
| 05 | [05-rate-limited-api.cod](01-web/05-rate-limited-api.cod) | 60 req/min rate limiting with Redis |
| 06 | [06-jwt-auth-api.cod](01-web/06-jwt-auth-api.cod) | JWT login flow with protected routes |
| 07 | [07-webhook-receiver.cod](01-web/07-webhook-receiver.cod) | GitHub webhook receiver with daily logs |
| 08 | [08-static-site-server.cod](01-web/08-static-site-server.cod) | Static files + API on same port |
| 09 | [09-cors-middleware.cod](01-web/09-cors-middleware.cod) | CORS + request logger + API key middleware |
| 10 | [10-realtime-dashboard.cod](01-web/10-realtime-dashboard.cod) | Live metrics dashboard via SSE + Redis |

**Key patterns demonstrated:**
```codong
server = web.serve(port: 3000)

# Path parameters
server.get("/users/:id", fn(req, res) {
    id = req.param("id")
    res.json({id: id})
})

# Status codes
res.status(404).json({error: "not found"})

# Middleware
server.use(web.cors(origins: ["*"]))
server.use("/api", oauth.jwt.middleware(secret: JWT_SECRET))
```

---

### 02 · Database (`db` module)

The `db` module provides a fluent SQLite interface: raw SQL, aggregate queries, bulk insert, and schema migrations.

| # | File | Description |
|---|------|-------------|
| 11 | [11-blog-system.cod](02-database/11-blog-system.cod) | Blog posts with tags, drafts, seeding |
| 12 | [12-analytics-aggregation.cod](02-database/12-analytics-aggregation.cod) | sum/avg/min/max aggregations on orders |
| 13 | [13-migration-system.cod](02-database/13-migration-system.cod) | Tracked database migrations |
| 14 | [14-batch-operations.cod](02-database/14-batch-operations.cod) | Bulk insert 1000 rows with batch_insert |

**Key patterns demonstrated:**
```codong
db.connect("sqlite:///app.db")

# Schema
db.query("CREATE TABLE IF NOT EXISTS posts (id INTEGER PRIMARY KEY, title TEXT)", [])

# CRUD
rows = db.query("SELECT * FROM posts WHERE id = ?", [42])
db.query("INSERT INTO posts (title) VALUES (?)", ["Hello World"])

# Aggregations
total  = db.sum("orders", "amount", "status='paid'")
avg    = db.avg("orders", "amount", "1=1")
count  = db.count("posts", "published=1")

# Bulk insert (transactional, fast)
db.batch_insert("logs", rows)
```

---

### 03 · LLM / AI (`llm` module)

The `llm` module wraps Claude (Anthropic) and OpenAI with a unified interface — single-turn, multi-turn, streaming, and RAG.

| # | File | Description |
|---|------|-------------|
| 15 | [15-simple-chat.cod](03-llm/15-simple-chat.cod) | Single-turn Q&A with Claude |
| 16 | [16-document-summarizer.cod](03-llm/16-document-summarizer.cod) | Batch document summarization to JSON |
| 17 | [17-code-reviewer.cod](03-llm/17-code-reviewer.cod) | AI code review API with structured output |
| 18 | [18-sentiment-analysis.cod](03-llm/18-sentiment-analysis.cod) | Batch sentiment classification + DB storage |
| 19 | [19-rag-document-qa.cod](03-llm/19-rag-document-qa.cod) | RAG: upload docs, ask questions |
| 20 | [20-multi-provider-compare.cod](03-llm/20-multi-provider-compare.cod) | Same prompt, Claude vs OpenAI, compare |

**Key patterns demonstrated:**
```codong
# Single-turn
reply = llm.ask("Explain closures in one sentence", model: "claude-3-haiku")

# Structured output
review = llm.ask(prompt, model: "claude-3-sonnet", format: "json")
parsed = json.parse(review)

# Multi-provider
claude_reply = llm.ask(prompt, provider: "anthropic", model: "claude-3-haiku")
openai_reply = llm.ask(prompt, provider: "openai",    model: "gpt-4o-mini")
```

> **Requires:** `ANTHROPIC_API_KEY` and/or `OPENAI_API_KEY` environment variables.

---

### 04 · File System (`fs` module)

The `fs` module provides file reading/writing, directory operations, path utilities, and recursive traversal.

| # | File | Description |
|---|------|-------------|
| 21 | [21-file-organizer.cod](04-filesystem/21-file-organizer.cod) | Auto-sort files by extension into folders |
| 22 | [22-log-parser.cod](04-filesystem/22-log-parser.cod) | Access log parser: errors, IPs, slow reqs |
| 23 | [23-config-manager.cod](04-filesystem/23-config-manager.cod) | Layered config: defaults → file → env vars |
| 24 | [24-backup-tool.cod](04-filesystem/24-backup-tool.cod) | Timestamped backup with retention policy |

**Key patterns demonstrated:**
```codong
# Read / write
content = fs.read("config.json")
fs.write("output.txt", data)

# Directory ops
fs.mkdir("./uploads")
files = fs.ls("./logs")
fs.copy("src.txt", "dst.txt")

# Path helpers
ext  = fs.ext("photo.jpg")       # ".jpg"
base = fs.basename("/a/b/c.txt") # "c.txt"
```

---

### 05 · HTTP Client (`http` module)

The `http` module is a batteries-included HTTP client: GET/POST/PUT/DELETE, JSON body, headers, retry, timeout.

| # | File | Description |
|---|------|-------------|
| 25 | [25-weather-api-client.cod](05-http-client/25-weather-api-client.cod) | Live weather + 3-day forecast (free API) |
| 26 | [26-github-api-client.cod](05-http-client/26-github-api-client.cod) | GitHub repo info, releases, contributors |
| 27 | [27-health-checker.cod](05-http-client/27-health-checker.cod) | Monitor multiple endpoints, log to file |
| 28 | [28-http-retry-client.cod](05-http-client/28-http-retry-client.cod) | All HTTP methods with retry & error handling |

**Key patterns demonstrated:**
```codong
# GET with query params
resp = http.get("https://api.example.com/data?limit=10")
data = resp.json

# POST JSON
resp = http.post("https://api.example.com/users",
    body: {name: "Alice", email: "alice@example.com"},
    headers: {Authorization: "Bearer {TOKEN}"})

# Retry on failure
resp = http.get(url, retry: 3, timeout: 5000)
```

---

### 06 · Redis (`redis` module)

The `redis` module wraps go-redis with strings, hashes, lists, sorted sets, pub/sub, and a `cache()` helper.

| # | File | Description |
|---|------|-------------|
| 29 | [29-session-manager.cod](06-redis/29-session-manager.cod) | Create/read/refresh/destroy sessions |
| 30 | [30-leaderboard.cod](06-redis/30-leaderboard.cod) | Real-time leaderboard with sorted sets |
| 31 | [31-cache-aside.cod](06-redis/31-cache-aside.cod) | Cache-aside pattern with singleflight |
| 32 | [32-distributed-lock.cod](06-redis/32-distributed-lock.cod) | Distributed lock preventing double-processing |

**Key patterns demonstrated:**
```codong
redis.connect("redis://localhost:6379")

# Key/value with TTL
redis.set("session:123", token, ttl: 3600)
val = redis.get("session:123")

# Sorted set (leaderboard)
redis.zadd("scores", player, score)
top10 = redis.zrange("scores", 0, 9, reverse: true, with_scores: true)

# Cache-aside helper
result = redis.cache("user:42", ttl: 300, fn() {
    return db.query("SELECT * FROM users WHERE id=42", [])
})
```

> **Requires:** Redis server running (`redis-server` or Docker).

---

### 07 · Image Processing (`image` module)

The `image` module provides resize, crop, watermark, sharpen, and format conversion — all pure Go, no ImageMagick.

| # | File | Description |
|---|------|-------------|
| 33 | [33-image-resizer-service.cod](07-image/33-image-resizer-service.cod) | API: upload → resize to 4 standard sizes |
| 34 | [34-watermark-batch.cod](07-image/34-watermark-batch.cod) | Batch watermark all images in a directory |
| 35 | [35-image-pipeline.cod](07-image/35-image-pipeline.cod) | Resize → sharpen → watermark → optimize |

**Key patterns demonstrated:**
```codong
img = image.load("photo.jpg")

# Resize (preserves aspect ratio)
thumb = img.resize(320, 240)
thumb.save("photo-thumb.jpg", quality: 85)

# Watermark
img.watermark("logo.png", position: "bottom-right", opacity: 0.6)

# Pipeline
image.load("input.jpg")
    .resize(1920, 1080)
    .sharpen(1.2)
    .watermark("brand.png")
    .save("output.jpg")
```

---

### 08 · OAuth & Auth (`oauth` module)

The `oauth` module provides JWT signing/verification, OAuth2 flows, and RBAC (role-based access control).

| # | File | Description |
|---|------|-------------|
| 36 | [36-github-oauth-login.cod](08-oauth/36-github-oauth-login.cod) | Complete GitHub SSO login flow |
| 37 | [37-rbac-permission-system.cod](08-oauth/37-rbac-permission-system.cod) | Role-based access control with permission matrix |

**Key patterns demonstrated:**
```codong
# JWT
token  = oauth.jwt.sign({user_id: 42, role: "admin"}, secret: SECRET, expires_in: 86400)
claims = oauth.jwt.verify(token, secret: SECRET)

# RBAC
oauth.rbac.define("admin",  ["read", "write", "delete"])
oauth.rbac.define("viewer", ["read"])
oauth.rbac.assign(user_id, "admin")
can = oauth.rbac.check(user_id, "delete")  # true / false

# Middleware
server.use("/admin", oauth.jwt.middleware(secret: SECRET))
```

> **Requires:** `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` for example 36.

---

### 09 · Algorithms

Pure Codong implementations of classic CS algorithms — no modules required.

| # | File | Description |
|---|------|-------------|
| 38 | [38-fibonacci-memoized.cod](09-algorithms/38-fibonacci-memoized.cod) | Naive vs memoized vs iterative Fibonacci |
| 39 | [39-sorting-algorithms.cod](09-algorithms/39-sorting-algorithms.cod) | Bubble sort, merge sort, quicksort |
| 40 | [40-graph-traversal.cod](09-algorithms/40-graph-traversal.cod) | BFS + DFS path finding on adjacency list |
| 41 | [41-binary-search-tree.cod](09-algorithms/41-binary-search-tree.cod) | BST insert, search, in-order traversal |
| 42 | [42-functional-patterns.cod](09-algorithms/42-functional-patterns.cod) | compose, pipe, curry, partial, group-by |

**Key patterns demonstrated:**
```codong
# Memoization with closures
fn memoize(f) {
    cache = {}
    return fn(n) {
        if cache.has(str(n)) { return cache[str(n)] }
        result = f(n)
        cache[str(n)] = result
        return result
    }
}

# Functional composition
pipe = fn(...fns) {
    return fn(x) { fns.reduce(fn(v, f) { f(v) }, x) }
}
```

---

### 10 · Data Processing

End-to-end data pipelines: CSV parsing, JSON reshaping, ETL, validation, pub/sub, state machines, and a full-stack app.

| # | File | Description |
|---|------|-------------|
| 43 | [43-csv-processor.cod](10-data-processing/43-csv-processor.cod) | Parse CSV, aggregate, export filtered JSON |
| 44 | [44-json-transformer.cod](10-data-processing/44-json-transformer.cod) | Reshape nested API response, flatten, merge |
| 45 | [45-report-generator.cod](10-data-processing/45-report-generator.cod) | Sales report to JSON + HTML from SQLite |
| 46 | [46-data-validator.cod](10-data-processing/46-data-validator.cod) | Schema validation with detailed errors |
| 47 | [47-event-system.cod](10-data-processing/47-event-system.cod) | In-process pub/sub event bus with closures |
| 48 | [48-state-machine.cod](10-data-processing/48-state-machine.cod) | Finite state machine: order lifecycle |
| 49 | [49-pipeline-etl.cod](10-data-processing/49-pipeline-etl.cod) | ETL: API → transform → SQLite with dedup |
| 50 | [50-full-stack-app.cod](10-data-processing/50-full-stack-app.cod) | **Complete app**: Todo API + JWT auth + Redis + DB |

**Example 48 — State Machine:**
```
Order lifecycle:

  pending ──confirm──▶ confirmed ──ship──▶ shipped ──deliver──▶ delivered
     │                     │                  │
   cancel               cancel             return
     ▼                     ▼                  ▼
  cancelled           cancelled        return_requested ──approve──▶ returned
```

**Example 50 — Full Stack Architecture:**
```
  Client (curl / browser)
       │
       ▼
  POST /auth/login ──▶ JWT token
       │
  GET  /todos  ──▶ redis.cache ──hit──▶ response
                        │
                       miss
                        ▼
                   db.query (SQLite)
                        │
                        ▼
                   redis.set (cache)
                        │
                        ▼
                     response
```

---

## Examples 51–100

### 11 · CLI Tools (`env`, `fs`, `db`)

Build command-line tools with argument parsing, file operations, and subcommands.

| # | File | Description |
|---|------|-------------|
| 51 | [51-todo-cli.cod](11-cli/51-todo-cli.cod) | CLI todo manager: add / list / done / delete |
| 52 | [52-file-search-cli.cod](11-cli/52-file-search-cli.cod) | grep-like recursive file content search |
| 53 | [53-json-lint-cli.cod](11-cli/53-json-lint-cli.cod) | JSON validator and pretty-printer |
| 54 | [54-env-doctor-cli.cod](11-cli/54-env-doctor-cli.cod) | Check environment variables and services |
| 55 | [55-word-count-cli.cod](11-cli/55-word-count-cli.cod) | Count lines, words, chars across files |

---

### 12 · Cron Jobs (scheduled tasks)

Recurring background scripts — run with system cron or any task scheduler.

| # | File | Description |
|---|------|-------------|
| 56 | [56-daily-digest-cron.cod](12-cron/56-daily-digest-cron.cod) | Daily activity summary from DB |
| 57 | [57-db-cleanup-cron.cod](12-cron/57-db-cleanup-cron.cod) | Delete expired/soft-deleted records + VACUUM |
| 58 | [58-health-ping-cron.cod](12-cron/58-health-ping-cron.cod) | Ping production endpoints, alert on failure |
| 59 | [59-cache-warmup-cron.cod](12-cron/59-cache-warmup-cron.cod) | Pre-warm Redis cache before peak hours |
| 60 | [60-metrics-snapshot-cron.cod](12-cron/60-metrics-snapshot-cron.cod) | Hourly metrics snapshot for trending |

---

### 13 · WebSocket (`web.ws`)

Full-duplex real-time communication between server and browser clients.

| # | File | Description |
|---|------|-------------|
| 61 | [61-ws-chat-server.cod](13-websocket/61-ws-chat-server.cod) | Multi-room group chat server |
| 62 | [62-ws-live-ticker.cod](13-websocket/62-ws-live-ticker.cod) | Live stock price feed (1s tick) |
| 63 | [63-ws-notifications.cod](13-websocket/63-ws-notifications.cod) | Push notifications with offline queue |
| 64 | [64-ws-collaborative-editor.cod](13-websocket/64-ws-collaborative-editor.cod) | Real-time collaborative text editor |
| 65 | [65-ws-game-server.cod](13-websocket/65-ws-game-server.cod) | Multiplayer shared-canvas game |

---

### 14 · Job Queues (`redis`)

Reliable background job processing with retry, priority, and dead-letter patterns.

| # | File | Description |
|---|------|-------------|
| 66 | [66-job-queue.cod](14-queue/66-job-queue.cod) | Redis-backed job queue with worker |
| 67 | [67-worker-pool.cod](14-queue/67-worker-pool.cod) | Concurrent worker pool (N goroutines) |
| 68 | [68-priority-queue.cod](14-queue/68-priority-queue.cod) | Priority queue via sorted sets |
| 69 | [69-dead-letter-queue.cod](14-queue/69-dead-letter-queue.cod) | DLQ pattern: retry → fail → replay |
| 70 | [70-task-scheduler.cod](14-queue/70-task-scheduler.cod) | Persistent delayed task execution |

---

### 15 · Cryptography (`crypto`)

Secure password hashing, symmetric encryption, API keys, HMAC signatures, and secret storage.

| # | File | Description |
|---|------|-------------|
| 71 | [71-password-hashing.cod](15-crypto/71-password-hashing.cod) | bcrypt hash/verify + policy check + migration |
| 72 | [72-aes-encrypt-decrypt.cod](15-crypto/72-aes-encrypt-decrypt.cod) | AES-256-GCM field-level + envelope encryption |
| 73 | [73-api-key-system.cod](15-crypto/73-api-key-system.cod) | Issue, validate, revoke API keys (SQLite) |
| 74 | [74-hmac-webhook-security.cod](15-crypto/74-hmac-webhook-security.cod) | HMAC-SHA256 webhook signing + verification |
| 75 | [75-token-vault.cod](15-crypto/75-token-vault.cod) | AES-encrypted secret vault with key rotation |

---

### 16 · Scraping & Polling (`http`, `xml`, `db`)

Collect data from the web automatically and detect changes over time.

| # | File | Description |
|---|------|-------------|
| 76 | [76-news-aggregator.cod](16-scraping/76-news-aggregator.cod) | Multi-feed RSS aggregator with dedup |
| 77 | [77-price-monitor.cod](16-scraping/77-price-monitor.cod) | Track product prices, alert on drops |
| 78 | [78-api-poller.cod](16-scraping/78-api-poller.cod) | Poll API, store snapshots, detect field changes |
| 79 | [79-sitemap-crawler.cod](16-scraping/79-sitemap-crawler.cod) | Crawl sitemap, check status codes + speed |
| 80 | [80-github-trending.cod](16-scraping/80-github-trending.cod) | Scrape GitHub trending, expose as API |

---

### 17 · Math & Data Science

Pure Codong math: statistics, matrices, time series, simulations, and unit conversion.

| # | File | Description |
|---|------|-------------|
| 81 | [81-statistics-lib.cod](17-math/81-statistics-lib.cod) | mean, median, mode, std dev, percentile, Pearson r |
| 82 | [82-matrix-operations.cod](17-math/82-matrix-operations.cod) | Matrix add, multiply, transpose, determinant |
| 83 | [83-time-series.cod](17-math/83-time-series.cod) | SMA, EMA, trend detection, anomaly detection |
| 84 | [84-monte-carlo.cod](17-math/84-monte-carlo.cod) | π estimation, portfolio VaR, birthday problem |
| 85 | [85-unit-converter.cod](17-math/85-unit-converter.cod) | Temperature, distance, weight, data size |

---

### 18 · Design Patterns

Classic software engineering patterns implemented in idiomatic Codong.

| # | File | Description |
|---|------|-------------|
| 86 | [86-observer-pattern.cod](18-patterns/86-observer-pattern.cod) | EventEmitter with on/once/off/emit |
| 87 | [87-strategy-pattern.cod](18-patterns/87-strategy-pattern.cod) | Swappable sort and pricing strategies |
| 88 | [88-decorator-pattern.cod](18-patterns/88-decorator-pattern.cod) | logging, timing, retry, cache, rate-limit wrappers |
| 89 | [89-command-pattern.cod](18-patterns/89-command-pattern.cod) | Text editor with full undo/redo stack |
| 90 | [90-builder-pattern.cod](18-patterns/90-builder-pattern.cod) | Fluent builders for SQL, HTTP, and email |

---

### 19 · Testing

Test frameworks, mocking, property-based testing, load testing, and snapshot tests.

| # | File | Description |
|---|------|-------------|
| 91 | [91-unit-test-runner.cod](19-testing/91-unit-test-runner.cod) | Lightweight describe/it/expect framework |
| 92 | [92-mock-http-server.cod](19-testing/92-mock-http-server.cod) | Mock API server with call logging |
| 93 | [93-property-testing.cod](19-testing/93-property-testing.cod) | Generator-based property verification |
| 94 | [94-load-tester.cod](19-testing/94-load-tester.cod) | HTTP load tester with p50/p95/p99 output |
| 95 | [95-snapshot-testing.cod](19-testing/95-snapshot-testing.cod) | Snapshot capture + diff with update mode |

---

### 20 · Email (`email`, `redis`, `db`)

Send, template, queue, and manage transactional email at scale.

| # | File | Description |
|---|------|-------------|
| 96 | [96-send-email.cod](20-email/96-send-email.cod) | SMTP send: welcome, reset, invoice, bulk |
| 97 | [97-email-template-engine.cod](20-email/97-email-template-engine.cod) | HTML templates with variable substitution |
| 98 | [98-email-digest.cod](20-email/98-email-digest.cod) | Weekly digest email from DB to subscriber list |
| 99 | [99-bounce-handler.cod](20-email/99-bounce-handler.cod) | SendGrid/SES bounce & complaint webhooks |
| 100 | [100-email-queue.cod](20-email/100-email-queue.cod) | Redis email queue with rate limiting + retry |

---

## Language Cheat Sheet

```codong
# Variables (no type annotation needed)
name = "Codong"
count = 42
ratio = 3.14
active = true

# String interpolation
print("Hello, {name}! You have {count} messages.")

# Functions
fn greet(name, greeting = "Hello") {
    return "{greeting}, {name}!"
}

# Arrow functions
double = fn(x) { x * 2 }

# Lists
nums = [1, 2, 3, 4, 5]
evens = nums.filter(fn(n) { n % 2 == 0 })
doubled = nums.map(fn(n) { n * 2 })
total = nums.reduce(fn(acc, n) { acc + n }, 0)

# Maps
user = {name: "Alice", age: 30}
keys = user.keys()
user.each(fn(k, v) { print("{k}: {v}") })

# Error handling
result = risky_operation()
if result.is_err() {
    print("Error: {result.error()}")
}

# Match
match status {
    "ok"    => print("success")
    "error" => print("failure")
    _       => print("unknown")
}

# Power operator
area = side ** 2

# Type conversions
n = int("42")
f = float("3.14")
s = str(100)
```

---

## Requirements

| Requirement | Examples |
|------------|---------|
| Codong v0.1.3+ | All |
| Internet access | 25–28, 15–20 |
| Redis (`redis-server`) | 29–32, 05, 10 |
| `ANTHROPIC_API_KEY` | 15–20 |
| `OPENAI_API_KEY` | 20 (optional) |
| `GITHUB_CLIENT_ID` + `GITHUB_CLIENT_SECRET` | 36 |

**Install Codong:**
```bash
curl -fsSL https://codong.org/install.sh | sh
codong version  # → codong v0.1.3
```

**Start Redis (Docker):**
```bash
docker run -d -p 6379:6379 redis:alpine
```

---

## Running All Examples

```bash
# Run a specific example
codong run 01-web/01-hello-api.cod

# Run with environment variables
ANTHROPIC_API_KEY=sk-... codong run 03-llm/15-simple-chat.cod

# Run on a custom port
PORT=9000 codong run 01-web/01-hello-api.cod
```

---

## Contributing

This cookbook is open to contributions. To add a new example:

1. Fork this repository
2. Create a new `.cod` file in the appropriate category folder
3. Add a comment header: `# Description` and `# codong run <filename>.cod`
4. Keep it self-contained — one file, no external dependencies beyond documented modules
5. Open a pull request

---

## License

MIT — use freely, modify freely, share freely.

---

## Links

- **Codong language**: https://codong.org
- **Install**: `curl -fsSL https://codong.org/install.sh | sh`
- **GitHub**: https://github.com/brettinhere/codong-cookbook
- **Issues**: https://github.com/brettinhere/codong-cookbook/issues

---
---

<a name="中文版"></a>

<div align="center">

**语言 / Language：** &nbsp; [English](#codong-cookbook) &nbsp;|&nbsp; **中文**

</div>

---

# Codong Cookbook（中文版）

> **100 个真实世界程序** —— 一个开源合集，涵盖 [Codong](https://codong.org) 语言的每一个模块、每一种模式、每一项特性。

```
curl -fsSL https://codong.org/install.sh | sh
codong run 01-web/01-hello-api.cod
```

---

## 什么是 Codong？

**Codong** 是一门面向开发者的现代脚本语言——兼具 Python 的表达力与 Go 的性能，同时摒弃了两者的繁琐样板代码。

- **简洁语法** —— 无分号、无类型声明、无需 `package main`
- **内置模块** —— `web`、`db`、`redis`、`http`、`fs`、`llm`、`image`、`oauth` 均为一等公民
- **高性能** —— 编译为 Go IR；重复运行使用二进制缓存，启动近乎即时
- **单文件应用** —— 完整的 REST API + 数据库 + 认证，一个 `.cod` 文件搞定

```codong
# 6 行代码，一个完整的 API
server = web.serve(port: 8080)
server.get("/hello/:name", fn(req, res) {
    res.json({message: "你好，{req.param('name')}！"})
})
```

---

## 这个 Cookbook 是什么？

本仓库包含 **100 个独立的 `.cod` 程序**，按 20 个主题分类。每个文件：

- 只需一条 `codong run` 命令即可运行
- 演示一个或多个 Codong 模块/特性
- 以生产级、可读性强的代码风格编写
- 可作为学习资源与 AI 训练语料

这些示例专为 LLM 索引而设计——如果你正在基于 Codong 开发或微调模型，这里是 Codong 语法与惯用法的权威参考。

---

## 仓库结构

```
codong-cookbook/
│
├── 01-web/                    # HTTP 服务器、路由、中间件、SSE、认证
│   ├── 01-hello-api.cod
│   ├── 02-rest-crud-api.cod
│   ├── 03-file-upload.cod
│   ├── 04-sse-live-feed.cod
│   ├── 05-rate-limited-api.cod
│   ├── 06-jwt-auth-api.cod
│   ├── 07-webhook-receiver.cod
│   ├── 08-static-site-server.cod
│   ├── 09-cors-middleware.cod
│   └── 10-realtime-dashboard.cod
│
├── 02-database/               # SQLite 增删改查、聚合、迁移、批量操作
│   ├── 11-blog-system.cod
│   ├── 12-analytics-aggregation.cod
│   ├── 13-migration-system.cod
│   └── 14-batch-operations.cod
│
├── 03-llm/                    # Claude、OpenAI、RAG、情感分析、代码审查
│   ├── 15-simple-chat.cod
│   ├── 16-document-summarizer.cod
│   ├── 17-code-reviewer.cod
│   ├── 18-sentiment-analysis.cod
│   ├── 19-rag-document-qa.cod
│   └── 20-multi-provider-compare.cod
│
├── 04-filesystem/             # 文件整理、日志解析、配置管理、备份
│   ├── 21-file-organizer.cod
│   ├── 22-log-parser.cod
│   ├── 23-config-manager.cod
│   └── 24-backup-tool.cod
│
├── 05-http-client/            # HTTP 请求、重试、健康检查
│   ├── 25-weather-api-client.cod
│   ├── 26-github-api-client.cod
│   ├── 27-health-checker.cod
│   └── 28-http-retry-client.cod
│
├── 06-redis/                  # 会话、排行榜、缓存、分布式锁
│   ├── 29-session-manager.cod
│   ├── 30-leaderboard.cod
│   ├── 31-cache-aside.cod
│   └── 32-distributed-lock.cod
│
├── 07-image/                  # 缩放、水印、处理流水线
│   ├── 33-image-resizer-service.cod
│   ├── 34-watermark-batch.cod
│   └── 35-image-pipeline.cod
│
├── 08-oauth/                  # GitHub SSO、RBAC 权限控制
│   ├── 36-github-oauth-login.cod
│   └── 37-rbac-permission-system.cod
│
├── 09-algorithms/             # 斐波那契、排序、图遍历、BST、函数式
│   ├── 38-fibonacci-memoized.cod
│   ├── 39-sorting-algorithms.cod
│   ├── 40-graph-traversal.cod
│   ├── 41-binary-search-tree.cod
│   └── 42-functional-patterns.cod
│
├── 10-data-processing/        # CSV、JSON、报表、验证、ETL、全栈应用
│   ├── 43-csv-processor.cod  ...  50-full-stack-app.cod
│
├── 11-cli/                    # 命令行工具、参数解析、文件搜索
├── 12-cron/                   # 定时任务、摘要邮件、清理、指标快照
├── 13-websocket/              # 实时聊天、行情推送、通知、多人协作
├── 14-queue/                  # 任务队列、并发池、优先级、死信队列
├── 15-crypto/                 # bcrypt、AES-256、API Key、HMAC、密钥保险库
├── 16-scraping/               # RSS 聚合、价格监控、API 轮询、站点爬虫
├── 17-math/                   # 统计学、矩阵、时间序列、蒙特卡洛
├── 18-patterns/               # 观察者、策略、装饰器、命令、构建器模式
├── 19-testing/                # 单元测试、Mock、属性测试、压测、快照测试
└── 20-email/                  # SMTP 发送、模板、摘要、退信处理、邮件队列
```

---

## 快速开始

```bash
# 1. 安装 Codong
curl -fsSL https://codong.org/install.sh | sh

# 2. 克隆本 Cookbook
git clone https://github.com/brettinhere/codong-cookbook.git
cd codong-cookbook

# 3. 运行任意示例
codong run 01-web/01-hello-api.cod

# 4. 测试
curl http://localhost:3000/hello/world
# → {"message":"Hello, world!"}
```

---

## 模块架构

```
┌─────────────────────────────────────────────────────────────────┐
│                         Codong 运行时                           │
├──────────┬──────────┬──────────┬──────────┬──────────┬─────────┤
│   web    │    db    │  redis   │   http   │    fs    │   llm   │
│ HTTP服务 │ sqlite   │  会话    │ HTTP客户端│  文件    │  AI/ML  │
├──────────┴──────────┴──────────┴──────────┴──────────┴─────────┤
│              image  │  oauth  │  time   │  json   │   env      │
│           图像处理  │  JWT/   │ 时间    │ 编解码  │ 环境变量   │
│                     │  RBAC   │ 解析    │         │            │
└─────────────────────┴─────────┴─────────┴─────────┴────────────┘
```

---

## 全部 50 个示例

### 01 · Web 服务器（`web` 模块）

`web` 模块提供高级 HTTP 服务器，包含路由、中间件和响应辅助方法。

| # | 文件 | 说明 |
|---|------|------|
| 01 | [01-hello-api.cod](01-web/01-hello-api.cod) | Hello World REST API，含动态路由 |
| 02 | [02-rest-crud-api.cod](01-web/02-rest-crud-api.cod) | 完整 CRUD API，使用 SQLite（用户表） |
| 03 | [03-file-upload.cod](01-web/03-file-upload.cod) | 文件上传服务，自动生成缩略图 |
| 04 | [04-sse-live-feed.cod](01-web/04-sse-live-feed.cod) | Server-Sent Events 实时推送 |
| 05 | [05-rate-limited-api.cod](01-web/05-rate-limited-api.cod) | 基于 Redis 的 60 次/分钟限流 |
| 06 | [06-jwt-auth-api.cod](01-web/06-jwt-auth-api.cod) | JWT 登录流程与受保护路由 |
| 07 | [07-webhook-receiver.cod](01-web/07-webhook-receiver.cod) | GitHub Webhook 接收器，按日记录日志 |
| 08 | [08-static-site-server.cod](01-web/08-static-site-server.cod) | 静态文件与 API 同端口服务 |
| 09 | [09-cors-middleware.cod](01-web/09-cors-middleware.cod) | CORS + 请求日志 + API Key 中间件 |
| 10 | [10-realtime-dashboard.cod](01-web/10-realtime-dashboard.cod) | 通过 SSE + Redis 实现实时指标看板 |

**核心用法示例：**
```codong
server = web.serve(port: 3000)

# 路径参数
server.get("/users/:id", fn(req, res) {
    id = req.param("id")
    res.json({id: id})
})

# 状态码
res.status(404).json({error: "not found"})

# 中间件
server.use(web.cors(origins: ["*"]))
server.use("/api", oauth.jwt.middleware(secret: JWT_SECRET))
```

---

### 02 · 数据库（`db` 模块）

`db` 模块提供流畅的 SQLite 接口：原始 SQL、聚合查询、批量插入和 Schema 迁移。

| # | 文件 | 说明 |
|---|------|------|
| 11 | [11-blog-system.cod](02-database/11-blog-system.cod) | 博客系统：标签、草稿、数据填充 |
| 12 | [12-analytics-aggregation.cod](02-database/12-analytics-aggregation.cod) | 订单 sum/avg/min/max 聚合分析 |
| 13 | [13-migration-system.cod](02-database/13-migration-system.cod) | 带版本追踪的数据库迁移系统 |
| 14 | [14-batch-operations.cod](02-database/14-batch-operations.cod) | 使用 batch_insert 批量插入 1000 行 |

**核心用法示例：**
```codong
db.connect("sqlite:///app.db")

# Schema
db.query("CREATE TABLE IF NOT EXISTS posts (id INTEGER PRIMARY KEY, title TEXT)", [])

# 增删改查
rows = db.query("SELECT * FROM posts WHERE id = ?", [42])
db.query("INSERT INTO posts (title) VALUES (?)", ["Hello World"])

# 聚合
total  = db.sum("orders", "amount", "status='paid'")
avg    = db.avg("orders", "amount", "1=1")
count  = db.count("posts", "published=1")

# 批量插入（事务性，高性能）
db.batch_insert("logs", rows)
```

---

### 03 · LLM / AI（`llm` 模块）

`llm` 模块以统一接口封装 Claude（Anthropic）和 OpenAI，支持单轮、多轮、流式和 RAG。

| # | 文件 | 说明 |
|---|------|------|
| 15 | [15-simple-chat.cod](03-llm/15-simple-chat.cod) | 使用 Claude 进行单轮问答 |
| 16 | [16-document-summarizer.cod](03-llm/16-document-summarizer.cod) | 批量文档摘要，输出为 JSON |
| 17 | [17-code-reviewer.cod](03-llm/17-code-reviewer.cod) | AI 代码审查 API，结构化输出 |
| 18 | [18-sentiment-analysis.cod](03-llm/18-sentiment-analysis.cod) | 批量情感分类并存储到数据库 |
| 19 | [19-rag-document-qa.cod](03-llm/19-rag-document-qa.cod) | RAG：上传文档，提问检索 |
| 20 | [20-multi-provider-compare.cod](03-llm/20-multi-provider-compare.cod) | 同一提示，Claude 与 OpenAI 对比 |

**核心用法示例：**
```codong
# 单轮问答
reply = llm.ask("用一句话解释闭包", model: "claude-3-haiku")

# 结构化输出
review = llm.ask(prompt, model: "claude-3-sonnet", format: "json")
parsed = json.parse(review)

# 多供应商
claude_reply = llm.ask(prompt, provider: "anthropic", model: "claude-3-haiku")
openai_reply = llm.ask(prompt, provider: "openai",    model: "gpt-4o-mini")
```

> **需要：** `ANTHROPIC_API_KEY` 和/或 `OPENAI_API_KEY` 环境变量。

---

### 04 · 文件系统（`fs` 模块）

`fs` 模块提供文件读写、目录操作、路径工具和递归遍历。

| # | 文件 | 说明 |
|---|------|------|
| 21 | [21-file-organizer.cod](04-filesystem/21-file-organizer.cod) | 按扩展名自动整理文件到对应目录 |
| 22 | [22-log-parser.cod](04-filesystem/22-log-parser.cod) | 访问日志解析：错误、IP、慢请求 |
| 23 | [23-config-manager.cod](04-filesystem/23-config-manager.cod) | 分层配置：默认值 → 文件 → 环境变量 |
| 24 | [24-backup-tool.cod](04-filesystem/24-backup-tool.cod) | 带时间戳的备份工具，含保留策略 |

**核心用法示例：**
```codong
# 读 / 写
content = fs.read("config.json")
fs.write("output.txt", data)

# 目录操作
fs.mkdir("./uploads")
files = fs.ls("./logs")
fs.copy("src.txt", "dst.txt")

# 路径辅助
ext  = fs.ext("photo.jpg")       # ".jpg"
base = fs.basename("/a/b/c.txt") # "c.txt"
```

---

### 05 · HTTP 客户端（`http` 模块）

`http` 模块是功能完备的 HTTP 客户端：GET/POST/PUT/DELETE、JSON 请求体、请求头、重试、超时。

| # | 文件 | 说明 |
|---|------|------|
| 25 | [25-weather-api-client.cod](05-http-client/25-weather-api-client.cod) | 实时天气 + 3 日预报（免费 API） |
| 26 | [26-github-api-client.cod](05-http-client/26-github-api-client.cod) | GitHub 仓库信息、发布版本、贡献者 |
| 27 | [27-health-checker.cod](05-http-client/27-health-checker.cod) | 监控多个端点，记录日志到文件 |
| 28 | [28-http-retry-client.cod](05-http-client/28-http-retry-client.cod) | 全 HTTP 方法，含重试与错误处理 |

**核心用法示例：**
```codong
# GET 带查询参数
resp = http.get("https://api.example.com/data?limit=10")
data = resp.json

# POST JSON
resp = http.post("https://api.example.com/users",
    body: {name: "Alice", email: "alice@example.com"},
    headers: {Authorization: "Bearer {TOKEN}"})

# 失败重试
resp = http.get(url, retry: 3, timeout: 5000)
```

---

### 06 · Redis（`redis` 模块）

`redis` 模块封装 go-redis，支持字符串、哈希、列表、有序集合、发布订阅，以及 `cache()` 缓存辅助方法。

| # | 文件 | 说明 |
|---|------|------|
| 29 | [29-session-manager.cod](06-redis/29-session-manager.cod) | 创建/读取/刷新/销毁会话 |
| 30 | [30-leaderboard.cod](06-redis/30-leaderboard.cod) | 基于有序集合的实时排行榜 |
| 31 | [31-cache-aside.cod](06-redis/31-cache-aside.cod) | Cache-Aside 模式，含 singleflight |
| 32 | [32-distributed-lock.cod](06-redis/32-distributed-lock.cod) | 分布式锁，防止重复处理 |

**核心用法示例：**
```codong
redis.connect("redis://localhost:6379")

# 带 TTL 的键值对
redis.set("session:123", token, ttl: 3600)
val = redis.get("session:123")

# 有序集合（排行榜）
redis.zadd("scores", player, score)
top10 = redis.zrange("scores", 0, 9, reverse: true, with_scores: true)

# Cache-Aside 辅助方法
result = redis.cache("user:42", ttl: 300, fn() {
    return db.query("SELECT * FROM users WHERE id=42", [])
})
```

> **需要：** Redis 服务器运行中（`redis-server` 或 Docker）。

---

### 07 · 图像处理（`image` 模块）

`image` 模块提供缩放、裁剪、水印、锐化和格式转换——纯 Go 实现，无需 ImageMagick。

| # | 文件 | 说明 |
|---|------|------|
| 33 | [33-image-resizer-service.cod](07-image/33-image-resizer-service.cod) | API：上传 → 缩放为 4 种标准尺寸 |
| 34 | [34-watermark-batch.cod](07-image/34-watermark-batch.cod) | 批量为目录中所有图片添加水印 |
| 35 | [35-image-pipeline.cod](07-image/35-image-pipeline.cod) | 缩放 → 锐化 → 水印 → 优化 |

**核心用法示例：**
```codong
img = image.load("photo.jpg")

# 缩放（保持宽高比）
thumb = img.resize(320, 240)
thumb.save("photo-thumb.jpg", quality: 85)

# 水印
img.watermark("logo.png", position: "bottom-right", opacity: 0.6)

# 流水线
image.load("input.jpg")
    .resize(1920, 1080)
    .sharpen(1.2)
    .watermark("brand.png")
    .save("output.jpg")
```

---

### 08 · OAuth 与认证（`oauth` 模块）

`oauth` 模块提供 JWT 签发/验证、OAuth2 授权流程和 RBAC（基于角色的访问控制）。

| # | 文件 | 说明 |
|---|------|------|
| 36 | [36-github-oauth-login.cod](08-oauth/36-github-oauth-login.cod) | 完整的 GitHub SSO 登录流程 |
| 37 | [37-rbac-permission-system.cod](08-oauth/37-rbac-permission-system.cod) | 带权限矩阵的角色访问控制 |

**核心用法示例：**
```codong
# JWT
token  = oauth.jwt.sign({user_id: 42, role: "admin"}, secret: SECRET, expires_in: 86400)
claims = oauth.jwt.verify(token, secret: SECRET)

# RBAC
oauth.rbac.define("admin",  ["read", "write", "delete"])
oauth.rbac.define("viewer", ["read"])
oauth.rbac.assign(user_id, "admin")
can = oauth.rbac.check(user_id, "delete")  # true / false

# 中间件
server.use("/admin", oauth.jwt.middleware(secret: SECRET))
```

> **需要：** 示例 36 需要 `GITHUB_CLIENT_ID` 和 `GITHUB_CLIENT_SECRET`。

---

### 09 · 算法

纯 Codong 实现的经典计算机科学算法，无需任何模块。

| # | 文件 | 说明 |
|---|------|------|
| 38 | [38-fibonacci-memoized.cod](09-algorithms/38-fibonacci-memoized.cod) | 朴素 vs 记忆化 vs 迭代 Fibonacci |
| 39 | [39-sorting-algorithms.cod](09-algorithms/39-sorting-algorithms.cod) | 冒泡排序、归并排序、快速排序 |
| 40 | [40-graph-traversal.cod](09-algorithms/40-graph-traversal.cod) | 邻接表上的 BFS + DFS 路径查找 |
| 41 | [41-binary-search-tree.cod](09-algorithms/41-binary-search-tree.cod) | BST 插入、查找、中序遍历 |
| 42 | [42-functional-patterns.cod](09-algorithms/42-functional-patterns.cod) | compose、pipe、curry、partial、group-by |

**核心用法示例：**
```codong
# 闭包实现记忆化
fn memoize(f) {
    cache = {}
    return fn(n) {
        if cache.has(str(n)) { return cache[str(n)] }
        result = f(n)
        cache[str(n)] = result
        return result
    }
}

# 函数组合
pipe = fn(...fns) {
    return fn(x) { fns.reduce(fn(v, f) { f(v) }, x) }
}
```

---

### 10 · 数据处理

端到端数据流水线：CSV 解析、JSON 重塑、ETL、数据验证、发布订阅、状态机，以及完整全栈应用。

| # | 文件 | 说明 |
|---|------|------|
| 43 | [43-csv-processor.cod](10-data-processing/43-csv-processor.cod) | 解析 CSV，聚合，导出过滤后的 JSON |
| 44 | [44-json-transformer.cod](10-data-processing/44-json-transformer.cod) | 重塑嵌套 API 响应、扁平化、合并 |
| 45 | [45-report-generator.cod](10-data-processing/45-report-generator.cod) | 从 SQLite 生成 JSON + HTML 销售报告 |
| 46 | [46-data-validator.cod](10-data-processing/46-data-validator.cod) | Schema 验证，含详细错误信息 |
| 47 | [47-event-system.cod](10-data-processing/47-event-system.cod) | 基于闭包的进程内发布订阅事件总线 |
| 48 | [48-state-machine.cod](10-data-processing/48-state-machine.cod) | 有限状态机：订单生命周期 |
| 49 | [49-pipeline-etl.cod](10-data-processing/49-pipeline-etl.cod) | ETL：API → 转换 → SQLite，含去重 |
| 50 | [50-full-stack-app.cod](10-data-processing/50-full-stack-app.cod) | **完整应用**：Todo API + JWT 认证 + Redis + 数据库 |

**示例 48 — 状态机流程图：**
```
订单生命周期：

  pending ──confirm──▶ confirmed ──ship──▶ shipped ──deliver──▶ delivered
（待处理）               （已确认）           （已发货）           （已送达）
     │                     │                  │
   cancel               cancel             return
     ▼                     ▼                  ▼
  cancelled           cancelled        return_requested ──approve──▶ returned
 （已取消）           （已取消）          （申请退货）                  （已退货）
```

**示例 50 — 全栈架构图：**
```
  客户端（curl / 浏览器）
       │
       ▼
  POST /auth/login ──▶ JWT token
       │
  GET  /todos  ──▶ redis.cache ──命中──▶ 响应
                        │
                       未命中
                        ▼
                   db.query（SQLite）
                        │
                        ▼
                   redis.set（写入缓存）
                        │
                        ▼
                      响应
```

---

## 第 51–100 个示例

### 11 · 命令行工具（`env`、`fs`、`db`）

| # | 文件 | 说明 |
|---|------|------|
| 51 | [51-todo-cli.cod](11-cli/51-todo-cli.cod) | CLI 待办事项管理器：添加/列表/完成/删除 |
| 52 | [52-file-search-cli.cod](11-cli/52-file-search-cli.cod) | 类 grep 递归文件内容搜索 |
| 53 | [53-json-lint-cli.cod](11-cli/53-json-lint-cli.cod) | JSON 验证器与格式化工具 |
| 54 | [54-env-doctor-cli.cod](11-cli/54-env-doctor-cli.cod) | 检查环境变量与服务是否就绪 |
| 55 | [55-word-count-cli.cod](11-cli/55-word-count-cli.cod) | 统计文件的行数、单词数、字符数 |

---

### 12 · 定时任务

| # | 文件 | 说明 |
|---|------|------|
| 56 | [56-daily-digest-cron.cod](12-cron/56-daily-digest-cron.cod) | 从数据库生成每日活动摘要 |
| 57 | [57-db-cleanup-cron.cod](12-cron/57-db-cleanup-cron.cod) | 删除过期/软删除记录 + VACUUM |
| 58 | [58-health-ping-cron.cod](12-cron/58-health-ping-cron.cod) | 心跳检测生产端点，失败时告警 |
| 59 | [59-cache-warmup-cron.cod](12-cron/59-cache-warmup-cron.cod) | 高峰前预热 Redis 缓存 |
| 60 | [60-metrics-snapshot-cron.cod](12-cron/60-metrics-snapshot-cron.cod) | 每小时指标快照，用于趋势分析 |

---

### 13 · WebSocket 实时通信

| # | 文件 | 说明 |
|---|------|------|
| 61 | [61-ws-chat-server.cod](13-websocket/61-ws-chat-server.cod) | 多房间群聊服务器 |
| 62 | [62-ws-live-ticker.cod](13-websocket/62-ws-live-ticker.cod) | 实时股价行情推送（1 秒间隔） |
| 63 | [63-ws-notifications.cod](13-websocket/63-ws-notifications.cod) | 推送通知，含离线消息队列 |
| 64 | [64-ws-collaborative-editor.cod](13-websocket/64-ws-collaborative-editor.cod) | 实时多人协作文本编辑器 |
| 65 | [65-ws-game-server.cod](13-websocket/65-ws-game-server.cod) | 多人共享画布游戏服务器 |

---

### 14 · 任务队列（`redis`）

| # | 文件 | 说明 |
|---|------|------|
| 66 | [66-job-queue.cod](14-queue/66-job-queue.cod) | Redis 任务队列 + Worker |
| 67 | [67-worker-pool.cod](14-queue/67-worker-pool.cod) | N 个并发 Worker 协程池 |
| 68 | [68-priority-queue.cod](14-queue/68-priority-queue.cod) | 基于有序集合的优先队列 |
| 69 | [69-dead-letter-queue.cod](14-queue/69-dead-letter-queue.cod) | 死信队列：重试 → 失败 → 重放 |
| 70 | [70-task-scheduler.cod](14-queue/70-task-scheduler.cod) | 持久化延迟任务调度器 |

---

### 15 · 密码学（`crypto`）

| # | 文件 | 说明 |
|---|------|------|
| 71 | [71-password-hashing.cod](15-crypto/71-password-hashing.cod) | bcrypt 哈希/验证 + 策略检查 + 迁移 |
| 72 | [72-aes-encrypt-decrypt.cod](15-crypto/72-aes-encrypt-decrypt.cod) | AES-256-GCM 字段级 + 信封加密 |
| 73 | [73-api-key-system.cod](15-crypto/73-api-key-system.cod) | 签发、验证、吊销 API Key |
| 74 | [74-hmac-webhook-security.cod](15-crypto/74-hmac-webhook-security.cod) | HMAC-SHA256 Webhook 签名与验证 |
| 75 | [75-token-vault.cod](15-crypto/75-token-vault.cod) | AES 加密的密钥保险库，支持主密钥轮换 |

---

### 16 · 爬虫与轮询

| # | 文件 | 说明 |
|---|------|------|
| 76 | [76-news-aggregator.cod](16-scraping/76-news-aggregator.cod) | 多源 RSS 聚合，含去重 |
| 77 | [77-price-monitor.cod](16-scraping/77-price-monitor.cod) | 监控商品价格，降价时告警 |
| 78 | [78-api-poller.cod](16-scraping/78-api-poller.cod) | API 轮询，存储快照，检测字段变化 |
| 79 | [79-sitemap-crawler.cod](16-scraping/79-sitemap-crawler.cod) | 爬取 Sitemap，检查状态码与响应速度 |
| 80 | [80-github-trending.cod](16-scraping/80-github-trending.cod) | 抓取 GitHub Trending，封装为 API |

---

### 17 · 数学与数据科学

| # | 文件 | 说明 |
|---|------|------|
| 81 | [81-statistics-lib.cod](17-math/81-statistics-lib.cod) | 均值、中位数、众数、标准差、百分位、相关系数 |
| 82 | [82-matrix-operations.cod](17-math/82-matrix-operations.cod) | 矩阵加法、乘法、转置、行列式 |
| 83 | [83-time-series.cod](17-math/83-time-series.cod) | SMA、EMA、趋势检测、异常检测 |
| 84 | [84-monte-carlo.cod](17-math/84-monte-carlo.cod) | π 估算、投资组合 VaR、生日问题 |
| 85 | [85-unit-converter.cod](17-math/85-unit-converter.cod) | 温度、距离、重量、数据大小转换 |

---

### 18 · 设计模式

| # | 文件 | 说明 |
|---|------|------|
| 86 | [86-observer-pattern.cod](18-patterns/86-observer-pattern.cod) | EventEmitter：on/once/off/emit |
| 87 | [87-strategy-pattern.cod](18-patterns/87-strategy-pattern.cod) | 可替换的排序与定价策略 |
| 88 | [88-decorator-pattern.cod](18-patterns/88-decorator-pattern.cod) | 日志、计时、重试、缓存、限流装饰器 |
| 89 | [89-command-pattern.cod](18-patterns/89-command-pattern.cod) | 文本编辑器，带完整撤销/重做栈 |
| 90 | [90-builder-pattern.cod](18-patterns/90-builder-pattern.cod) | SQL、HTTP 请求、邮件的流式构建器 |

---

### 19 · 测试

| # | 文件 | 说明 |
|---|------|------|
| 91 | [91-unit-test-runner.cod](19-testing/91-unit-test-runner.cod) | 轻量级 describe/it/expect 测试框架 |
| 92 | [92-mock-http-server.cod](19-testing/92-mock-http-server.cod) | 含调用记录的 Mock API 服务器 |
| 93 | [93-property-testing.cod](19-testing/93-property-testing.cod) | 基于生成器的属性验证 |
| 94 | [94-load-tester.cod](19-testing/94-load-tester.cod) | HTTP 压测，输出 p50/p95/p99 |
| 95 | [95-snapshot-testing.cod](19-testing/95-snapshot-testing.cod) | 快照捕获与差异比对，支持更新模式 |

---

### 20 · 邮件（`email`、`redis`、`db`）

| # | 文件 | 说明 |
|---|------|------|
| 96 | [96-send-email.cod](20-email/96-send-email.cod) | SMTP 发送：欢迎、重置密码、账单、批量 |
| 97 | [97-email-template-engine.cod](20-email/97-email-template-engine.cod) | HTML 邮件模板引擎，支持变量替换 |
| 98 | [98-email-digest.cod](20-email/98-email-digest.cod) | 从数据库生成周报发送给订阅者 |
| 99 | [99-bounce-handler.cod](20-email/99-bounce-handler.cod) | SendGrid/SES 退信与投诉 Webhook 处理 |
| 100 | [100-email-queue.cod](20-email/100-email-queue.cod) | Redis 邮件队列，含限速 + 重试 |

---

## 语言速查表

```codong
# 变量（无需类型声明）
name = "Codong"
count = 42
ratio = 3.14
active = true

# 字符串插值
print("你好，{name}！你有 {count} 条消息。")

# 函数
fn greet(name, greeting = "你好") {
    return "{greeting}，{name}！"
}

# 箭头函数
double = fn(x) { x * 2 }

# 列表
nums = [1, 2, 3, 4, 5]
evens = nums.filter(fn(n) { n % 2 == 0 })
doubled = nums.map(fn(n) { n * 2 })
total = nums.reduce(fn(acc, n) { acc + n }, 0)

# Map
user = {name: "Alice", age: 30}
keys = user.keys()
user.each(fn(k, v) { print("{k}: {v}") })

# 错误处理
result = risky_operation()
if result.is_err() {
    print("错误：{result.error()}")
}

# Match 匹配
match status {
    "ok"    => print("成功")
    "error" => print("失败")
    _       => print("未知")
}

# 幂运算符
area = side ** 2

# 类型转换
n = int("42")
f = float("3.14")
s = str(100)
```

---

## 运行要求

| 要求 | 涉及示例 |
|------|---------|
| Codong v0.1.3+ | 全部 |
| 网络访问 | 25–28、15–20 |
| Redis（`redis-server`） | 29–32、05、10 |
| `ANTHROPIC_API_KEY` | 15–20 |
| `OPENAI_API_KEY` | 20（可选） |
| `GITHUB_CLIENT_ID` + `GITHUB_CLIENT_SECRET` | 36 |

**安装 Codong：**
```bash
curl -fsSL https://codong.org/install.sh | sh
codong version  # → codong v0.1.3
```

**启动 Redis（Docker）：**
```bash
docker run -d -p 6379:6379 redis:alpine
```

---

## 运行示例

```bash
# 运行指定示例
codong run 01-web/01-hello-api.cod

# 带环境变量运行
ANTHROPIC_API_KEY=sk-... codong run 03-llm/15-simple-chat.cod

# 指定端口运行
PORT=9000 codong run 01-web/01-hello-api.cod
```

---

## 贡献

本 Cookbook 欢迎贡献。添加新示例的步骤：

1. Fork 本仓库
2. 在对应分类目录中创建新的 `.cod` 文件
3. 添加注释头：`# 说明` 和 `# codong run <文件名>.cod`
4. 保持自包含——一个文件，除已记录模块外无外部依赖
5. 提交 Pull Request

---

## 许可证

MIT —— 自由使用，自由修改，自由分享。

---

## 链接

- **Codong 官网**：https://codong.org
- **安装**：`curl -fsSL https://codong.org/install.sh | sh`
- **GitHub**：https://github.com/brettinhere/codong-cookbook
- **Issues**：https://github.com/brettinhere/codong-cookbook/issues
