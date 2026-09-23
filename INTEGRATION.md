# Public-safe integration examples

## CI scan

```bash
mcp-guardian-scan path/to/mcp.json --format sarif > results.sarif
```

The command exits `1` when a high/critical issue is found, `2` for invalid input, and `0` otherwise.

## Product API

```http
POST /v1/scan
content-type: application/json
x-api-key: ...

{"source_name":"client.json","document":{"mcpServers":{}}}
```

The response contains a normalized risk score, verdict, server inventory, severities, rule identifiers, remediation and optional CWE mapping. The private repository includes OpenAPI documentation and executable examples.

## Runtime policy decision

```json
{
  "decision": "require_approval",
  "risk_score": 85,
  "reasons": ["Destructive tool call"],
  "matched_rules": ["destructive-action"]
}
```

These examples describe stable public interfaces without disclosing proprietary rule implementation.
