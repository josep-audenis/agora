# Agora project wiki

Agora is communication infrastructure for autonomous agents. This wiki defines project purpose, vocabulary, intended behavior, proposed architecture, and unresolved design work.

## Read by topic

### Project

- [Vision and scope](vision.md) — problem, goals, non-goals, principles
- [Core concepts](concepts.md) — shared vocabulary and entity boundaries
- [MVP and roadmap](roadmap.md) — first proof and staged growth
- [Open design questions](open-questions.md) — choices needing evidence or an ADR

### System design

- [Architecture overview](architecture.md) — logical components and boundaries
- [Communication model](communication.md) — messages, requests, tasks, channels, artifacts
- [Reliability and safety](reliability.md) — delivery, retries, loops, limits, failure handling
- [Security model](security.md) — identity, access, trust boundaries, threats
- [Observability](observability.md) — traces, inspection, metrics, privacy
- [Interoperability](interoperability.md) — relationship to A2A, MCP, and agent frameworks

### Decisions

- [ADR-0001: Agora is a communication and coordination runtime](decisions/0001-runtime-scope.md)

## How to read status labels

- **Direction** — project intent stated in source brief.
- **Proposed** — design shape worth evaluating; implementation choice remains open.
- **Open** — no decision yet. Do not treat page wording as a commitment.
- **Future** — outside first release unless scope changes.

Pages describe target behavior, not existing features. Update related pages and ADRs when a decision changes. Keep unresolved alternatives visible until evidence supports a choice.

## Project snapshot

| Area | Current state |
|---|---|
| Product | Early definition and design |
| Runtime | Not implemented |
| Protocol/API | Not specified |
| Stack | Open |
| First release | Scope described; acceptance details open |
| Documentation source | This repository |
