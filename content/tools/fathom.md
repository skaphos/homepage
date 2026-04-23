---
title: "Fathom"
weight: 25
portfolio: "Skaphos Platform"
tagline: "Platform integrity validation for Kubernetes"
status: "Planned"
statusClass: "status-planned"
summary: "Fathom validates Kubernetes cluster integrity against explicit platform health requirements."
repo: "https://github.com/skaphos/fathom"
module: "github.com/skaphos/fathom"
---

Fathom validates Kubernetes cluster integrity against defined platform health requirements.

It is focused on structural platform soundness rather than metric-based monitoring and can be deployed to a Kubernetes cluster as a standalone system.

## Conceptual components

- Fathom Operator for in-cluster continuous evaluation and Kubernetes resource publication.
- Fathom CLI for human-readable inspection, CI/CD integration, and fleet diagnostics.

## Example invariant domains

- Certificate issuance and expiry safety.
- Ingress and routing functionality.
- Ingress surface reachability and TLS termination.
- Service mesh control plane operation.
- CNI and DNS functionality.
- Cluster networking and Kubernetes API consistency.
