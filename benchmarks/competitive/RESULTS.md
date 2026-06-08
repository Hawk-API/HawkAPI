# Competitive Benchmark Results

**Generated:** 2026-06-08T10:54:17+00:00  
**Config:** 10s × 64 connections × 4 wrk threads  
**Server:** Granian (1 worker, ASGI)  
**Tool:** wrk

## Summary — Throughput (Requests/sec, higher is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 18,014 | 9,280 | 25,704 🏆 | 12,798 | 14,345 | 20,708 |
| json | 45,699 | 18,305 | 47,182 🏆 | 22,680 | 19,158 | 40,774 |
| path_param | 43,265 | 13,848 | 44,063 🏆 | 18,083 | 18,910 | 37,162 |
| plaintext | 54,442 | 17,939 | 61,001 🏆 | 24,304 | 22,008 | 44,886 |
| query_params | 29,943 | 14,537 | 33,203 🏆 | 17,740 | 15,907 | 27,358 |
| routing_stress | 44,658 | 9,329 | 47,202 🏆 | 21,708 | 18,244 | 14,192 |

## p99 Latency (ms, lower is better)

| Scenario | blacksheep | fastapi | hawkapi | litestar | sanic | starlette |
|---|---|---|---|---|---|---|
| body_validation | 4.43 | 15.65 | 3.04 🏆 | 6.84 | 12.47 | 4.03 |
| json | 2.11 | 4.41 | 1.92 🏆 | 3.35 | 4.11 | 1.94 |
| path_param | 1.86 | 6.33 | 1.84 🏆 | 4.24 | 4.17 | 2.10 |
| plaintext | 1.91 | 4.50 | 1.83 | 3.16 | 3.65 | 1.78 🏆 |
| query_params | 2.60 | 7.34 | 2.36 🏆 | 4.43 | 5.23 | 2.80 |
| routing_stress | 1.81 | 9.31 | 1.73 🏆 | 3.49 | 10.56 | 6.26 |

## Detailed Results

### body_validation

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 25,704 | 2.47 | 2.49 | 2.80 | 3.04 | 0 |
| starlette | 20,708 | 3.08 | 3.05 | 3.55 | 4.03 | 0 |
| blacksheep | 18,014 | 3.52 | 3.47 | 4.11 | 4.43 | 0 |
| sanic | 14,345 | 4.50 | 4.17 | 5.38 | 12.47 | 0 |
| litestar | 12,798 | 5.01 | 4.74 | 6.27 | 6.84 | 0 |
| fastapi | 9,280 | 6.96 | 6.66 | 8.65 | 15.65 | 0 |

### json

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 47,182 | 1.35 | 1.35 | 1.55 | 1.92 | 0 |
| blacksheep | 45,699 | 1.40 | 1.39 | 1.60 | 2.11 | 0 |
| starlette | 40,774 | 1.56 | 1.55 | 1.75 | 1.94 | 0 |
| litestar | 22,680 | 2.80 | 2.87 | 3.14 | 3.35 | 0 |
| sanic | 19,158 | 3.33 | 3.35 | 3.80 | 4.11 | 0 |
| fastapi | 18,305 | 3.49 | 3.37 | 4.20 | 4.41 | 0 |

### path_param

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 44,063 | 1.45 | 1.45 | 1.64 | 1.84 | 0 |
| blacksheep | 43,265 | 1.48 | 1.48 | 1.67 | 1.86 | 0 |
| starlette | 37,162 | 1.72 | 1.72 | 1.92 | 2.10 | 0 |
| sanic | 18,910 | 3.39 | 3.38 | 3.90 | 4.17 | 0 |
| litestar | 18,083 | 3.54 | 3.77 | 4.06 | 4.24 | 0 |
| fastapi | 13,848 | 4.62 | 4.49 | 5.97 | 6.33 | 0 |

### plaintext

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 61,001 | 1.04 | 1.02 | 1.21 | 1.83 | 0 |
| blacksheep | 54,442 | 1.17 | 1.17 | 1.36 | 1.91 | 0 |
| starlette | 44,886 | 1.42 | 1.42 | 1.61 | 1.78 | 0 |
| litestar | 24,304 | 2.62 | 2.66 | 2.94 | 3.16 | 0 |
| sanic | 22,008 | 2.90 | 2.89 | 3.33 | 3.65 | 0 |
| fastapi | 17,939 | 3.56 | 3.47 | 4.23 | 4.50 | 0 |

### query_params

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 33,203 | 1.91 | 1.92 | 2.16 | 2.36 | 0 |
| blacksheep | 29,943 | 2.13 | 2.15 | 2.41 | 2.60 | 0 |
| starlette | 27,358 | 2.33 | 2.35 | 2.61 | 2.80 | 0 |
| litestar | 17,740 | 3.58 | 3.77 | 4.24 | 4.43 | 0 |
| sanic | 15,907 | 4.03 | 3.90 | 4.93 | 5.23 | 0 |
| fastapi | 14,537 | 4.40 | 3.85 | 6.34 | 7.34 | 0 |

### routing_stress

| Framework | RPS | avg ms | p50 ms | p95 ms | p99 ms | errors |
|---|---:|---:|---:|---:|---:|---:|
| hawkapi | 47,202 | 1.35 | 1.36 | 1.54 | 1.73 | 0 |
| blacksheep | 44,658 | 1.42 | 1.44 | 1.63 | 1.81 | 0 |
| litestar | 21,708 | 2.95 | 3.00 | 3.27 | 3.49 | 0 |
| sanic | 18,244 | 3.55 | 3.32 | 4.46 | 10.56 | 0 |
| starlette | 14,192 | 4.47 | 3.87 | 6.09 | 6.26 | 0 |
| fastapi | 9,329 | 6.81 | 6.24 | 8.99 | 9.31 | 0 |


## How HawkAPI Ranks

HawkAPI placement per scenario:

- body_validation: #1
- json: #1
- path_param: #1
- plaintext: #1
- query_params: #1
- routing_stress: #1
