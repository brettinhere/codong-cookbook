# Codong Cookbook

> **50 real-world programs** — every module, every pattern, every feature of the [Codong](https://codong.org) language in one open-source collection.

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

This repository contains **50 standalone `.cod` programs** organized into 10 topic areas. Each file:

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
└── 10-data-processing/        # CSV, JSON, reports, validation, ETL, full-stack
    ├── 43-csv-processor.cod
    ├── 44-json-transformer.cod
    ├── 45-report-generator.cod
    ├── 46-data-validator.cod
    ├── 47-event-system.cod
    ├── 48-state-machine.cod
    ├── 49-pipeline-etl.cod
    └── 50-full-stack-app.cod
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
