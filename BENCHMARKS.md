# Verified benchmark summary

Private release: `v1.1.0`  
Verification environment: Python 3.12.14, 2026-09-22

| Verification | Result |
|---|---:|
| Automated tests | 53 passing |
| Statement coverage | 93.75% |
| Calibration corpus | 10 synthetic cases / 1,000 scans |
| Holdout corpus | 30 synthetic cases / 3,000 scans |
| False positives / false negatives | 0 / 0 on both included corpora |
| Expected-rule misses | 0 |
| Holdout median latency | 0.0144 ms |
| Holdout p95 latency | 0.0259 ms |
| Policy microbenchmark | 50,000 evaluations |
| Policy median / p95 | 0.0199 ms / 0.0291 ms |
| Locked dependency audits | 0 known vulnerabilities |
| Container verification | Build, health and authenticated scan successful in CI |

The two corpora are seller-authored synthetic regression fixtures. The results establish deterministic behavior for the included cases only and are not a third-party field benchmark or a universal detection-rate claim. Latency is host-dependent and excludes network transport and downstream MCP execution.
