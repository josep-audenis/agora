# Security model

Security is foundational because participants can initiate work and select destinations. This page records required questions and boundaries, not a completed threat model or implemented control set.

## Security objectives

- Authenticate every remote participant and operator.
- Authorize registration, discovery, send, publish, subscribe, task operations, artifact access, and administration separately.
- Isolate tenants and prevent one participant from reading another’s messages or task results without policy grant.
- Make policy decisions and administrative actions auditable.
- Protect credentials and sensitive payloads in transit, at rest, in logs, and in traces.
- Bound abuse of compute, storage, fan-out, and external destinations.

## Trust boundaries

1. Agent process to Agora API.
2. Agora control functions to queues, databases, and artifact storage.
3. Agora to remote or external agents.
4. Tenant boundary inside shared runtime.
5. Operator console and administrative API.

Each boundary needs explicit identity propagation and least-privilege policy. A participant’s declared name or capability is metadata, not proof of identity or trustworthiness.

## Threats to design against

- Compromised or malicious agent sends unauthorized requests or floods channels.
- Spoofed identity or stale registration redirects work.
- Confused deputy: runtime uses its own broad credentials for agent-requested action.
- Cross-tenant message, task, trace, or artifact disclosure.
- Replay, duplicate task creation, or forged completion update.
- Prompt injection or untrusted payload influences another participant.
- Artifact references expose private data or allow unsafe content retrieval.
- Excessive delegation increases cost or exhausts queue capacity.
- External callback or endpoint validation creates server-side request forgery risk.
- Logs and traces retain secrets, personal data, or confidential prompts.

## Required design rules

- Separate identity from capabilities and liveness.
- Apply authorization at destination and operation boundary, not only at registration.
- Pass delegated credentials with narrow scope and explicit expiry; avoid ambient runtime credentials.
- Scope task, trace, artifact, and mailbox reads to principal and tenant.
- Validate payload size, schema, content type, expiry, and routing target.
- Treat external endpoints and artifacts as untrusted; define egress controls before remote callbacks.
- Redact secrets and define retention/deletion rules for payload-bearing telemetry.
- Require explicit operator access paths; record administrative reads and mutations.

## Identity model

Source vision proposes names such as organization-scoped agent URIs. Naming syntax, issuer, key lifecycle, authentication mechanism, rotation, federation, and proof-of-possession are open. A stable logical agent identity must not be reused as a bearer secret.

## Baseline versus later scope

Authentication, tenant scoping, authorization checks, and safe payload handling are prerequisites for any remotely accessible release. Later security milestones may add federation, signed messages, organization networks, and richer policy management; they cannot postpone basic protections.

See [open design questions](open-questions.md) for choices that need ADRs before implementation.
