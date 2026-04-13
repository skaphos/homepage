---
title: "Berth"
weight: 20
portfolio: "Skaphos Platform"
tagline: "Distributed lease coordination for multi-cluster Kubernetes workloads"
status: "Released"
statusClass: "status-released"
summary: "Berth provides Kubernetes-native distributed lease coordination for cross-cluster workloads and shared resources."
repo: "https://github.com/skaphos/berth"
module: "github.com/skaphos/berth"
---

Berth is a distributed lease coordination service for Kubernetes multi-cluster workloads.

It provides TTL-based leases for cross-cluster mutual exclusion without introducing an external database or separate consensus layer. Leases are expressed as Kubernetes resources and managed through an API server, an operator, and a CLI.

## Core components

- API server for lease operations.
- Operator that reconciles `BerthLease` resources.
- CLI for inspection, release, and diagnostics.

## Typical use cases

- CronJob singleton execution across a fleet.
- Exclusive access to shared external systems.
- Leader election for cross-cluster controllers.
- Multi-cluster workload coordination with explicit lease state.
