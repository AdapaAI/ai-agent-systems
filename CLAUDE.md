# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Technical debt orchestration system — a multi-agent platform that scans codebases for debt, reviews code quality, and generates actionable refactoring recommendations. The project is in early development; no build tooling or language has been committed to yet.

## Repository Structure

- `agents/codebase-improvements/` — Source of per-file improvement suggestions (tabular data, 3PP REST API, or internal analysis)
- `agents/code-reviewer/` — Automated code review for style, security, and maintainability
- `agents/solution-designer/` — Reads per-file improvements, consults CLAUDE.md for standards and architecture, and uses skills to implement the required code changes
- `agents/git-agent/` — Handles git operations (branching, committing, opening PRs)
- `skills/commit-message/` — Generates structured conventional commit messages from diffs
- `skills/code-review/` — Performs inline code review, returns structured feedback
- `orchestrator/` — Orchestration logic coordinating all agents and skills
- `docs/` — Project documentation

## Notes

- No build system, test runner, or language toolchain is configured yet. Add relevant commands here once a stack is chosen.
