# Changelog

The format is loosely based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). Versions follow SemVer.

## [Unreleased]

## [0.1.7] - 2026-05-16

Static-response cache. Plaintext throughput jumped from #2 to #1 in the competitive suite, and we lead all six scenarios on both throughput and p99 latency now.

### Performance

- Static-response cache. Handlers that just `return PlainTextResponse("Hello, World!")` (or `JSONResponse(...)` / `HTMLResponse(...)` / `Response(...)` with literal args, no params) get their two ASGI messages built once at registration via AST inspection. Dispatch is one branch + two awaits. Local micro-bench: 0.89 µs/req, 1.1M req/s on raw ASGI. Other handlers fall through unchanged.

### Docs

- README leads with "Why HawkAPI" (Performance / Production rigor / Unique features). Added a p99-latency table — we win every scenario there too.

## [0.1.6] - 2026-05-16

Security audit. Five SAST/dep/secrets scanners added to CI. Three HIGH findings fixed.

### Security

- `get_flags` no longer reads identity from `X-User-Id` / `X-Tenant-Id` headers (CWE-290). Identity must come from an authenticated dependency. Raw headers still on `ctx.headers` for non-identity rules.
- GraphQL `GET` rejects mutations and subscriptions for every operation in the document, not just the first token (CWE-352).
- GraphQL endpoints now have `max_depth=15` and `timeout_s=30.0` defaults; `make_graphql_handler` wraps the executor in `asyncio.wait_for` (CWE-770).
- `mount_graphql` ships `graphiql=False` by default (CWE-200). Opt in for dev environments.
- `mount_grpc` adds `maximum_concurrent_rpcs=1000` default. Pass `None` to opt out.
- `doctor` DOC050 explicit-scheme-checks its hard-coded PyPI URL; clean under bandit B310 and semgrep.

### Added

- `SECURITY.md`, `docs/security/threat-model.md` (STRIDE per subsystem), `docs/security/owasp-api-top10-2023.md`, `docs/security/code-review-2026-05-16.md`.
- `.github/workflows/security.yml` runs Bandit + Semgrep + pip-audit + Gitleaks + CodeQL on every push, PR, and weekly.
- `.github/dependabot.yml` for weekly pip + actions updates.

## [0.1.5] - 2026-04-19

Fixes from the full code review.

### Fixed

- Static-response handler returning `StreamingResponse` / `FileResponse` could run twice through the trivial fast-path fallback. `_compute_trivial` now excludes streaming-return handlers at registration; the fast path also guards in-place.
- Typed path params (`{id:int}` etc.) were not coerced on the trivial fast-path. Now they are.
- GraphiQL HTML pins exact versions (`graphiql@3.0.9`, `react@18.3.1`, `react-dom@18.3.1`) and adds SRI `integrity=` hashes on every script/stylesheet.
- `FileFlagProvider` now writes `_cache` before `_mtime` so concurrent readers can't observe a new mtime with a stale cache.
- Hoist `ParamSource` / `_coerce_fast` imports out of `_execute_trivial_route` — small per-request win.

### Added

- `hawkapi doctor --offline` skips rules that hit the network (DOC050 PyPI version check). Rules opt in via `requires_network = True`.
- README note: use `secrets.compare_digest` to compare credentials from `HTTPBasic` / `HTTPBearer`.

### Changed

- `build_mypyc.py` documents the MSVC `__is_trivial` / `__has_*` trait trap so future private attributes avoid the C++11 keyword collisions.
- ruff config excludes local venvs, build artefacts, and non-library code (`benchmarks/`, `examples/`, `hatch_build.py`).

## [0.1.4] - 2026-04-19

Wave 3 perf, `hawkapi doctor` CLI, badge + logo for downstream projects.

### Added

- `hawkapi doctor <APP_SPEC>` — 18-rule health check across security / observability / performance / correctness / deps. Human or JSON output, `--severity` filter, exit 0/1/2.
- `docs/assets/hawk-icon.svg` + "Using HawkAPI?" README section with a dynamic PyPI-version badge and copy-paste snippets.

### Changed

- Trivial-route fast path. Routes with no DI, deps, permissions, background tasks, response model, deprecation, or per-route middleware skip all bookkeeping and call the handler directly. Eligibility computed once at registration. Targeted at plaintext throughput.
- `hawkapi dev` installs `uvloop.EventLoopPolicy()` when available; `--no-uvloop` to opt out.
- Added `routing/router.py` and `di/resolver.py` to mypyc `HOT_MODULES`. `app.py` and `requests/request.py` stay interpreted (user subclassing).

## [0.1.3] - 2026-04-19

Tier 2 (Bulkhead / Feature flags / GraphQL / gRPC), Tier 3 (OpenAPI codegen, typed routes), DX parity with FastAPI.

### Added

- `app.mount_grpc(servicer, add_to_server=..., port=50051)` — thin gRPC over `grpc.aio` with ASGI lifespan, built-in observability interceptor, reflection toggle, TLS passthrough, port-merge. Zero default deps (`grpcio` lazy).
- `app.mount_graphql(path, executor=...)` — POST + GET wire protocol, GraphiQL UI, `context_factory`, and `from_graphql_core` / `from_strawberry` adapters (lazy).
- Feature flags: `FlagProvider` Protocol, Static / Env / File providers (File with mtime hot-reload, JSON+TOML+YAML), `Flags` facade, `Depends(get_flags)`, `@requires_flag`, `on_flag_evaluated` plugin hook.
- `hawkapi gen-client` — zero-dep TypeScript and Python client SDKs from OpenAPI 3.1.
- `response_model` auto-inferred from the handler's return annotation (msgspec, Pydantic, generics, Optionals). Explicit `response_model=` still wins.
- `hawkapi migrate` — FastAPI → HawkAPI codemod via AST rewriting.
- Bulkhead primitive (`@bulkhead(name, limit=...)`) with Local and Redis backends; opt-in Prometheus metrics.
- `hawkapi.status` — HTTP + WebSocket status constants (FastAPI parity).
- Route- and router-level `dependencies=[Depends(...)]` for side-effect deps.
- `Security(dep, scopes=[...])` + `SecurityScopes` + OpenAPI `operation.security` reflection.
- `response_model_exclude_none` / `_unset` / `_defaults` flags on routes.
- Free-threaded Python 3.13 wheels (`cp313t-cp313t`) via cibuildwheel; `hawkapi._threading` helpers for PEP 703.
- Performance regression gate (5% mean threshold) and pytest-memray memory budget tests in CI.
- Distributed Redis-backed circuit breaker and adaptive concurrency limiter.
- HTTP/2 deployment guide.
- Competitive benchmark CI: weekly cron + release trigger, auto-PR with refreshed `RESULTS.md`.

## [0.1.2] - 2026-04-05

### Added

- CSRF (double-submit cookie), Session (signed cookie), Redis rate limiter.
- Per-route middleware: `@app.get("/x", middleware=[...])`.
- Streaming request body (`request.stream()`).
- MessagePack content negotiation.
- W3C Trace Context propagation.
- Plugin hooks: `on_startup`, `on_shutdown`, `on_exception`, `on_middleware_added`.
- `hawkapi init` CLI.
- TestClient cookie jar, `CaseInsensitiveDict` headers, `is_success` / `is_redirect` / `raise_for_status` helpers.

### Fixed

- Multipart `rstrip` corrupting binary uploads.
- `StreamingResponse` not sending terminal ASGI chunk on error.
- CRLF injection in `RedirectResponse`.
- Radix tree silent param name / type conflicts.
- Circuit breaker holding `asyncio.Lock` during I/O.
- `X-Forwarded-For` IP spoofing (now uses rightmost non-trusted).
- HEAD responses preserving correct `Content-Length`.
- Generator dependency cleanup distinguishes success / error.
- Duplicate `Content-Length` from middleware `after_response`.
- GZip double-compression of already-encoded responses.
- `FileResponse` `more_body` flag on exact chunk boundaries.
- DI `Provider` `asyncio.Lock` created lazily.
- `Settings._coerce` crash on `Optional[T]`.
- WebSocket send methods check connection state.
- Cookie parser strips RFC 6265 quoted values.
- ~40 more bug fixes.

### Changed

- `app.py` split into `_docs.py` / `_health.py` / `_execute_route()`.
- Controllers instantiated per request (was shared singleton).
- Middleware stack uses `MiddlewareEntry` dataclass.

## [0.1.1] - 2026-03-04

### Added

- Middleware: `Prometheus`, `StructuredLogging` (structlog), `CircuitBreaker` (closed → open → half-open), `TrustedProxy`, `RequestLimits`, `Debug`.
- `/readyz` + `/livez` health probes.
- Deprecation headers: `Deprecation`, `Sunset`, `Link`.
- Pagination: `Page[T]`, `CursorPage[T]`, `PaginationParams`, `CursorParams`.
- OpenAPI `example` on `Query`, `Path`, `Header`, `Body`, `Cookie`.
- CLI: `hawkapi new`, `hawkapi check`, `hawkapi changelog`, `hawkapi diff`.
- DI container introspection (JSON + Mermaid graph).
- Plugin API: route registration + schema generation hooks.
- TypeScript / Python client SDK templates.
- Docker template + deployment guide; FastAPI migration guide.
- E2E benchmark suite + GitHub Action.
- PyPI trusted publishing workflow.

### Fixed

- Singleton provider race: eager lock + `_UNSET` sentinel for `None` caching.
- `StreamingResponse` only sends terminal frame on successful completion.
- `CircuitBreakerMiddleware` state transitions under `asyncio.Lock`.
- `ObservabilityMiddleware` records via `try/finally`.
- WebSocket 404: consume `websocket.connect` before close frame (ASGI protocol).
- `HTTPBearer` / `HTTPBasic` / `OAuth2PasswordBearer` return `WWW-Authenticate` on 401.
- Empty bearer / OAuth2 tokens rejected.
- `BackgroundTasks` handles `functools.partial` via `getattr(func, "__name__", repr(func))`.
- `Page` division by zero on `size <= 0`.
- `detect_breaking_changes` keys parameters by `(name, in)` and resolves `$ref` in responses.
- `TrustedProxyMiddleware` validates IPs via `ipaddress.ip_address()`.
- `JSONResponse` dedupes `Content-Type` when caller sets one.
- Radix tree `find_allowed_methods` path normalization matches `lookup()`.
- OpenAPI schema shallow-copies operation dict for multi-method routes.

### Docs

- Middleware guide: `before_request` / `after_response` hooks (was `handle(call_next)`).
- Middleware table: 6 → 15 entries.
- `StreamingResponse`: `media_type` → `content_type`.
- Removed phantom `shutdown_drain_timeout`, `Settings.Config`.
- `metrics` and `logging` extras documented.
- README fixes: `credentials.credentials`, pagination ctor, cursor param.

## [0.1.0] - 2026-03-03

Initial release.

### Added

- ASGI 3.0 core, custom middleware pipeline.
- Radix tree router with typed path params (`int` / `str` / `float` / `uuid`).
- Responses: JSON, HTML, PlainText, Redirect, Streaming, File, SSE.
- DI container: singleton / scoped / transient lifecycles, generator deps with `yield`, nested `Depends()` cleanup.
- `response_model` filtering.
- OpenAPI 3.1 auto-gen + Swagger UI, ReDoc, Scalar.
- Middleware: CORS, GZip, Timing, TrustedHost, SecurityHeaders, RequestID, HTTPSRedirect, RateLimit, ErrorHandler.
- Security schemes: API Key (header/query/cookie), HTTPBearer, HTTPBasic, OAuth2PasswordBearer.
- WebSocket with async iteration + DI.
- Class-based controllers.
- Router with prefix, tags, mounts.
- `Settings` with env binding and profiles.
- `TestClient` (sync, pytest-friendly), scoped DI overrides.
- `BackgroundTasks`, `StaticFiles` (with path traversal protection, ETag, 304).
- `HTTPException` with RFC 9457 Problem Details.
- Request body size limits.
- `hawkapi dev` CLI (uvicorn auto-reload).
- Sync handler support via threadpool.
- API versioning (`VersionRouter`, per-version OpenAPI).
- Breaking-changes detector (`detect_breaking_changes()`).
- RBAC via `PermissionPolicy` + `permissions=` on routes/WS.
- `ObservabilityMiddleware` with structured logs + traces + metrics.
- Cold-start optimizations: lazy imports, `serverless=True`.
- Health endpoint (`/healthz`), request timeout, graceful shutdown.
- `py.typed`, pyright-strict clean, MkDocs site.

[0.1.7]: https://github.com/ashimov/HawkAPI/compare/v0.1.6...v0.1.7
[0.1.6]: https://github.com/ashimov/HawkAPI/compare/v0.1.5...v0.1.6
[0.1.5]: https://github.com/ashimov/HawkAPI/compare/v0.1.4...v0.1.5
[0.1.4]: https://github.com/ashimov/HawkAPI/compare/v0.1.3...v0.1.4
[0.1.3]: https://github.com/ashimov/HawkAPI/compare/v0.1.2...v0.1.3
[0.1.2]: https://github.com/ashimov/HawkAPI/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/ashimov/HawkAPI/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/ashimov/HawkAPI/releases/tag/v0.1.0
