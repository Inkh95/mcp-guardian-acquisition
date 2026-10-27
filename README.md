# MCP Guardian — AI Tool Governance

**MCP security scanning before deployment. Deterministic governance at tool-call time.**

[![Status](https://img.shields.io/badge/status-acquisition%20available-55e6a5)](#acquisition)
[![Release](https://img.shields.io/badge/private%20release-v1.1.0-7c8cff)](#verified-snapshot)
[![Tests](https://img.shields.io/badge/tests-53%20passing-55e6a5)](#verified-snapshot)
[![Coverage](https://img.shields.io/badge/coverage-93.75%25-55e6a5)](#verified-snapshot)

MCP Guardian is a private-source software component available through a non-exclusive organization source license or a separately negotiated project acquisition. It detects risky MCP configuration in CI, emits SARIF, and enforces allow/block/human-approval decisions when AI agents call tools.

![Verified CLI demonstration](assets/demo-scan.svg)

## October 2026 organization release

The [current commercial download](https://payhip.com/b/kL8Z3) is the October 27 organization source package. It adds credential-bound tenant identities, exact tool/server scopes, expiring request-bound approvals, metadata-only new journal events, local heuristic signals and an operational console. Python 3.12 is recommended (project minimum 3.11). Initial dependency installation needs registry access; prepared-wheel offline installation is documented. The core requires no paid model API or seller-hosted license check.

This is a self-hosted developer integration component. Its runtime is a bounded JSON-RPC HTTP adapter; native stdio, streaming and complete MCP session/version negotiation are not supplied. Validate your exact integration before deployment. Installation, hosting, custom integration, support, maintenance and future releases are not included. The audit chain is unkeyed and unanchored; it does not protect against an attacker who can rewrite the database consistently.

Read [the practical evaluation guide](EVALUATION_GUIDE.md) before choosing an integration. The historical v1.1.0 measurements below describe that earlier snapshot, not a new independent evaluation of the October delivery.

## The gap

Agent observability explains what happened. Prompt guardrails inspect model traffic. Traditional SAST inspects source. MCP Guardian controls the boundary where agent configuration becomes executable tool access.

## Integration surface

- CLI: scan JSON/YAML and return CI exit codes
- SARIF 2.1.0: upload findings to existing code-scanning workflows
- REST: embed scanner decisions in a product backend
- Runtime proxy: enforce trusted upstreams and risk policy
- Approval API: route destructive or high-value actions to a human
- Audit API: retrieve tenant-scoped records and verify chain integrity

## Architecture

```mermaid
flowchart TD
    C["MCP config"] --> S["Static scanner"]
    S --> R["JSON / SARIF"]
    A["AI agent"] --> G["Runtime gateway"]
    G --> D{"Allow / Block / Approve"}
    D --> U["Trusted MCP server"]
    G --> E["Audit evidence"]
```

## Verified snapshot

| Metric | Verified result |
|---|---:|
| Tests | 53 passed |
| Statement coverage | 93.75% |
| Calibration / holdout cases | 10 / 30 synthetic fixtures |
| Calibration / holdout runs | 1,000 / 3,000 |
| Precision / recall on both corpora | 1.000 / 1.000 |
| Holdout median / p95 latency | 0.0144 ms / 0.0259 ms |
| Production + development audits | 0 known vulnerabilities |
| Container | Build, startup, health and authenticated scan verified in CI |

The accuracy result applies only to the included seller-authored synthetic corpora. The separate holdout is not third-party validation and the result is not presented as a universal real-world detection rate.

## What the buyer receives

Complete private source and repository history, tests, evaluation suite, API/CLI, Docker and CI assets, documentation, assignable seller-owned project IP, and ten business days of asynchronous transition support during the first 30 days after closing.

**Organization source license: EUR 74.99** — [buy on Payhip](https://payhip.com/b/kL8Z3). One legal organization receives a non-exclusive perpetual license for the supplied version, including use, modification and deployment for its own operations and products under the included LICENSE.md. Standalone redistribution/resale of the source, exclusive IP, support, maintenance and future releases are not included.

**Project acquisition initial asking price: EUR 19,500**, subject to NDA, technical/legal diligence, existing non-exclusive licenses, and a signed asset purchase/IP assignment agreement.

No production implementation details are included in this showroom. A read-only private review can follow mutual NDA.

## Acquisition

Project acquisition is a separate software asset transaction, not a subscription, token sale, equity offering, or revenue-multiple claim. Licenses already granted remain subject to their terms. See [ACQUISITION.md](ACQUISITION.md), [BENCHMARKS.md](BENCHMARKS.md), [TECHNICAL_OVERVIEW.md](TECHNICAL_OVERVIEW.md), and [INTEGRATION.md](INTEGRATION.md).


## AEGIS Gateway technical evaluation

AEGIS extends the MCP Guardian approach with model and policy version governance, exact-request human approval and a metadata-only AI Flight Recorder. The current v0.7 build has a localhost synthetic demo and 74 passing automated tests. It is offered for scoped technical evaluation; it is not a production security certification or clinically validated healthcare product. See [AEGIS.md](AEGIS.md) for capabilities, evidence and limitations.

To request the public-safe acquisition brief or NDA process, contact the owner through the [GitHub profile](https://github.com/Inkh95).
