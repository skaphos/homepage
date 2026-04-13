---
title: "Skaphos CLI"
weight: 60
tagline: "Unified command surface for Skaphos platform tooling"
status: "Proposed"
statusClass: "status-proposed"
summary: "Skaphos CLI is a thin dispatcher that presents Meridian, Fathom, Tack, and Anchor through one consistent interface."
module: "github.com/skaphos/skaphos-cli"
---

Skaphos CLI is the unified command-line interface for the Skaphos platform tooling suite.

It is intentionally thin: each standalone tool remains the authoritative implementation, while `skaphos` provides a single entry point and plugin registry for operators who want a unified workflow.

## Intended scope

- Unified dispatch for Meridian, Fathom, Tack, and Anchor.
- Config-driven plugin registration.
- Tool discovery, verification, and version reporting.
- Consistent operational entry point without centralizing tool logic.
