---
title: "Sting"
weight: 15
portfolio: "Adjacent Tools"
tagline: "Commit history, queryable by agents and terminals"
status: "Released"
statusClass: "status-released"
summary: "Sting queries a GitHub or GitLab user's commits over a time window and hands them to an LLM agent or a terminal in a consumable form."
repo: "https://github.com/skaphos/sting"
module: "github.com/skaphos/sting"
---

Sting turns provider commit history into something an agent or a human can actually consume: ask for an author's commits over a window, get a structured Markdown or JSON report.

It is a single binary. Run it directly for terminal reports, or run `sting mcp` to expose the same capability to agent runtimes as an MCP server over stdio.

## Core components

- Query CLI producing Markdown or JSON commit reports by author and time window.
- Repository activity digests (`sting activity`) summarizing a repository over a window without naming an author.
- MCP server exposing four read-only tools: `get_commits`, `get_repo_activity`, `get_prs`, and `get_pr_inbox`.
- OAuth authentication flows for GitHub and GitLab (`sting init`, `sting auth`).
- Agent-runtime registration (`sting install`) for Claude Code, Codex, OpenCode, and Grok.

## Design notes

- Read-only against providers; Sting never mutates repository state.
- Dedicated read-only tokens live in Sting's own configuration rather than relying on ambient provider credentials.
- Installable via the `skaphos/tools` Homebrew tap, `.deb` and `.rpm` packages attached to each release, or `go install`.
