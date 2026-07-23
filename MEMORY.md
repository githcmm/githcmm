# MEMORY.md

Running log of decisions, context, and state for this project, carried across Claude Code sessions. Read this file first at the start of every session. Append a new dated entry below at the end of a session or after any significant decision — newest entry at the bottom.

## Project

NinjaScript addon for NinjaTrader **version 8**. Built by a coordinated team of Claude Code subagents, defined one at a time by the user. The addon's internal design is also planned as multiple cooperating components (multi-agent architecture within the addon itself), not just a dev-team convention.

**Ultimate goal**: a NinjaTrader 8 addon/**strategy that auto-trades** - not just an indicator. The user has a large body of trade-system information (entry rules, candlestick patterns, stop/target logic, etc.) they will post, culminating in a "master prompt" that defines the actual trading system to implement. This trade-system spec (once posted) is the source of truth the agents check code against - not live chart observation, since this environment cannot run NinjaTrader itself.

## Agent roster (Claude Code subagents, `.claude/agents/*.md`)

- **nt8-researcher** - General NinjaScript/NinjaTrader 8 API, syntax, and conceptual research. Consults official NT docs (developer.ninjatrader.com/docs/desktop/ninjascript_editor_overview, ninjatrader.com/support/helpguides/nt8) and forums/GitHub instead of guessing from memory. Read-only (Read, Grep, Glob, WebFetch, WebSearch) - reports findings back for the main session to record, does not edit MEMORY.md/CLAUDE.md itself.
- **compile-error-fixer** - Takes a specific compiler error + code, researches the confirmed root cause against the same NT8 sources, and applies the fix directly. Tools: Read, Grep, Glob, Edit, Bash, WebFetch, WebSearch.
- **session-logger** - Writes/appends the dated Log entries in this file (and updates the roster/architecture sections when something structural changes). Tools: Read, Grep, Glob, Bash, Edit. Should be invoked at session end or after significant decisions.
- **chart-watcher** - Verifies implemented code matches the trade-system spec: indicator calculations, candlestick/price-action pattern detection (e.g. engulfing candles), order entry levels, initial stop-loss placement, target levels. Audits code logic (and any exported backtest/trade logs the user provides) against the trade-system spec - does not observe a live chart (no NinjaTrader instance in this environment). Tools: Read, Grep, Glob, Bash. Report-only, does not edit code (hands mismatches to compile-error-fixer or the user).
- **Coordinator/"director" role**: not a separate subagent. Only the main Claude Code session can dispatch to subagents (subagents can't call the Agent tool themselves), so the main session acts as coordinator - dispatching to the agents above, relaying user input, and verifying answers. Revisit this if the user wants a distinct QA/verifier subagent instead.
- More agents pending - user has indicated there are additional ones to define, and a master prompt with the full trade-system spec is coming.

## Addon internal architecture (design-in-progress)

_Not yet decided. Placeholder — the addon is expected to split responsibilities across internal components (e.g. signal generation, risk management, order execution) rather than one monolithic class. Update this section once the user and the team agree on the concrete design._

## Log

### 2026-07-22
- Repo was empty (default GitHub profile README only).
- User's plan: build a NinjaScript v8 addon; wants both (a) a team of Claude Code subagents to help develop it, and (b) the addon itself to have an internal multi-agent architecture.
- Created `CLAUDE.md` and this `MEMORY.md` for cross-session continuity, per user request.
- Next: user will supply agent skills/roles one at a time for the dev-team subagents; then scaffold the actual NinjaScript project structure.

### 2026-07-23
- Created first three dev-team subagents in `.claude/agents/`: `nt8-researcher`, `compile-error-fixer`, `session-logger` (see Agent roster section above for details).
- User originally described nt8-researcher and compile-error-fixer identically; split them by scope (general research vs. specific compiler-error diagnosis+fix) since the user approved building both.
- User also described a 4th "director" role (coordinates the team, verifies answers, takes input from the user). Decided this is the main session's job, not a subagent, since subagents here can't dispatch other subagents - documented as the Coordinator entry above. Not yet explicitly confirmed by the user; revisit if they want a dedicated QA/verifier subagent instead.
- User has more agents to define; expect this roster to grow.
- Next: await further agent definitions from the user; still no NinjaScript project scaffold yet.
- Created 4th subagent `chart-watcher` (see roster above) - verifies indicator/pattern/entry/stop/target logic in code against the trade-system spec, since this environment can't run NinjaTrader to observe a live chart.
- User clarified the bigger picture: this is ultimately a NinjaTrader 8 **auto-trading strategy**, not just an indicator. User has a large amount of trade-system information to post, culminating in a "master prompt" defining the trading system - that spec is what chart-watcher (and the team generally) will check code against.
- Next: await the master prompt and remaining agent definitions; no NinjaScript project scaffold yet.
