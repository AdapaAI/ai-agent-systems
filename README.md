# Kythron

A general-purpose multi-agent platform built natively on Claude Code. Kythron provides a structured, opinionated home for subagents, shared skills, slash commands, and orchestration logic — designed to scale across any domain.

## Structure

| Folder | Purpose |
|--------|---------|
| `.claude/agents/` | One `.md` file per agent — system prompt, model, tool permissions |
| `.claude/skills/` | Reusable capabilities agents invoke |
| `.claude/commands/` | Custom slash commands |
| `.claude/rules/` | Platform-wide standards and constraints |
| `.claude/memory/` | Persistent feedback loops per agent |
| `.claude/tests/` | Functional correctness tests per agent |
| `.claude/evals/` | Quality measurement per agent |
