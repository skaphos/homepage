---
title: "Tack"
weight: 50
tagline: "Declarative progressive traffic shifting"
status: "Proposed"
statusClass: "status-proposed"
summary: "Tack manages blue/green and canary traffic shifting through a Kubernetes-native provider-agnostic interface."
module: "github.com/skaphos/tack"
---

Tack manages declarative progressive traffic shifting across multiple load balancer provider types.

It provides a Kubernetes-native surface for blue/green and canary traffic management while remaining decoupled from any specific deployment or upgrade system.

## Planned characteristics

- Provider-agnostic adapter model.
- Declarative `TrafficShift` resources.
- Manual or automated progression and rollback.
- Clean integration point for Meridian rollouts without depending on Meridian.
