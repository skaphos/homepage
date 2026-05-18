---
title: "About"
---

Skaphos is an open suite of platform-control tools for teams that operate Kubernetes-based systems across many applications, clusters, regions, environments, and failure domains.

We are not building a Kubernetes dashboard, a CI system, a hosted PaaS, or a wrapper around primitives the ecosystem already provides. We are building the control-plane layer between raw infrastructure and human process — the layer that makes platform state explicit, delivery explainable, topology inspectable, policy enforceable, and recovery deterministic.

The long form of why is in the [manifesto]({{< relref "manifesto" >}}).

## Who it is for

Platform engineers, infrastructure engineers, and Kubernetes operators running real production environments. Skaphos assumes Kubernetes fundamentals and works directly with Kubernetes primitives and APIs rather than abstracting them away.

## How to adopt it

Skaphos tools are adoptable in layers. Start at visibility — inventory, topology discovery, drift, ownership — without any control-plane mutation. Add standardization when repository and environment structure needs to converge. Take on control — promotion, policy gates, Git mutation, audit — only when trust is earned.

## What it is not

- Not a platform-as-a-service abstraction.
- Not a proprietary orchestration layer that replaces Kubernetes.
- Not a per-application pricing trap dressed up as a control plane.
