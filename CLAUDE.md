# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Kythron is a general-purpose multi-agent platform built natively on Claude Code. It provides a structured home for subagents, shared skills, commands, and orchestration logic. Agents are independent and can serve any domain.

## Repository Structure

```
kythron/
├── CLAUDE.md                    ← you are here
├── README.md
└── .claude/
    ├── settings.json
    ├── agents/                  ← one .md file per agent
    ├── skills/                  ← reusable capabilities agents invoke
    ├── commands/                ← custom slash commands
    ├── rules/                   ← platform-wide standards and constraints
    ├── memory/                  ← persistent feedback loops per agent
    ├── tests/                   ← functional correctness tests per agent
    └── evals/                   ← quality measurement per agent
```

## Orchestration

The `orchestrator` agent (`.claude/agents/orchestrator.md`) is the entry point. It routes tasks to subagents, manages multi-step workflows, and handles retries and fallbacks.

## Adding a New Agent

1. Create `.claude/agents/<agent-name>.md` with frontmatter (name, description, model, tools) and a system prompt
2. Register the agent in `orchestrator.md` under Available Agents
3. Add routing logic in `orchestrator.md`
4. Create test cases in `.claude/tests/<agent-name>/`
5. Add evals in `.claude/evals/<agent-name>/`

## Notes

- No build system or language toolchain is configured yet. Add relevant commands here once a stack is chosen.
