# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This repository is in its initial planning phase for a **NinjaScript addon targeting NinjaTrader 8**. As of now there is no source code — only this guidance file, `MEMORY.md`, and the default profile `README.md`. There are no build, lint, or test commands yet because no project has been scaffolded. Once the addon's C#/NinjaScript project is created, this file must be updated with the real build/lint/test commands and the actual architecture (NinjaScript component layout — Indicators/Strategies/AddOns, how they compile inside NinjaTrader, project references, etc.).

## Persistent memory

`MEMORY.md` in the repo root is the running log of decisions, agent definitions, and in-progress work carried across sessions. Every Claude Code instance working in this repo must:

1. Read `MEMORY.md` at the start of the session before starting new work.
2. Append a dated entry to `MEMORY.md` at the end of the session (or after any significant decision) summarizing what changed and what's next — do not silently let context be lost between sessions.
3. Keep `MEMORY.md` factual and current — correct or remove stale entries rather than letting contradictions accumulate.

## Development team (Claude Code subagents)

This project uses a team of custom Claude Code subagents (to be defined in `.claude/agents/*.md`) that collaborate on building the addon — e.g. a NinjaScript API specialist, a C#/.NET reviewer, a backtesting/strategy analyst, etc. Each agent's role, responsibilities, and tool access are recorded in `MEMORY.md` as they are defined. Check there for the current roster before assuming an agent doesn't exist yet.

## Addon architecture (planned)

The addon itself is being designed as multiple cooperating components internally (e.g. signal generation, risk management, order execution as separate NinjaScript classes/objects rather than one monolithic strategy). The concrete design is still being worked out with the user — check `MEMORY.md` for the latest agreed architecture before assuming a structure.

## Working branch

Active development happens on `claude/ninjascript-v8-agents-78520u`.
