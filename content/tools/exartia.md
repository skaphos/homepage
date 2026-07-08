---
title: "Exartia"
weight: 38
portfolio: "Skaphos Platform"
tagline: "Deterministic platform manifest bundles for cluster classes"
status: "Proposed"
statusClass: "status-proposed"
summary: "Exartia compiles versioned platform manifests into immutable OCI bundles with typed values contracts and ordered apply plans."
module: "github.com/skaphos/exartia"
---

Exartia is a deterministic platform manifest bundle compiler for Kubernetes.

It packages the platform components a cluster class carries — CNI, cert-manager, ingress, mesh, policy — as immutable, digest-pinned OCI bundles, validates typed cluster input against a declared schema, renders deterministically, and emits ordered apply plans for GitOps systems to reconcile.

The name is the Greek ἐξάρτια — a ship's fittings and rigging. A bundle is the fit-out of a cluster class: the versioned equipment set the hull carries.

## The package model

Helm and Kustomize both implement the overlay model: base YAML exists, and the consumer mutates it. Exartia implements the package model: an immutable versioned bundle owns structure, ordering, and the values contract; the cluster supplies only a digest-pinned bundle reference, target dimensions, and typed values. Cluster input is data, not behavior.

## Planned characteristics

- One bundle per cluster class, containing the class's intertwined component collection.
- Typed values validated against a bundle-declared JSON Schema; strict substitution, no template logic.
- Phase-class interleaved apply plans — all CRDs before any controller, all controllers before any cross-component configuration.
- `RenderLock` proof records binding bundle digest, values digest, renderer version, and output digest.
- One-shot applier only; Keleustes, Flux, or Argo CD own continuous reconciliation.

## Design boundary

Exartia fills the platform shaping artifact layer that Meridian explicitly defers. It does not provision clusters, does not reconcile continuously, and has no dependency on any other Skaphos tool.
