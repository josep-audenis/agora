# MVP and roadmap

Roadmap records intended order, not delivery dates or promises. Scope can change through evidence and documented decisions.

## First proof

Prove one claim: independently implemented agents using different technologies can communicate through one common runtime, continue work asynchronously, and leave enough trace data to explain outcome.

First demo can use planner, research agent, and deterministic risk service. Demonstration should show discovery, request/response, delegated task, event or message, artifact result, and trace inspection. Do not optimize for many agents.

## MVP capabilities

| Capability | MVP outcome |
|---|---|
| Registry | Participants register, heartbeat, advertise capabilities, and discover eligible participants |
| Direct communication | Sender can address participant and inspect delivery outcome |
| Request/response | Caller can receive result, error, or task handle |
| Events | Publisher can publish to channel; authorized subscribers can receive |
| Async tasks | Create, dispatch/claim, run, complete, fail, cancel, and inspect task |
| Basic resilience | Deadlines, bounded retries, idempotency, and inspectable failed work |
| Traceability | One trace can connect cross-agent communication and task lifecycle |
| Client access | At least one SDK plus documented interoperable boundary; exact SDK sequence open |
| Console | Inspect agents, messages, tasks, and traces if console is included in first release |

## Release sequence

### 0.1 — Core communication

Registry and discovery, direct messaging, request/response, durable history, initial client SDK, and basic traces. First release must prove heterogeneous participation. Python/FastAPI, Redis, and PostgreSQL remain candidates, not requirements.

### 0.2 — Asynchronous runtime

Mailboxes, tasks, channels/pub-sub, lifecycle updates, timeouts, bounded retries, and dead-letter inspection.

### 0.3 — Observability and console

Trace viewer, communication graph, task/message inspection, latency and error metrics, and optional token/cost estimates.

### 0.4 — Interoperability

Second SDK, framework adapters, external protocol support, and compatibility/conformance guidance. TypeScript SDK appears in original direction; its exact release boundary remains open.

### 0.5 — Reliability controls

Idempotency coverage, rate and concurrency limits, budgets, TTLs, loop controls, circuit breakers, and backpressure.

### 0.6 — Expanded security

Organization boundaries, policy administration, signed messages or registration metadata, and federation. Basic authentication, authorization, tenant isolation, and secret handling must exist earlier for any networked release.

### 1.0 — Stable runtime

Publish stable protocol/API compatibility policy, operational guarantees, supported deployment model, upgrade guidance, security model, and production recovery procedures. “1.0” requires documented semantics more than feature count.

## MVP acceptance questions

Before calling MVP complete, decide and demonstrate:

- What does successful send mean: accepted, durably committed, delivered, or processed?
- Which failures trigger retry, who retries, and when does retry stop?
- How does task owner recover after worker crash?
- How do independently built participants authenticate and receive permission?
- Can operator follow one task across participants without reading prompt content?
- Does sample system keep working if a participant restarts or temporarily disconnects?

Track decision work in [open questions](open-questions.md). See [architecture](architecture.md) for component responsibilities.
