# Competitive Benchmark Results

**Generated:** 2026-09-07T11:37:21+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 12,092 | 6,946 | 19,913 🏆 | 8,782 | 10,902 | 16,500 |
| json | 30,985 | 11,741 | 34,218 🏆 | 14,037 | 12,502 | 27,153 |
| path_param | 28,524 | 9,955 | 31,873 🏆 | 12,648 | 12,720 | 23,354 |
| plaintext | 43,799 | 11,684 | 53,414 🏆 | 14,220 | 13,682 | 33,419 |
| query_params | 16,705 | 8,915 | 19,516 🏆 | 12,356 | 10,156 | 15,755 |
| routing_stress | 30,305 | 7,040 | 33,921 🏆 | 14,024 | 13,609 | 9,226 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 6.72 | 14.05 | 4.08 🏆 | 9.85 | 13.94 | 5.57 |
| json | 2.50 🏆 | 6.47 | 2.87 | 5.36 | 6.21 | 2.89 |
| path_param | 2.80 | 8.51 | 2.51 🏆 | 6.00 | 6.06 | 3.38 |
| plaintext | 1.95 | 6.43 | 1.86 🏆 | 5.15 | 5.57 | 2.70 |
| query_params | 4.49 | 9.69 | 3.90 🏆 | 6.18 | 7.34 | 4.65 |
| routing_stress | 2.70 | 11.76 | 2.35 🏆 | 5.30 | 11.24 | 8.51 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 19,913 | 3.19 | 3.17 | 3.71 | 4.08 | 0 |
| starlette | 16,500 | 3.89 | 3.75 | 4.68 | 5.57 | 0 |
| blacksheep | 12,092 | 5.26 | 5.06 | 6.28 | 6.72 | 0 |
| sanic | 10,902 | 5.94 | 5.39 | 7.65 | 13.94 | 0 |
| litestar | 8,782 | 7.24 | 6.86 | 8.93 | 9.85 | 0 |
| fastapi | 6,946 | 9.24 | 8.78 | 11.25 | 14.05 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 34,218 | 1.85 | 1.84 | 2.10 | 2.87 | 0 |
| blacksheep | 30,985 | 2.06 | 2.08 | 2.31 | 2.50 | 0 |
| starlette | 27,153 | 2.35 | 2.37 | 2.69 | 2.89 | 0 |
| litestar | 14,037 | 4.55 | 4.73 | 5.13 | 5.36 | 0 |
| sanic | 12,502 | 5.13 | 5.22 | 5.90 | 6.21 | 0 |
| fastapi | 11,741 | 5.44 | 5.63 | 6.26 | 6.47 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 31,873 | 2.00 | 2.02 | 2.29 | 2.51 | 0 |
| blacksheep | 28,524 | 2.22 | 2.23 | 2.58 | 2.80 | 0 |
| starlette | 23,354 | 2.74 | 2.76 | 3.14 | 3.38 | 0 |
| sanic | 12,720 | 5.03 | 5.11 | 5.76 | 6.06 | 0 |
| litestar | 12,648 | 5.06 | 5.29 | 5.80 | 6.00 | 0 |
| fastapi | 9,955 | 6.42 | 6.12 | 8.29 | 8.51 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 53,414 | 1.19 | 1.18 | 1.40 | 1.86 | 0 |
| blacksheep | 43,799 | 1.45 | 1.48 | 1.69 | 1.95 | 0 |
| starlette | 33,419 | 1.90 | 1.92 | 2.19 | 2.70 | 0 |
| litestar | 14,220 | 4.50 | 4.70 | 4.96 | 5.15 | 0 |
| sanic | 13,682 | 4.67 | 4.70 | 5.28 | 5.57 | 0 |
| fastapi | 11,684 | 5.47 | 5.62 | 6.23 | 6.43 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 19,516 | 3.27 | 3.38 | 3.70 | 3.90 | 0 |
| blacksheep | 16,705 | 3.83 | 3.98 | 4.26 | 4.49 | 0 |
| starlette | 15,755 | 4.03 | 4.21 | 4.46 | 4.65 | 0 |
| litestar | 12,356 | 5.17 | 5.16 | 5.98 | 6.18 | 0 |
| sanic | 10,156 | 6.30 | 6.50 | 7.05 | 7.34 | 0 |
| fastapi | 8,915 | 7.17 | 6.71 | 9.50 | 9.69 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 33,921 | 1.87 | 1.89 | 2.13 | 2.35 | 0 |
| blacksheep | 30,305 | 2.11 | 2.12 | 2.43 | 2.70 | 0 |
| litestar | 14,024 | 4.53 | 4.82 | 5.12 | 5.30 | 0 |
| sanic | 13,609 | 4.76 | 4.36 | 6.25 | 11.24 | 0 |
| starlette | 9,226 | 6.93 | 6.92 | 8.35 | 8.51 | 0 |
| fastapi | 7,040 | 9.08 | 9.40 | 11.51 | 11.76 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #1
- path_param: #1
- plaintext: #1
- query_params: #1
- routing_stress: #1
