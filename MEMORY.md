# MEMORY.md

Running log of decisions, context, and state for this project, carried across Claude Code sessions. Read this file first at the start of every session. Append a new dated entry below at the end of a session or after any significant decision — newest entry at the bottom.

## Project

NinjaScript addon for NinjaTrader **version 8**. Built by a coordinated team of Claude Code subagents, defined one at a time by the user. The addon's internal design is also planned as multiple cooperating components (multi-agent architecture within the addon itself), not just a dev-team convention.

## Agent roster (Claude Code subagents, `.claude/agents/*.md`)

_None defined yet. The user will provide each agent's skill/role one at a time. As each is added, record here: name, responsibilities, tools/access, and how it hands off to the others._

## Addon internal architecture (design-in-progress)

_Not yet decided. Placeholder — the addon is expected to split responsibilities across internal components (e.g. signal generation, risk management, order execution) rather than one monolithic class. Update this section once the user and the team agree on the concrete design._

## Log

### 2026-07-22
- Repo was empty (default GitHub profile README only).
- User's plan: build a NinjaScript v8 addon; wants both (a) a team of Claude Code subagents to help develop it, and (b) the addon itself to have an internal multi-agent architecture.
- Created `CLAUDE.md` and this `MEMORY.md` for cross-session continuity, per user request.
- Next: user will supply agent skills/roles one at a time for the dev-team subagents; then scaffold the actual NinjaScript project structure.
