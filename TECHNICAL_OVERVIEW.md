# Technical overview

## Two-stage control

MCP Guardian applies the same security posture before deployment and during execution:

1. The offline scanner reads MCP JSON/YAML configuration.
2. It inventories configured servers and evaluates executable, package, transport, credential, permission, filesystem, egress and metadata risks.
3. Results are emitted as normalized JSON or SARIF 2.1.0 for CI/code-scanning workflows.
4. At runtime, the gateway normalizes tool calls and applies deterministic policy.
5. Each action is allowed, blocked, or placed behind a human approval checkpoint.
6. Approved execution is atomically claimed to prevent duplicate forwarding.
7. Evaluations and approval events enter a tenant-scoped, tamper-evident audit chain.

## Publicly disclosed controls

- Fixed trusted upstream routing; no client-selected upstream URL
- Deterministic baseline enforcement without an external model dependency
- Separate operator and approver authorization boundaries
- Tenant-scoped approvals and audit queries
- Duplicate-execution protection for approved actions
- Signed webhook validation with replay-window enforcement
- JSON, SARIF, REST/OpenAPI and CLI integration surfaces
- Reproducible dependency locks and CI container smoke testing

## Deployment profile

The private package uses Python 3.12, FastAPI, Pydantic, SQLite, HTTPX, Docker and GitHub Actions. It is deliberately compact and embeddable. Storage, identity and transport boundaries are documented for replacement with a buyer's enterprise infrastructure.

Exact rule implementation, internal schemas and production source remain private until controlled diligence under NDA.
