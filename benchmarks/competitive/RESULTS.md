# Competitive Benchmark Results

**Generated:** 2026-09-28T12:57:05+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 12,201 | 6,699 | 19,831 🏆 | 8,459 | 10,030 | 15,863 |
| json | 30,350 | 11,530 | 33,883 🏆 | 13,252 | 11,370 | 26,823 |
| path_param | 28,283 | 9,862 | 30,462 🏆 | 11,823 | 11,489 | 22,899 |
| plaintext | 41,584 | 11,251 | 52,586 🏆 | 13,357 | 12,694 | 32,796 |
| query_params | 16,292 | 8,010 | 19,078 🏆 | 10,956 | 10,055 | 15,899 |
| routing_stress | 29,018 | 6,507 | 33,285 🏆 | 13,793 | 12,540 | 9,637 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 6.72 | 20.44 | 4.19 🏆 | 11.43 | 13.78 | 5.77 |
| json | 2.67 🏆 | 6.65 | 2.85 | 6.10 | 6.70 | 3.03 |
| path_param | 2.83 | 8.89 | 2.67 🏆 | 6.50 | 7.27 | 3.53 |
| plaintext | 2.04 | 6.82 | 2.00 🏆 | 5.45 | 6.07 | 2.66 |
| query_params | 4.61 | 10.33 | 4.03 🏆 | 6.76 | 7.90 | 4.70 |
| routing_stress | 3.02 | 12.76 | 2.42 🏆 | 5.67 | 11.69 | 8.91 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 19,831 | 3.22 | 3.19 | 3.77 | 4.19 | 0 |
| starlette | 15,863 | 4.05 | 3.90 | 4.89 | 5.77 | 0 |
| blacksheep | 12,201 | 5.24 | 5.02 | 6.27 | 6.72 | 0 |
| sanic | 10,030 | 6.44 | 5.84 | 8.37 | 13.78 | 0 |
| litestar | 8,459 | 7.62 | 7.11 | 9.51 | 11.43 | 0 |
| fastapi | 6,699 | 9.62 | 9.11 | 11.95 | 20.44 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 33,883 | 1.88 | 1.87 | 2.14 | 2.85 | 0 |
| blacksheep | 30,350 | 2.11 | 2.13 | 2.39 | 2.67 | 0 |
| starlette | 26,823 | 2.37 | 2.39 | 2.76 | 3.03 | 0 |
| litestar | 13,252 | 4.82 | 4.90 | 5.54 | 6.10 | 0 |
| fastapi | 11,530 | 5.55 | 5.72 | 6.39 | 6.65 | 0 |
| sanic | 11,370 | 5.64 | 5.72 | 6.29 | 6.70 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 30,462 | 2.08 | 2.12 | 2.40 | 2.67 | 0 |
| blacksheep | 28,283 | 2.25 | 2.27 | 2.61 | 2.83 | 0 |
| starlette | 22,899 | 2.77 | 2.79 | 3.22 | 3.53 | 0 |
| litestar | 11,823 | 5.41 | 5.62 | 6.26 | 6.50 | 0 |
| sanic | 11,489 | 5.58 | 5.67 | 6.32 | 7.27 | 0 |
| fastapi | 9,862 | 6.48 | 6.05 | 8.61 | 8.89 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 52,586 | 1.20 | 1.19 | 1.42 | 2.00 | 0 |
| blacksheep | 41,584 | 1.53 | 1.56 | 1.77 | 2.04 | 0 |
| starlette | 32,796 | 1.93 | 1.96 | 2.23 | 2.66 | 0 |
| litestar | 13,357 | 4.75 | 4.99 | 5.25 | 5.45 | 0 |
| sanic | 12,694 | 5.05 | 5.08 | 5.64 | 6.07 | 0 |
| fastapi | 11,251 | 5.68 | 5.75 | 6.57 | 6.82 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 19,078 | 3.35 | 3.46 | 3.80 | 4.03 | 0 |
| blacksheep | 16,292 | 3.92 | 4.07 | 4.35 | 4.61 | 0 |
| starlette | 15,899 | 4.02 | 4.17 | 4.47 | 4.70 | 0 |
| litestar | 10,956 | 5.83 | 6.20 | 6.48 | 6.76 | 0 |
| sanic | 10,055 | 6.37 | 6.42 | 7.50 | 7.90 | 0 |
| fastapi | 8,010 | 7.98 | 8.38 | 10.07 | 10.33 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 33,285 | 1.92 | 1.93 | 2.18 | 2.42 | 0 |
| blacksheep | 29,018 | 2.20 | 2.21 | 2.50 | 3.02 | 0 |
| litestar | 13,793 | 4.63 | 4.61 | 5.38 | 5.67 | 0 |
| sanic | 12,540 | 5.16 | 4.72 | 6.90 | 11.69 | 0 |
| starlette | 9,637 | 6.63 | 5.99 | 8.65 | 8.91 | 0 |
| fastapi | 6,507 | 9.83 | 9.70 | 12.43 | 12.76 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #1
- path_param: #1
- plaintext: #1
- query_params: #1
- routing_stress: #1
