# Competitive Benchmark Results

**Generated:** 2026-10-12T14:27:48+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 41,313 | 18,415 | 55,294 🏆 | 26,553 | 28,585 | 42,182 |
| json | 91,969 🏆 | 39,226 | 91,652 | 54,043 | 47,567 | 81,306 |
| path_param | 89,094 | 27,335 | 90,360 🏆 | 47,470 | 47,719 | 75,562 |
| plaintext | 99,867 🏆 | 38,040 | 98,134 | 56,599 | 53,545 | 85,525 |
| query_params | 65,939 | 24,182 | 70,435 🏆 | 44,274 | 37,038 | 60,688 |
| routing_stress | 92,256 | 17,444 | 93,762 🏆 | 54,412 | 35,924 | 26,379 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 1.91 | 16.36 | 1.49 🏆 | 3.70 | 13.81 | 5.15 |
| json | 1.14 | 1.94 | 1.20 | 1.40 | 2.12 | 1.03 🏆 |
| path_param | 1.09 | 2.80 | 1.03 🏆 | 1.61 | 2.67 | 1.12 |
| plaintext | 1.16 🏆 | 1.98 | 1.56 | 1.34 | 2.42 | 1.45 |
| query_params | 1.27 | 3.67 | 1.21 🏆 | 1.73 | 2.73 | 1.26 |
| routing_stress | 1.04 🏆 | 4.60 | 1.18 | 1.43 | 12.45 | 3.09 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 55,294 | 1.16 | 1.15 | 1.30 | 1.49 | 0 |
| starlette | 42,182 | 1.56 | 1.49 | 1.74 | 5.15 | 0 |
| blacksheep | 41,313 | 1.55 | 1.54 | 1.73 | 1.91 | 0 |
| sanic | 28,585 | 2.46 | 2.06 | 3.11 | 13.81 | 0 |
| litestar | 26,553 | 2.47 | 2.35 | 2.75 | 3.70 | 0 |
| fastapi | 18,415 | 3.69 | 3.31 | 3.95 | 16.36 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| blacksheep | 91,969 | 0.69 | 0.68 | 0.79 | 1.14 | 0 |
| hawkapi | 91,652 | 0.70 | 0.68 | 0.79 | 1.20 | 0 |
| starlette | 81,306 | 0.78 | 0.78 | 0.88 | 1.03 | 0 |
| litestar | 54,043 | 1.18 | 1.18 | 1.29 | 1.40 | 0 |
| sanic | 47,567 | 1.38 | 1.35 | 1.52 | 2.12 | 0 |
| fastapi | 39,226 | 1.63 | 1.63 | 1.79 | 1.94 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 90,360 | 0.70 | 0.70 | 0.80 | 1.03 | 0 |
| blacksheep | 89,094 | 0.72 | 0.71 | 0.81 | 1.09 | 0 |
| starlette | 75,562 | 0.84 | 0.84 | 0.94 | 1.12 | 0 |
| sanic | 47,719 | 1.39 | 1.35 | 1.51 | 2.67 | 0 |
| litestar | 47,470 | 1.34 | 1.34 | 1.48 | 1.61 | 0 |
| fastapi | 27,335 | 2.33 | 2.37 | 2.52 | 2.80 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| blacksheep | 99,867 | 0.63 | 0.63 | 0.72 | 1.16 | 0 |
| hawkapi | 98,134 | 0.65 | 0.64 | 0.73 | 1.56 | 0 |
| starlette | 85,525 | 0.75 | 0.73 | 0.85 | 1.45 | 0 |
| litestar | 56,599 | 1.12 | 1.13 | 1.23 | 1.34 | 0 |
| sanic | 53,545 | 1.24 | 1.20 | 1.37 | 2.42 | 0 |
| fastapi | 38,040 | 1.67 | 1.69 | 1.85 | 1.98 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 70,435 | 0.90 | 0.90 | 1.00 | 1.21 | 0 |
| blacksheep | 65,939 | 0.97 | 0.96 | 1.07 | 1.27 | 0 |
| starlette | 60,688 | 1.05 | 1.05 | 1.15 | 1.26 | 0 |
| litestar | 44,274 | 1.44 | 1.44 | 1.59 | 1.73 | 0 |
| sanic | 37,038 | 1.76 | 1.72 | 1.93 | 2.73 | 0 |
| fastapi | 24,182 | 2.63 | 2.35 | 3.50 | 3.67 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 93,762 | 0.68 | 0.67 | 0.77 | 1.18 | 0 |
| blacksheep | 92,256 | 0.69 | 0.69 | 0.78 | 1.04 | 0 |
| litestar | 54,412 | 1.17 | 1.17 | 1.28 | 1.43 | 0 |
| sanic | 35,924 | 2.00 | 1.66 | 2.41 | 12.45 | 0 |
| starlette | 26,379 | 2.41 | 2.40 | 2.90 | 3.09 | 0 |
| fastapi | 17,444 | 3.67 | 3.81 | 4.41 | 4.60 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #2
- path_param: #1
- plaintext: #2
- query_params: #1
- routing_stress: #1
