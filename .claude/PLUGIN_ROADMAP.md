# HawkAPI plugin roadmap

Saved 2026-05-16. 12 plugins shipped: `hawkapi`, `hawkapi-sentry`, `hawkapi-otel`, `hawkapi-cache`, `hawkapi-mcp`, `hawkapi-auth`, `hawkapi-mail`, `hawkapi-sqlalchemy`, `hawkapi-celery`, `hawkapi-websockets`, `hawkapi-storage`, `hawkapi-admin`.

## Backlog

### Security / prod-infra
- `hawkapi-ratelimit` — token bucket + sliding window, Redis backend
- `hawkapi-csrf` — CSRF for form-flows (pairs with admin)
- `hawkapi-monitoring` — Prometheus metrics endpoint (separate from OTel)

### API ergonomics
- `hawkapi-pagination` — cursor + offset, `Page[T]` helper
- `hawkapi-i18n` — gettext + Accept-Language + lazy strings
- `hawkapi-sse` — Server-Sent Events (separate from websockets)

### Infrastructure integrations
- `hawkapi-redis` — generic Redis client with DI + healthcheck
- `hawkapi-mongo` — Motor wrapper + sessions in DI
- `hawkapi-clickhouse` — async ClickHouse client
- `hawkapi-kafka` — aiokafka consumer/producer DI
- `hawkapi-search` — Meilisearch / Typesense / Elasticsearch abstraction

### Service patterns
- `hawkapi-webhook` — outbound webhooks (retry, HMAC signing, dead-letter)
- `hawkapi-cron` — simple in-process scheduler (no Celery dep)
- `hawkapi-events` — outbox pattern + domain event bus
- `hawkapi-cli` — manage.py-style CLI (db migrate / reset, shell, run jobs)

### Payments / billing
- `hawkapi-payments` — Stripe + PayPal wrappers with webhook handling

## Top-3 to ship next

`hawkapi-ratelimit`, `hawkapi-cron`, `hawkapi-pagination` — highest-leverage gaps for any production API.

## Per-plugin checklist (locked in from prior sessions)

- Author identity: `Berik Ashimov <bash@Beriks-MacBook-Pro.local>`, no Co-Authored-By
- ZERO mentions of Claude / Anthropic / OpenAI / assistant anywhere — grep before push
- Module-level singleton registry (TestClient does not set `scope["app"]`)
- `pyright` strict + `reportUnknown* = false`; relax `reportGeneralTypeIssues` for SDK-heavy code
- `ruff` ignore list: `S101, S110, B008, SIM105, SIM108, SIM113`
- Release workflow first run always fails (PyPI trusted publisher not yet configured); rerun + clean failed deployment after user confirms setup
