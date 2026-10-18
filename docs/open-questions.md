# Open design questions

These choices affect contracts, operations, security, or data migration. Resolve with prototypes or comparison before locking implementation. Add an ADR when a choice becomes accepted.

## Runtime and deployment

1. Is initial Agora single-tenant, multi-tenant, or local-first with later hosted mode?
2. Is first deployment one process, one service plus dependencies, or a library/embedded runtime?
3. Which language/runtime is primary? Source names Python and FastAPI as candidates.
4. Which persistence and queue technologies meet durability, ordering, and recovery needs with least operational burden? Redis/Redis Streams and PostgreSQL are candidates, not selected.
5. What is minimum supported deployment: local development, self-hosted single node, or managed multi-node?

## Contract and interoperability

6. Does Agora define native protocol, adopt A2A as wire contract, or expose one or more bindings?
7. Which entities belong in stable public model versus implementation metadata?
8. Is destination normally participant ID, capability query, or both? How are ambiguous matches handled?
9. Which SDK ships first, and how will first demo prove heterogeneous operation?
10. What versioning and compatibility guarantees apply to SDK, runtime API, and protocol?

## Delivery and task semantics

11. What exactly counts as accepted, delivered, acknowledged, and completed?
12. What durability and ordering guarantees apply to mailbox, channel, request, and task paths?
13. Who owns retry and how are worker leases, fencing, and stale completions handled?
14. What is retained after task completion, and for how long?
15. How do streaming, resume, cancellation, partial outputs, and artifacts behave?

## Identity, policy, and trust

16. Who issues participant identities? How does local identity map to external A2A identities?
17. Which authentication mechanisms must first release support?
18. How are permissions expressed and evaluated across sender, recipient, channel, task, artifact, and tenant?
19. What is tenant boundary and is deployment allowed to host mutually untrusted organizations?
20. How will participant capability claims be validated or rated?

## Operations and product

21. Which console actions are MVP versus later control-plane work?
22. Is token/cost telemetry core, adapter-provided, or optional metadata?
23. What are initial scale targets for registered agents, messages, fan-out, task duration, and retention?
24. Which minimum SLOs matter for local and hosted operation?
25. What documentation, conformance suite, and recovery tooling are required for first production use?

## Conflicts in source roadmap

Original brief lists both Python and TypeScript SDKs under MVP, then places TypeScript SDK in release 0.4. It also lists a console under MVP, then places console work in 0.3. This wiki preserves both directions and leaves release boundaries open. Decide after MVP proof and operator needs are clearer.

## Resolution rule

For each question: name owner, list alternatives, test constraints, record outcome and consequences in ADR if costly to reverse. Keep status as **Open** until decision is recorded. Do not silently turn architecture sketches into commitments.
