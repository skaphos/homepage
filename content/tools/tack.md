---
title: "Tack"
weight: 50
portfolio: "Skaphos Platform"
tagline: "Declarative progressive traffic shifting"
status: "Proposed"
statusClass: "status-proposed"
summary: "Tack expresses progressive traffic shifts — canary and blue/green — as declarative intent, independent of the engine directing the traffic."
module: "github.com/skaphos/tack"
---

Tack expresses progressive traffic shifting — canary steps and blue/green cutover — as declarative intent.

Many different engines can direct traffic to clusters: cloud load balancers, service meshes, API gateways, ingress controllers, DNS, and CDNs. Tack's premise is that the shift itself — source, destination, progression, rollback — deserves a first-class declarative surface that does not depend on whichever engine happens to be moving the packets.

How that intent binds to concrete traffic engines is deliberately unsettled; the integration model is being rethought before implementation begins.

## Scope

- Declarative expression of a traffic shift: source, destination, progression steps, rollback.
- Manual or automated progression.
- Decoupled from any specific deployment or upgrade system; a clean integration point for Meridian rollouts without depending on Meridian.
