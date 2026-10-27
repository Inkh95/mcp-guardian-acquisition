# Evaluating an MCP tool-control component

Founder disclosure: MCP Guardian is commercial software by Dobromir Kostov. This public guide describes an evaluation workflow, not independent security certification.

## Start with a concrete boundary

Before connecting an agent to a tool, answer three questions:

1. What executable package, command or remote endpoint does the configuration select?
2. Which tool calls may that agent make, and which require a separate reviewer?
3. What evidence remains if the operation is blocked, approved or ends ambiguously?

A configuration scanner and a runtime gate address different points. A clean configuration scan does not prove that every later action is safe.

## What to test

| Synthetic case | Acceptance question |
|---|---|
| Allowed read | Does the permitted call reach only the configured upstream? |
| Denied action | Is the call stopped before the upstream is invoked? |
| Sensitive action | Is a request-bound review required before execution? |
| Approval replay | Is a second use of that approval identifier rejected? |
| Request change | Does modifying the bound payload invalidate approval? |
| Cross-tenant read | Are another tenant's records inaccessible? |
| Argument redaction | Do new journal events omit arguments and context? |
| Uncertain upstream outcome | Can an operator investigate without blindly retrying? |

Use disposable synthetic records and isolated upstream fixtures. Do not use real customer secrets for a demo.

## Evaluate the supplied package

The current [organization source package](https://payhip.com/b/kL8Z3) includes setup instructions, tests and five-scenario buyer demo. After installing its locked dependencies and package in an isolated Python environment:

```sh
mcp-guardian-scan examples/safe-mcp.json
mcp-guardian-scan examples/unsafe-mcp.json --format sarif
python demos/buyer_demo.py
python demos/local_registry_smoke.py
```

These commands require the purchased package. This public showroom does not include the proprietary scanner implementation or a free executable download. An unsafe scan can intentionally return a failing exit code.

The included verification record reports 177 tests and 95.45% Guardian statement coverage on Python 3.12.14 for the October delivery. Treat those as seller-provided test evidence and reproduce them in your environment. Synthetic coverage does not establish a real-world detection rate.

## Check integration compatibility first

The runtime implements a bounded JSON-RPC HTTP adapter. Native stdio, streaming and complete MCP session/version negotiation are not supplied. Do not assume it is a drop-in replacement for every MCP client.

Buyer acceptance should cover the exact client/server transport, TLS and ingress controls, gateway bypass prevention, deployment isolation, backup/restore, retention and upstream crash reconciliation. Docker definitions are supplied, but their execution remains a deployment acceptance task in the current delivery evidence.

An approval identifier is claimed once; that is not distributed exactly-once execution across new requests. The audit hash chain is unkeyed and unanchored, so an actor able to rewrite the database consistently can defeat it.

## Commercial next step

- [Review the organization source license and purchase](https://payhip.com/b/kL8Z3): EUR 74.99 one-time for the supplied version. No exclusive ownership, installation, hosting, support, maintenance or future updates included.
- [Review acquisition scope](ACQUISITION.md): separate initial asking price EUR 19,500, subject to diligence, existing licenses and a signed transfer agreement.
- Contact Dobromir Kostov through the [owner profile](https://github.com/Inkh95) for an enterprise evaluation discussion. Private source access requires a separately agreed review process.

Updated 27 October 2026.
