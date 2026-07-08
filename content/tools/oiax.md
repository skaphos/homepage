---
title: "Oiax"
weight: 75
portfolio: "Adjacent Tools"
tagline: "Declarative Git branch promotion reconciliation"
status: "Proposed"
statusClass: "status-proposed"
summary: "Oiax keeps promotion pull requests reconciled across branch-per-environment GitOps repositories, and returns downstream hotfixes to the source branch."
module: "github.com/skaphos/oiax"
---

Oiax is a declarative Git branch promotion reconciler for repositories that model environments as long-lived branches.

Given a declared promotion graph, it observes branch and forge state and ensures the pull requests required to move changes through that graph exist — exactly one active managed request per diverged edge — the posture release-please takes toward release pull requests, applied to environment promotion.

The name is the Greek οἴαξ — the tiller, the handle fitted to the rudder head. Oiax removes Git workflow toil; a hand stays on the tiller. Approval, validation, and policy gates remain wherever the repository already puts them.

## Planned characteristics

- Promotion graph declared as data in a repository-local file.
- Content-based divergence detection that survives squash and rebase merges.
- Backflow: hotfixes landed on downstream branches are returned to the authoritative source branch via cherry-picked, deterministically named branches.
- Runs in CI — GitHub Actions first — with no persistent control plane.
- Idempotent and safe under concurrent, repeated, or missed invocations.

## Design boundary

Oiax manages the Git workflow that expresses promotion; it owns no promotion decisions and never merges its own pull requests. It serves teams below the control-plane threshold — branch-per-environment repositories on plain Argo CD or Flux. Teams running Keleustes do not need it for the applications Keleustes manages.
