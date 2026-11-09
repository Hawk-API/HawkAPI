# Competitive Benchmark Results

**Generated:** 2026-11-09T15:11:47+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 12,028 | 7,209 | 17,547 🏆 | 8,971 | 9,655 | 14,276 |
| json | 29,343 | 13,021 | 31,310 🏆 | 14,313 | 12,188 | 25,104 |
| path_param | 26,117 | 11,048 | 29,021 🏆 | 12,721 | 12,761 | 21,105 |
| plaintext | 41,008 | 12,660 | 52,397 🏆 | 14,727 | 13,967 | 30,999 |
| query_params | 15,538 | 8,922 | 17,183 🏆 | 12,940 | 11,383 | 16,473 |
| routing_stress | 27,335 | 6,831 | 31,109 🏆 | 13,677 | 12,147 | 12,254 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 7.48 | 15.28 | 4.70 🏆 | 9.78 | 13.78 | 6.30 |
| json | 2.65 🏆 | 6.76 | 3.13 | 5.88 | 6.67 | 3.09 |
| path_param | 3.05 | 8.42 | 2.68 🏆 | 6.62 | 6.77 | 3.78 |
| plaintext | 2.04 | 6.84 | 1.93 🏆 | 5.51 | 5.97 | 2.52 |
| query_params | 4.93 | 9.71 | 4.49 🏆 | 6.86 | 7.78 | 4.80 |
| routing_stress | 2.85 | 11.54 | 2.49 🏆 | 6.03 | 11.51 | 7.96 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 17,547 | 3.64 | 3.56 | 4.31 | 4.70 | 0 |
| starlette | 14,276 | 4.49 | 4.30 | 5.33 | 6.30 | 0 |
| blacksheep | 12,028 | 5.32 | 5.10 | 6.78 | 7.48 | 0 |
| sanic | 9,655 | 6.68 | 6.19 | 8.07 | 13.78 | 0 |
| litestar | 8,971 | 7.14 | 6.86 | 8.87 | 9.78 | 0 |
| fastapi | 7,209 | 8.91 | 8.36 | 11.34 | 15.28 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 31,310 | 2.03 | 2.03 | 2.28 | 3.13 | 0 |
| blacksheep | 29,343 | 2.16 | 2.20 | 2.43 | 2.65 | 0 |
| starlette | 25,104 | 2.55 | 2.55 | 2.91 | 3.09 | 0 |
| litestar | 14,313 | 4.47 | 4.29 | 5.60 | 5.88 | 0 |
| fastapi | 13,021 | 4.91 | 4.69 | 6.40 | 6.76 | 0 |
| sanic | 12,188 | 5.25 | 5.13 | 6.32 | 6.67 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 29,021 | 2.20 | 2.23 | 2.46 | 2.68 | 0 |
| blacksheep | 26,117 | 2.43 | 2.46 | 2.76 | 3.05 | 0 |
| starlette | 21,105 | 3.01 | 3.08 | 3.50 | 3.78 | 0 |
| sanic | 12,761 | 5.02 | 4.81 | 6.35 | 6.77 | 0 |
| litestar | 12,721 | 5.03 | 4.90 | 5.99 | 6.62 | 0 |
| fastapi | 11,048 | 5.76 | 5.11 | 8.06 | 8.42 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 52,397 | 1.21 | 1.19 | 1.44 | 1.93 | 0 |
| blacksheep | 41,008 | 1.55 | 1.58 | 1.79 | 2.04 | 0 |
| starlette | 30,999 | 2.06 | 2.07 | 2.28 | 2.52 | 0 |
| litestar | 14,727 | 4.34 | 4.18 | 5.26 | 5.51 | 0 |
| sanic | 13,967 | 4.59 | 4.48 | 5.52 | 5.97 | 0 |
| fastapi | 12,660 | 5.05 | 4.82 | 6.55 | 6.84 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 17,183 | 3.72 | 3.97 | 4.28 | 4.49 | 0 |
| starlette | 16,473 | 3.88 | 3.78 | 4.55 | 4.80 | 0 |
| blacksheep | 15,538 | 4.09 | 4.38 | 4.67 | 4.93 | 0 |
| litestar | 12,940 | 4.91 | 4.72 | 6.38 | 6.86 | 0 |
| sanic | 11,383 | 5.59 | 5.24 | 7.39 | 7.78 | 0 |
| fastapi | 8,922 | 7.17 | 6.51 | 9.31 | 9.71 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 31,109 | 2.05 | 2.07 | 2.28 | 2.49 | 0 |
| blacksheep | 27,335 | 2.33 | 2.36 | 2.62 | 2.85 | 0 |
| litestar | 13,677 | 4.67 | 4.46 | 5.76 | 6.03 | 0 |
| starlette | 12,254 | 5.22 | 4.60 | 7.61 | 7.96 | 0 |
| sanic | 12,147 | 5.32 | 5.00 | 6.58 | 11.51 | 0 |
| fastapi | 6,831 | 9.36 | 9.49 | 11.18 | 11.54 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #1
- path_param: #1
- plaintext: #1
- query_params: #1
- routing_stress: #1
