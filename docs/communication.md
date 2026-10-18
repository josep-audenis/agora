# Communication model

Agora should support several communication patterns through shared identity, policy, correlation, and observability rules.

## Request and response

Use when caller needs an answer before proceeding. Recipient may return result, error, or a handle to work that continues asynchronously. Requests need deadline, caller identity, recipient identity or capability, and correlation context.

## Direct message

Use when sender communicates information without requiring immediate result. Recipient may be offline. Mailbox persistence, acknowledgement, ordering, expiry, and retention are design decisions, not guarantees yet.

## Asynchronous task

Use for work that may outlive request connection or process. Task has creator, assignee, state, timestamps, deadline, parent context, and result/failure references. Caller can inspect or receive updates later.

Expected lifecycle:

`created → queued → assigned → running → completed | failed | cancelled | expired`

Exact states and legal transitions must be defined before an API is stable. Cancellation is a request to stop; it cannot guarantee rollback of side effects already performed.

## Channels and publish/subscribe

Use when publisher should not manage recipient list. A channel can have multiple publishers and subscribers. Runtime policy governs publish and subscribe permissions. Replay, per-subscriber offsets, ordering, fan-out limits, and delivery acknowledgement remain open.

## Artifacts

Use references for large, durable, or independently managed outputs. Artifact metadata should include owner, media type, creation time, integrity information, access policy, and retention. Do not make an artifact URL public merely because it appears in a message.

## Common envelope requirements

Exact schema is open. Any stable envelope should carry or reference:

- Stable operation ID and message/task kind.
- Authenticated sender and destination or channel.
- Creation time, deadline/expiry, and priority when relevant.
- Conversation, correlation, parent-message, task, and trace links as applicable.
- Typed payload or artifact references.
- Idempotency key where retries can repeat side effects.
- Protocol/schema version and content type.

## Delivery contract

“Sent” must have one precise meaning. Distinguish accepted by API, durably recorded, routed, received, acknowledged, and processed. Retries can create duplicates unless deduplication spans the relevant boundary. Define guarantees per communication pattern; do not promise generic exactly-once execution.

## Streaming

Streaming can expose progress and partial results for a request or task. It must preserve final state retrieval after stream disconnect. Backpressure, resume, ordering, and partial-output retention need explicit contracts.

## Versioning

Version external contracts independently from runtime release. Define compatibility rules, unknown-field behavior, deprecation window, and negotiation before publishing stable SDKs or protocol bindings.
