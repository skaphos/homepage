---
title: "Belay"
weight: 80
tagline: "Clean sidecar shutdown for CronJobs with injected proxies"
status: "Proposed"
statusClass: "status-proposed"
summary: "Belay keeps mesh-injected CronJob pods from hanging by ensuring injected proxy sidecars terminate when the primary container exits."
module: "github.com/skaphos/belay"
---

Belay ensures that Kubernetes CronJob pods containing injected service mesh proxy sidecars terminate cleanly when the primary container exits.

It operates as a mutating admission webhook that injects a lightweight watcher sidecar when mesh injection is detected, avoiding stuck Jobs and disrupted schedules.

## Intended fit

- Works with existing CronJob specs.
- Detects common mesh injection patterns.
- Handles sidecar shutdown inside the pod lifecycle.
- Solves a concrete operational problem without requiring a full platform stack.
