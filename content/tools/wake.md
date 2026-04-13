---
title: "Wake"
weight: 70
tagline: "Evidence-backed repository forensics and ownership analysis"
status: "In design"
statusClass: "status-active"
summary: "Wake analyzes Git history and repository evidence to produce inspectable conclusions about ownership, evolution, and contributor behavior."
repo: "https://github.com/skaphos/wake"
module: "github.com/skaphos/wake"
---

Wake is a repository forensics and contributor behavior analysis system.

It reads Git history and related repository evidence, extracts normalized events, and produces evidence-backed summaries of repository evolution, ownership concentration, role patterns, and documentation alignment.

## Design principles

- Evidence first, interpretation second.
- Confidence-scored conclusions rather than anecdotal summaries.
- Read-only inspection by default.
- Support for both system-health analysis and contributor-level ownership context.
