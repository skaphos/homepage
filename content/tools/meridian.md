---
title: "Meridian"
weight: 30
portfolio: "Skaphos Platform"
tagline: "Deterministic fleet lifecycle control for Kubernetes"
status: "In design"
statusClass: "status-active"
summary: "Meridian is a Kubernetes-native fleet lifecycle controller for provisioning, identity management, upgrades, and decommissioning."
repo: "https://github.com/skaphos/meridian"
module: "github.com/skaphos/meridian"
---

Meridian is a Kubernetes-native platform lifecycle controller for management clusters.

It manages the lifecycle of a Kubernetes fleet: provisioning, identity management, upgrade, and decommission. Cluster API is the provisioning engine beneath it, while Meridian defines deterministic fleet identity and replacement semantics on top.

## Scope

- Declarative cluster roles and platform profiles.
- Provider overlays and environment-aware fleet topology.
- Blue/green lifecycle orchestration for cluster replacement.
- Health-gated rollout progression with Fathom integration.

## Design boundary

Meridian coordinates fleet lifecycle state. It does not replace Kubernetes, act as a package manager, or become a GitOps engine.
