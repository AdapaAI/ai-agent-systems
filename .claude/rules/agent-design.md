# Agent Design Standards

Rules for writing agent `.md` files in Kythron.

## Frontmatter (required)

Every agent must have this frontmatter block:

```yaml
---
name: agent-name           # kebab-case, matches filename
description: one sentence  # what this agent does — used by orchestrator for routing
model: claude-sonnet-4-6   # default; use opus for complex reasoning, haiku for fast/cheap
tools:                     # only list tools the agent actually needs
  - Read
  - Bash
---
```

## System Prompt Rules

1. **First line states the job** — "You are X. Your job is to Y."
2. **Inputs section** — define exactly what the agent receives
3. **Outputs section** — define exactly what the agent returns, including format
4. **No ambiguity** — if the agent needs to make a decision, define the rules for that decision explicitly

## Tool Restrictions

Only grant tools the agent needs. Default restrictions:
- `fetcher-agent` — Bash only (runs scripts)
- `analyst-agent` — Read only (reads fetcher output)
- `reporter-agent` — Read, Write (reads analysis, writes dashboard)
- `orchestrator` — all tools (coordinates everything)

## Naming Conventions

- Agent files: `<function>-agent.md` (e.g. `fetcher-agent.md`)
- Skills: `<verb>-<noun>/SKILL.md` (e.g. `yfinance-fetch/SKILL.md`)
- Commands: `<verb>.md` (e.g. `analyze.md`)
- Tests: `.claude/tests/<agent-name>/`
- Evals: `.claude/evals/<agent-name>/`
