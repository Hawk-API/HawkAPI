# Competitive Benchmark Results

**Generated:** 2026-10-26T12:19:04+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 39,813 | 18,377 | 55,085 🏆 | 26,226 | 25,374 | 41,226 |
| json | 88,919 | 39,741 | 92,348 🏆 | 51,752 | 45,678 | 76,044 |
| path_param | 83,725 | 27,059 | 89,707 🏆 | 44,118 | 45,183 | 72,383 |
| plaintext | 95,394 | 37,146 | 100,325 🏆 | 54,874 | 49,586 | 83,625 |
| query_params | 64,231 | 24,618 | 72,833 🏆 | 41,929 | 35,630 | 58,009 |
| routing_stress | 86,401 | 17,759 | 94,548 🏆 | 51,865 | 33,691 | 25,753 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 2.00 | 19.48 | 1.52 🏆 | 3.23 | 16.11 | 5.71 |
| json | 1.00 🏆 | 1.96 | 1.38 | 1.52 | 3.31 | 1.15 |
| path_param | 1.37 | 2.73 | 1.38 | 1.72 | 2.71 | 1.11 🏆 |
| plaintext | 1.32 | 2.02 | 1.09 | 1.39 | 2.50 | 0.99 🏆 |
| query_params | 1.19 | 3.78 | 1.07 🏆 | 1.79 | 3.68 | 1.31 |
| routing_stress | 1.16 | 4.52 | 1.14 🏆 | 1.48 | 12.83 | 3.21 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 55,085 | 1.16 | 1.16 | 1.30 | 1.52 | 0 |
| starlette | 41,226 | 1.61 | 1.52 | 1.79 | 5.71 | 0 |
| blacksheep | 39,813 | 1.61 | 1.60 | 1.79 | 2.00 | 0 |
| litestar | 26,226 | 2.47 | 2.37 | 2.81 | 3.23 | 0 |
| sanic | 25,374 | 2.81 | 2.27 | 3.87 | 16.11 | 0 |
| fastapi | 18,377 | 3.78 | 3.29 | 3.98 | 19.48 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 92,348 | 0.69 | 0.67 | 0.79 | 1.38 | 0 |
| blacksheep | 88,919 | 0.72 | 0.71 | 0.81 | 1.00 | 0 |
| starlette | 76,044 | 0.84 | 0.84 | 0.94 | 1.15 | 0 |
| litestar | 51,752 | 1.24 | 1.23 | 1.36 | 1.52 | 0 |
| sanic | 45,678 | 1.46 | 1.40 | 1.58 | 3.31 | 0 |
| fastapi | 39,741 | 1.60 | 1.61 | 1.75 | 1.96 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 89,707 | 0.71 | 0.70 | 0.80 | 1.38 | 0 |
| blacksheep | 83,725 | 0.76 | 0.75 | 0.86 | 1.37 | 0 |
| starlette | 72,383 | 0.88 | 0.88 | 0.98 | 1.11 | 0 |
| sanic | 45,183 | 1.46 | 1.42 | 1.60 | 2.71 | 0 |
| litestar | 44,118 | 1.45 | 1.45 | 1.59 | 1.72 | 0 |
| fastapi | 27,059 | 2.36 | 2.38 | 2.58 | 2.73 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 100,325 | 0.63 | 0.63 | 0.71 | 1.09 | 0 |
| blacksheep | 95,394 | 0.67 | 0.66 | 0.75 | 1.32 | 0 |
| starlette | 83,625 | 0.76 | 0.76 | 0.86 | 0.99 | 0 |
| litestar | 54,874 | 1.16 | 1.16 | 1.27 | 1.39 | 0 |
| sanic | 49,586 | 1.34 | 1.29 | 1.48 | 2.50 | 0 |
| fastapi | 37,146 | 1.71 | 1.73 | 1.88 | 2.02 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 72,833 | 0.88 | 0.88 | 0.97 | 1.07 | 0 |
| blacksheep | 64,231 | 0.99 | 0.99 | 1.09 | 1.19 | 0 |
| starlette | 58,009 | 1.10 | 1.10 | 1.21 | 1.31 | 0 |
| litestar | 41,929 | 1.52 | 1.53 | 1.67 | 1.79 | 0 |
| sanic | 35,630 | 1.84 | 1.78 | 2.00 | 3.68 | 0 |
| fastapi | 24,618 | 2.59 | 2.29 | 3.42 | 3.78 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 94,548 | 0.67 | 0.66 | 0.76 | 1.14 | 0 |
| blacksheep | 86,401 | 0.74 | 0.73 | 0.84 | 1.16 | 0 |
| litestar | 51,865 | 1.22 | 1.23 | 1.35 | 1.48 | 0 |
| sanic | 33,691 | 2.11 | 1.76 | 2.52 | 12.83 | 0 |
| starlette | 25,753 | 2.47 | 2.38 | 3.03 | 3.21 | 0 |
| fastapi | 17,759 | 3.60 | 3.71 | 4.29 | 4.52 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #1
- path_param: #1
- plaintext: #1
- query_params: #1
- routing_stress: #1
