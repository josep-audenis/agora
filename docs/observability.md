# Observability

Agora should make agent interactions inspectable without exposing more content than necessary. Every accepted operation should be traceable across runtime and participant boundaries.

## Trace model

Use a root trace for a user goal or initiating operation. Link child requests, messages, tasks, retries, policy decisions, and artifacts by causal parentage. Preserve trace context when execution continues asynchronously or crosses participant process boundaries.

At minimum, an operator should be able to answer:

- Which participant initiated this work?
- Which messages and tasks led to final result?
- Where did time go, and which operation failed or retried?
- Was action allowed, denied, or deferred by policy?
- Which participant received work, and did it acknowledge or finish?
- What cost or resource use is known, and how was it estimated?

## Signals

| Signal | Useful fields |
|---|---|
| Traces | trace and span IDs, parent links, participant IDs, operation kind, outcome, duration |
| Metrics | queue depth, task age, delivery latency, retry rate, failure rate, resource use |
| Audit events | principal, action, resource, policy outcome, timestamp, actor and request IDs |
| Content history | message/task metadata and optionally payload under retention policy |

OpenTelemetry is a candidate integration from source brief, not a chosen dependency. Preserve trace semantics even if another SDK or exporter is selected.

## Console direction

First console scope should focus on agents, messages, tasks, and traces. Operators need filtering, causal navigation, state inspection, and authorized retry/cancel actions. Console should not become a prompt IDE or workflow builder by default.

## Privacy and retention

Payloads may contain secrets or user data. Separate operational metadata from content retention; provide configurable retention and deletion behavior. Redact credentials and sensitive values before export. Keep access to conversation content more restricted than access to aggregate health metrics.

Token and cost reporting is useful but approximate. Record source and confidence of estimates; do not present estimated spend as billing truth.
