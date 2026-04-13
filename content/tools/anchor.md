---
title: "Anchor"
weight: 40
tagline: "Admission-time enforcement for immutable artifact references"
status: "Proposed"
statusClass: "status-proposed"
summary: "Anchor enforces immutable artifact references at admission time across Kubernetes workloads and delivery resources."
module: "github.com/skaphos/anchor"
---

Anchor is a Kubernetes admission controller that enforces immutable artifact references across a cluster.

It rejects or warns on mutable references such as floating image tags, `latest`, unpinned Helm chart versions, or unresolved channel selectors before those resources are persisted.

## What it validates

- Container image references in workload specs.
- Helm chart version references in Flux resources.
- Git reference fields in GitOps source resources.
- Additional declared fields through policy-driven matching.
