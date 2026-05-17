---
title: "Keleustes"
weight: 35
portfolio: "Skaphos Platform"
tagline: "GitOps delivery control plane for Kubernetes platforms"
status: "Active"
statusClass: "status-active"
summary: "Keleustes is an open-source GitOps delivery control plane that unifies application sync, promotion, topology, policy, and audit into a single Kubernetes-native system."
module: "github.com/skaphos/keleustes"
---

Keleustes is a Kubernetes-native GitOps delivery control plane for platform teams running many applications across many clusters, environments, regions, and failure domains.

It combines topology-aware application modeling, GitOps reconciliation, release detection, promotion workflows, policy gates, health and diff, and audit history into a single system — rather than splitting that operating model across Argo CD, Kargo, custom CI scripts, and spreadsheets.

The name comes from the Greek κελευστής, the officer on a trireme who set the stroke and cadence for the rowers. Keleustes does not power the change; it directs the cadence of releases across environments, cells, and regions.

## What Keleustes replaces

- Argo CD application sync and visibility for supported deployment patterns.
- Kargo-style promotion orchestration.
- Custom CI scripts for environment promotion.
- Spreadsheet-driven deployment tracking.
- Ad hoc Git mutation bots.

## What Keleustes does not replace

Git, Kubernetes, Helm, Kustomize, OCI registries, CI systems, observability stacks, admission controllers, or change-management systems of record. Keleustes owns delivery control-plane state and composes with the rest.

## Core concepts

- `Application` — central delivery abstraction tying ownership, sources, manifest config, topology, and status together.
- `Source` — stream of deployable inputs (container images, Git, OCI artifacts, Helm charts, SBOMs).
- `Environment`, `Cell`, `DeploymentTarget` — ordered lifecycles, failure domains, and concrete targets.
- `Release` — pinned collection of artifacts for an application, with provenance.
- `Promotion` and `PromotionPolicy` — first-class objects for moving a Release into targets, with declared gates and evidence.

## Design boundary

Keleustes is opinionated about contracts and unopinionated about vendors. Notifications, signature verification, security scanning, policy gates, and audit forwarding are declarative plugin surfaces — built-in implementations cover the common case, and everything else attaches via webhook. Git is the durable desired-state boundary; cluster mutation outside break-glass is not a sanctioned path.
