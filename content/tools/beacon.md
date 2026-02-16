---
title: "Beacon"
tagline: "Platform integrity validation for Kubernetes"
status: "Planned and under development"
statusClass: "status-planned"
summary: "Beacon validates Kubernetes platform integrity against explicit operational requirements."
repo: "https://github.com/skaphos/cluster-health"
module: "github.com/skaphos/cluster-health"
---

Beacon validates Kubernetes platform integrity against explicit health requirements.

Monitoring tells you what is happening; Beacon evaluates whether the platform is structurally sound.

## Planned components

- Beacon Operator: in-cluster continuous evaluation and Kubernetes resource publication.
- Beacon CLI: human-readable inspection, CI/CD integration, and diagnostics.

## Example invariant domains

- Certificate issuance and expiry safety.
- Ingress and routing functionality.
- Service mesh control plane operation.
- CNI and DNS functionality.
- Cluster networking and Kubernetes API consistency.
