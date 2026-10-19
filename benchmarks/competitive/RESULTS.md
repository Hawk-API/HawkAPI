# Competitive Benchmark Results

**Generated:** 2026-10-19T12:09:18+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 12,363 | 6,850 | 19,932 🏆 | 8,900 | 10,604 | 16,423 |
| json | 31,029 | 11,672 | 34,360 🏆 | 13,568 | 11,964 | 26,964 |
| path_param | 28,542 | 9,063 | 31,595 🏆 | 12,029 | 11,899 | 23,512 |
| plaintext | 43,192 | 12,008 | 53,186 🏆 | 13,997 | 12,908 | 33,524 |
| query_params | 16,479 | 8,558 | 18,601 🏆 | 11,589 | 9,738 | 15,587 |
| routing_stress | 29,786 | 6,483 | 33,185 🏆 | 13,340 | 13,562 | 9,413 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 6.69 | 14.84 | 4.13 🏆 | 10.14 | 14.70 | 5.66 |
| json | 2.56 🏆 | 6.56 | 2.59 | 5.56 | 6.35 | 2.98 |
| path_param | 2.84 | 8.68 | 2.53 🏆 | 6.32 | 6.30 | 3.57 |
| plaintext | 1.98 🏆 | 6.62 | 2.11 | 5.28 | 5.81 | 2.53 |
| query_params | 4.58 | 9.98 | 4.08 🏆 | 6.51 | 7.61 | 4.70 |
| routing_stress | 2.73 | 12.16 | 2.38 🏆 | 5.54 | 11.03 | 8.44 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 19,932 | 3.19 | 3.16 | 3.74 | 4.13 | 0 |
| starlette | 16,423 | 3.88 | 3.77 | 4.72 | 5.66 | 0 |
| blacksheep | 12,363 | 5.14 | 4.93 | 6.21 | 6.69 | 0 |
| sanic | 10,604 | 6.10 | 5.56 | 7.99 | 14.70 | 0 |
| litestar | 8,900 | 7.21 | 6.70 | 9.04 | 10.14 | 0 |
| fastapi | 6,850 | 9.37 | 8.94 | 11.51 | 14.84 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 34,360 | 1.85 | 1.86 | 2.11 | 2.59 | 0 |
| blacksheep | 31,029 | 2.06 | 2.10 | 2.36 | 2.56 | 0 |
| starlette | 26,964 | 2.35 | 2.36 | 2.73 | 2.98 | 0 |
| litestar | 13,568 | 4.69 | 5.02 | 5.36 | 5.56 | 0 |
| sanic | 11,964 | 5.35 | 5.49 | 6.09 | 6.35 | 0 |
| fastapi | 11,672 | 5.48 | 5.45 | 6.35 | 6.56 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 31,595 | 2.01 | 2.04 | 2.31 | 2.53 | 0 |
| blacksheep | 28,542 | 2.23 | 2.23 | 2.59 | 2.84 | 0 |
| starlette | 23,512 | 2.72 | 2.72 | 3.16 | 3.57 | 0 |
| litestar | 12,029 | 5.31 | 5.24 | 6.10 | 6.32 | 0 |
| sanic | 11,899 | 5.38 | 5.54 | 6.03 | 6.30 | 0 |
| fastapi | 9,063 | 7.05 | 7.27 | 8.46 | 8.68 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 53,186 | 1.19 | 1.17 | 1.41 | 2.11 | 0 |
| blacksheep | 43,192 | 1.47 | 1.50 | 1.74 | 1.98 | 0 |
| starlette | 33,524 | 1.89 | 1.92 | 2.19 | 2.53 | 0 |
| litestar | 13,997 | 4.57 | 4.80 | 5.10 | 5.28 | 0 |
| sanic | 12,908 | 4.97 | 5.04 | 5.55 | 5.81 | 0 |
| fastapi | 12,008 | 5.32 | 5.18 | 6.38 | 6.62 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 18,601 | 3.42 | 3.55 | 3.84 | 4.08 | 0 |
| blacksheep | 16,479 | 3.88 | 4.06 | 4.32 | 4.58 | 0 |
| starlette | 15,587 | 4.10 | 4.24 | 4.49 | 4.70 | 0 |
| litestar | 11,589 | 5.52 | 5.92 | 6.31 | 6.51 | 0 |
| sanic | 9,738 | 6.57 | 6.84 | 7.32 | 7.61 | 0 |
| fastapi | 8,558 | 7.47 | 7.40 | 9.76 | 9.98 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 33,185 | 1.92 | 1.93 | 2.17 | 2.38 | 0 |
| blacksheep | 29,786 | 2.13 | 2.14 | 2.48 | 2.73 | 0 |
| sanic | 13,562 | 4.77 | 4.41 | 6.30 | 11.03 | 0 |
| litestar | 13,340 | 4.79 | 5.04 | 5.33 | 5.54 | 0 |
| starlette | 9,413 | 6.79 | 6.83 | 8.28 | 8.44 | 0 |
| fastapi | 6,483 | 9.86 | 10.10 | 11.96 | 12.16 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #1
- path_param: #1
- plaintext: #1
- query_params: #1
- routing_stress: #1
