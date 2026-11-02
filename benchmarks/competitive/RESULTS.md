# Competitive Benchmark Results

**Generated:** 2026-11-02T14:48:31+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 11,753 | 7,320 | 17,208 🏆 | 8,768 | 9,869 | 14,764 |
| json | 29,253 | 12,533 | 32,620 🏆 | 14,214 | 12,465 | 25,115 |
| path_param | 26,448 | 11,498 | 29,955 🏆 | 12,648 | 12,334 | 21,186 |
| plaintext | 40,147 | 12,590 | 52,250 🏆 | 14,790 | 14,179 | 31,119 |
| query_params | 16,085 | 9,011 | 17,231 🏆 | 12,080 | 12,076 | 16,257 |
| routing_stress | 28,186 | 6,663 | 31,949 🏆 | 14,720 | 12,359 | 11,925 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 7.52 | 12.95 | 4.71 🏆 | 9.82 | 13.48 | 5.90 |
| json | 2.58 | 6.73 | 2.47 🏆 | 5.83 | 6.68 | 3.08 |
| path_param | 2.94 | 8.26 | 2.60 🏆 | 6.66 | 6.70 | 3.65 |
| plaintext | 2.09 🏆 | 6.83 | 2.13 | 5.45 | 5.85 | 2.46 |
| query_params | 4.90 | 9.66 | 4.39 🏆 | 6.83 | 7.72 | 4.76 |
| routing_stress | 2.74 | 11.75 | 2.38 🏆 | 5.83 | 10.47 | 7.93 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 17,208 | 3.72 | 3.67 | 4.36 | 4.71 | 0 |
| starlette | 14,764 | 4.34 | 4.16 | 5.24 | 5.90 | 0 |
| blacksheep | 11,753 | 5.44 | 5.08 | 6.96 | 7.52 | 0 |
| sanic | 9,869 | 6.54 | 6.01 | 7.94 | 13.48 | 0 |
| litestar | 8,768 | 7.31 | 6.97 | 9.06 | 9.82 | 0 |
| fastapi | 7,320 | 8.77 | 8.02 | 11.31 | 12.95 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 32,620 | 1.94 | 1.98 | 2.21 | 2.47 | 0 |
| blacksheep | 29,253 | 2.18 | 2.20 | 2.41 | 2.58 | 0 |
| starlette | 25,115 | 2.55 | 2.56 | 2.90 | 3.08 | 0 |
| litestar | 14,214 | 4.50 | 4.31 | 5.58 | 5.83 | 0 |
| fastapi | 12,533 | 5.07 | 4.88 | 6.47 | 6.73 | 0 |
| sanic | 12,465 | 5.13 | 4.99 | 6.26 | 6.68 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 29,955 | 2.12 | 2.15 | 2.40 | 2.60 | 0 |
| blacksheep | 26,448 | 2.40 | 2.43 | 2.72 | 2.94 | 0 |
| starlette | 21,186 | 3.00 | 3.13 | 3.46 | 3.65 | 0 |
| litestar | 12,648 | 5.06 | 4.89 | 6.36 | 6.66 | 0 |
| sanic | 12,334 | 5.19 | 5.03 | 6.36 | 6.70 | 0 |
| fastapi | 11,498 | 5.56 | 4.86 | 7.93 | 8.26 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 52,250 | 1.22 | 1.19 | 1.45 | 2.13 | 0 |
| blacksheep | 40,147 | 1.59 | 1.62 | 1.82 | 2.09 | 0 |
| starlette | 31,119 | 2.05 | 2.07 | 2.28 | 2.46 | 0 |
| litestar | 14,790 | 4.32 | 4.17 | 5.20 | 5.45 | 0 |
| sanic | 14,179 | 4.52 | 4.39 | 5.47 | 5.85 | 0 |
| fastapi | 12,590 | 5.08 | 4.78 | 6.60 | 6.83 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 17,231 | 3.71 | 3.95 | 4.21 | 4.39 | 0 |
| starlette | 16,257 | 3.91 | 3.89 | 4.57 | 4.76 | 0 |
| blacksheep | 16,085 | 3.97 | 4.21 | 4.65 | 4.90 | 0 |
| litestar | 12,080 | 5.27 | 5.14 | 6.58 | 6.83 | 0 |
| sanic | 12,076 | 5.30 | 4.89 | 7.23 | 7.72 | 0 |
| fastapi | 9,011 | 7.05 | 6.44 | 9.34 | 9.66 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 31,949 | 1.99 | 2.02 | 2.22 | 2.38 | 0 |
| blacksheep | 28,186 | 2.26 | 2.28 | 2.54 | 2.74 | 0 |
| litestar | 14,720 | 4.34 | 4.21 | 5.34 | 5.83 | 0 |
| sanic | 12,359 | 5.22 | 4.87 | 6.61 | 10.47 | 0 |
| starlette | 11,925 | 5.36 | 4.68 | 7.65 | 7.93 | 0 |
| fastapi | 6,663 | 9.59 | 9.85 | 11.48 | 11.75 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #1
- path_param: #1
- plaintext: #1
- query_params: #1
- routing_stress: #1
