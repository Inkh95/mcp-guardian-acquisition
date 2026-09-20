# Verified benchmark summary

Private release: `v0.5.0`

| Verification | Result |
|---|---:|
| Automated tests | 31/31 passing |
| Code coverage | 92.66% |
| Policy evaluations | 50,000 |
| Mean latency | 0.0216 ms |
| Median latency | 0.0195 ms |
| p95 latency | 0.0215 ms |

The reference benchmark measures the deterministic policy engine for an exfiltration-risk request with a 512-character payload on Python 3.12. It excludes HTTP transport, database persistence, network latency, and downstream MCP execution. Results vary by host and can be independently reproduced under NDA.

