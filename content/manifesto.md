---
title: "Manifesto"
tagline: "Platform engineering as control-plane engineering"
---

Most organizations do not need another Kubernetes dashboard.

They do not need a prettier cluster inventory screen, another deployment
button, another proprietary approval workflow, or another SaaS layer that
charges per application for wrapping primitives the ecosystem already
provides.

They need a better operating model.

Kubernetes is not valuable because it hosts containers. That is the least
interesting part of it. Kubernetes is valuable because it provides a
programmable reconciliation substrate: APIs, controllers, desired state,
observed state, status, ownership, policy, admission, events, and
continuous convergence.

That is the foundation platform engineering should be built on.

But much of the industry still treats platform engineering as sysadmin 2.0:
a hosting interface with different nouns. Pods instead of VMs. YAML instead
of tickets. Dashboards instead of control planes. Human approval flows
wrapped around systems that should be able to explain, enforce, and
reconcile intent directly.

Skaphos exists because that is not enough.

A real platform is not a place where workloads run. A real platform is a
system that encodes operational intent and continuously reconciles reality
toward that intent.

That intent includes where software may run, how it moves, what policy
must pass, who owns it, what changed, what approved it, what failed, what
is currently deployed, what should happen next, and how the system can be
recovered when everything else is degraded.

Those should not live in spreadsheets, tribal knowledge, screenshots, wiki
pages, disconnected CI jobs, or vendor-specific dashboards.

They should be explicit primitives. They should be APIs. They should be
observable. They should be auditable. They should be recoverable from
source-controlled state. They should be boring enough to operate and
powerful enough to matter.

Skaphos is a collection of open platform-control tools built around that
belief.

## Core thesis

Platform engineering is becoming control-plane engineering.

The job is no longer merely to provision infrastructure, operate clusters,
expose deployment paths, or answer tickets. The job is to define the
durable operating model of the software system and encode that model into
reusable, inspectable, policy-aware primitives.

A platform should not just answer:

```text
Can this application deploy?
```

It should answer:

```text
What is this application?
Who owns it?
What release exists?
Where is it allowed to run?
Where is it currently running?
What version is deployed per target?
What promotion path governs it?
What policy gates apply?
What change record authorized it?
What failure domain does it affect?
What reconciler acted on it?
What evidence exists?
What must happen next?
Can we recover this state from Git?
```

Those are platform questions. Treating them as external process, human
memory, or vendor UI state is the root failure.

## What Skaphos believes

### 1. Kubernetes is a control-plane substrate, not a hosting product

Its real power is the API machinery: declarative resources, controllers,
reconciliation loops, status, events, ownership references, admission, and
extensibility. A platform that hides all of that behind a generic portal
is usually discarding the most useful part of the system.

The goal is not to make everyone use raw Kubernetes. The goal is to build
higher-level APIs that preserve the control-plane model instead of
bypassing it.

### 2. Desired state belongs in Git

Every byte of intended platform and application state should be derivable
from a commit in a repository the organization controls. Runtime state may
be observed, indexed, cached, rendered, and summarized elsewhere, but the
source of truth must remain recoverable.

This rejects parameter overrides, invisible UI mutations, edit-live-resource
workflows, and ad hoc deployment changes that cannot be reconstructed
later.

Break-glass must exist, but it must be explicit, auditable, attributable,
and reconciled back to Git.

### 3. Operational concepts should be first-class primitives

A mature platform needs explicit primitives for `Application`, `Release`,
`Environment`, `Cell`, `Region`, `DeploymentTarget`, `SyncPlan`,
`SyncRun`, `Promotion`, `PromotionPolicy`, `FreezeWindow`, `HealthCheck`,
`Approval`, `AuditEvent`, `Ownership`, `ChangeReference`.

These are not UI labels. They are not wiki sections. They are not
spreadsheet columns. They are the operating language of the platform and
should be represented as durable objects with lifecycle, status, policy,
and history.

### 4. Topology is part of deployment state

Environment, region, cell, failure domain, active/active posture,
active/passive posture, cluster type, ingress path, and blast radius are
all part of the deployment model. A platform that cannot model topology
cannot safely answer basic operational questions.

For serious platforms, topology must be encoded directly into delivery,
policy, health, and audit.

### 5. Promotion is a control-plane concern

Promotion is not a CI job with better YAML. Promotion is the movement of a
release through an explicit topology under policy, approval,
freeze-window, health, and audit constraints.

A promotion system should know what is moving, from where, to where, why,
under which policy, with what evidence, and what is blocking it.
Promotion should create or mutate desired state in Git. It should not
become an invisible second source of truth.

### 6. Reconciliation must be explainable

A control plane that cannot explain its decisions is not trustworthy.

For every sync, promotion, policy decision, or mutation, the system
should be able to show input state, desired-state commit, rendered output,
policy result, actor, target, action taken, observed result, failure
reason, and audit event.

A platform should not merely say "failed." It should say what failed, why,
what was attempted, what evidence exists, and what the next safe action
is.

### 7. Audit is not an afterthought

Audit should not be reconstructed from log scraping, CI history, Slack
messages, or screenshots. Audit events should be structured, durable,
correlated, and emitted by the same systems that make control-plane
decisions.

The audit trail should answer what happened, who or what caused it, what
policy applied, what state changed, and what evidence supported the
decision.

### 8. Platforms should degrade read-only before they fail closed into blindness

A platform must remain useful when mutation paths are degraded. If Git
mutation, sync, promotion, or policy engines are unavailable, operators
should still be able to inspect application inventory, topology, live
state, desired state, health, drift, and audit history.

Read-only degradation is a feature. Blindness during failure is an
architectural bug.

### 9. Vendor pricing should not punish operational maturity

Charging organizations more because they model their applications clearly
is backwards. Application count should not become a pricing weapon. Fleet
size should not force teams into opaque proprietary control layers. Basic
operational correctness should not be held behind enterprise ransom
tiers.

Skaphos tools should be open where primitives matter and monetized where
enterprise value is genuinely additive: hosted operations, support,
integrations, compliance workflows, managed control planes, and
implementation help.

### 10. Tools should compose

A tool should do one important thing well, expose its state clearly, and
compose with other tools through durable APIs, files, events, or Git.

Skaphos is not a monolith. It is an ecosystem of focused
platform-control tools that can be adopted independently but are designed
around the same operating model.

## Product vision

Skaphos is building open tools for platform teams that operate
Kubernetes-based systems across multiple applications, clusters, regions,
environments, and failure domains.

The goal is not to replace every tool in the software delivery chain. The
goal is to define and implement the missing control-plane layer between
raw infrastructure and human process.

That layer should make platform state explicit, delivery explainable,
topology inspectable, policy enforceable, and recovery deterministic.

## Product pillars

### Inventory and understanding

Before a platform can control anything, it must understand what exists.
Skaphos tools should help answer what applications exist, where they are
defined, where they are deployed, who owns them, what clusters and
environments exist, what topology is intended, and what differs between
desired and observed state. Visibility comes before control.

### Deterministic structure

Platform work fails when structure is implicit. Repositories,
environments, templates, manifests, generated files, ownership metadata,
documentation, and automation hooks need consistent shape. Skaphos tools
should help platform teams create and preserve that shape without turning
every repository into a bespoke snowflake.

### Topology-aware delivery

Software does not deploy into a vacuum. It deploys into environments,
regions, cells, clusters, failure domains, ingress paths, identity
boundaries, policy scopes, and change windows. Skaphos delivery tooling
should model that topology directly and use it to drive promotion,
synchronization, health, and audit.

### Git-native control

Git remains the durable record of intended state. Skaphos tools may read
from clusters, APIs, registries, CI systems, and event streams, but
intended state must round-trip through Git before it becomes normal
desired state. This keeps recovery simple, audit grounded, and
control-plane behavior explainable.

### Operator-grade UX

The UI should not be a toy view over Kubernetes objects. It should show
intent. An operator or developer should be able to see the platform as
the organization understands it: applications, releases, environments,
cells, deployment targets, promotions, policy gates, health, drift, and
blockers. Reduce cognitive load without hiding the truth.

### Audit and evidence

Every meaningful platform action should produce evidence. Promotion,
approval, sync, policy evaluation, Git mutation, health evaluation,
break-glass action, and rollback should emit structured events that can
be correlated and exported. Audit should be part of the architecture, not
a compliance garnish added after the fact.

### Sane commercialization

Skaphos should be commercially viable without undermining the reason it
exists. The primitives should be open. Teams should be able to run the
tools themselves. The basic ability to understand and operate a platform
should not require paying rent to a proprietary control plane.

Commercial offerings should focus on hosted control planes, enterprise
support, implementation and migration assistance, policy and compliance
packs, SSO/RBAC integrations, audit exports, managed fleet visibility,
long-term event retention, enterprise connectors, and operational
assurance. The business model should reward adoption, not punish scale.

## What Skaphos is not

Skaphos is not a Kubernetes dashboard company.

Skaphos is not trying to hide Kubernetes behind a shallow portal.

Skaphos is not trying to become a CI system, registry, cloud provider,
observability platform, service mesh, secrets manager, or ticketing
system.

Skaphos is not trying to own every part of the delivery chain.

Skaphos is focused on the control layer that makes platform operations
explicit, deterministic, and explainable.

## Design principles

1. **Git is the durable desired-state boundary.**
2. **Topology is part of deployment state.**
3. **Promotion is a first-class workflow, not CI glue.**
4. **Policy must produce evidence.**
5. **Reconciliation must be explainable.**
6. **Every mutation must be auditable.**
7. **Read-only degradation is better than operational blindness.**
8. **Operators must be able to recover with Git and a CLI.**
9. **Application count should not be a pricing weapon.**
10. **Kubernetes-native does not mean Kubernetes-only UX.**
11. **Useful tools should compose rather than trap.**
12. **The platform model should outlive any single vendor.**

## Adoption in layers

**Level 1 — Visibility.** Help teams see what exists: inventory, topology
discovery, application mapping, drift visibility, ownership, basic
health. No control-plane mutation required.

**Level 2 — Standardization.** Help teams make structure consistent:
repository layout, templates, bootstrap flows, environment conventions,
generated documentation, platform metadata. Operational consistency
without full delivery ownership.

**Level 3 — Control.** Help teams operate delivery through explicit
control-plane primitives: promotion, policy gates, Git mutation, sync
planning, health verification, freeze windows, approval, audit, rollback.
The highest-value tier, earned through trust.

## Why this matters

The next generation of platform engineering will not be won by whoever
has the prettiest cluster dashboard.

It will be won by teams that can encode operational intent clearly,
reconcile it safely, explain it under pressure, and recover it when the
surrounding systems fail.

Skaphos exists to build tools for that version of platform engineering.

Not sysadmin 2.0. Not Kubernetes as expensive hosting.

Platform engineering as control-plane engineering. That is the line.
