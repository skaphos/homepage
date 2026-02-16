---
title: "Repokeeper"
tagline: "Repository collections as explicit operational state"
status: "Implemented and released"
statusClass: "status-released"
summary: "Repokeeper manages and safely synchronizes repository collections as explicit operational state."
repo: "https://github.com/skaphos/repokeeper"
module: "github.com/skaphos/repokeeper"
---

Repokeeper manages collections of Git repositories across machines and directory layouts.

It provides structured repository inventory, health reporting, and safe synchronization as a unit.

## Core responsibilities

- Clone repository sets.
- Synchronize repositories safely.
- Maintain consistent repository structure across machines.
- Manage repository collections as explicit operational state.

## Safety model highlights

- Safe default sync behavior via fetch and prune.
- Does not reset, checkout, or mutate working trees in default flows.
- Designed to operate safely with dirty working trees.

## Core commands

- `repokeeper init`
- `repokeeper scan`
- `repokeeper status`
- `repokeeper sync`
- `repokeeper describe`
