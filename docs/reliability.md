# Reliability and safety

Autonomous delegation amplifies ordinary distributed-systems failure modes. Runtime must make work bounded, observable, and recoverable. These are design requirements; no guarantee is implemented yet.

## Failure model

Assume processes can stop between any two steps, connections can time out after remote work begins, messages can be delayed or duplicated, and dependencies can become unavailable. A timeout does not prove remote work stopped. Recovery must consult durable state and idempotency records.

## Required controls

| Control | Purpose | Contract to define |
|---|---|---|
| Deadline and TTL | Bound stale work and messages | Is deadline enforced at enqueue, start, and completion? |
| Retry policy | Recover transient failures | Which component retries, with what backoff and attempt limit? |
| Idempotency | Prevent duplicate side effects on repeated submission | Key scope, retention, and behavior on conflicting payload |
| Acknowledgement | Distinguish receipt from successful processing | What exact event does acknowledgement represent? |
| Dead-letter handling | Preserve work that cannot progress | Inspection, replay authorization, and retention |
| Lease or claim timeout | Recover tasks from failed workers | Lease renewal, fencing, and stale worker prevention |
| Backpressure | Protect runtime and participants from overload | Queue limits, rejection, and fairness behavior |
| Circuit breaking | Stop repeated calls to failing destinations | Scope, recovery probe, and operator controls |

## Delegation containment

Track causal depth and cumulative limits across one root operation. Per-call hop limits alone can miss broad fan-out. Proposed controls:

- Maximum delegation depth and message fan-out.
- Per-task, per-agent, and per-tenant rate and concurrency limits.
- Deadline propagation that never extends parent deadline by default.
- Token, compute, or monetary budgets where costs can be estimated.
- Loop and repeated-work detection using causal lineage and idempotency keys.
- Explicit policy for whether child tasks may create more child tasks.

Detection is not proof of malicious behavior; controls should produce explainable deny, defer, or review outcomes.

## Task state integrity

Persist state transitions with actor, timestamp, and reason. Define legal transitions and reject stale updates. A worker crash after side effect but before completion report is a key case: retries need application-level idempotency or compensation strategy.

## Recovery and operations

Operators need to inspect stuck tasks, retry or cancel with authorization, inspect dead letters, and understand duplicate suppression. Manual replay must be auditable and must preserve original causal links while recording replay identity.

## Guarantees to publish

Before production use, document per-pattern durability, ordering scope, duplicate behavior, retention, delivery visibility, and failure recovery. Do not state “exactly once” unless end-to-end side effects can actually be covered; infrastructure deduplication alone cannot ensure it.
