---
title: "Skaphos"
---

Kubernetes is a programmable reconciliation substrate — APIs, controllers, desired state, status, policy. Most platform products discard that and ship a hosting interface with different nouns. Skaphos doesn't.

Skaphos is an open suite of platform-control tools for teams that need to encode operational intent — applications, releases, environments, cells, promotions, policy, audit — as durable primitives rather than spreadsheets, tickets, or vendor UI state.

## What guides the work

- Git is the durable desired-state boundary.
- Topology is part of deployment state, not metadata.
- Promotion is a control-plane workflow, not CI glue.
- Reconciliation must be explainable, and every mutation auditable.
- Read-only degradation beats operational blindness.

## Where it is going

Skaphos is adoptable in layers: visibility first, then structure, then control. The work is organized into two portfolios — Skaphos Platform for the core control-plane systems, and Adjacent Tools for complementary utilities such as Repokeeper and Wake. The [manifesto]({{< relref "manifesto" >}}) is the long form of why this work exists.
