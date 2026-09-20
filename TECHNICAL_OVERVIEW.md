# Technical overview

## Decision pipeline

1. A trusted gateway assigns tenant and agent identity.
2. MCP Guardian normalizes the JSON-RPC tool request.
3. The deterministic policy engine evaluates tool name, arguments, destination, payload, and transaction context.
4. The request is allowed, blocked, or queued for human approval.
5. Allowed requests are forwarded only to deployment-configured upstreams.
6. Approval execution is atomically claimed to prevent duplicate forwarding.
7. Every evaluation is written into the tamper-evident audit chain.

## Security properties

- No client-selected upstream URL
- No external AI model required for baseline decisions
- Tenant identity is not trusted from the request body
- Separate approval authorization boundary
- Constant-time comparison for configured secrets
- Failed approved executions can be safely retried
- Completed approvals cannot be executed again
- Audit-chain integrity can be verified through the API

## Deployment profile

The private package uses Python 3.12, FastAPI, Pydantic, SQLite, HTTPX, Docker, and GitHub Actions. The design is intentionally compact and transferable, while keeping storage and transport interfaces suitable for replacement with a buyer's preferred enterprise infrastructure.

