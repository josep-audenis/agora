# ADR-0001: Agora is a communication and coordination runtime

## Status

Accepted as project scope

## Date

2026-10-18

## Context

Project brief defines Agora as shared communication infrastructure for independent agents. It identifies discovery, messages, asynchronous work, events, reliability, identity, and tracing as infrastructure concerns. Agent execution is expected to remain inside independently chosen frameworks and services.

The project needs a boundary that keeps its first release focused and prevents Agora from becoming an LLM framework, mandatory workflow engine, or closed agent protocol without clear need.

## Decision

Define Agora as an open-source communication and coordination runtime for autonomous agents and related software participants. Agora may provide discovery, routing, durable communication/task state, policy enforcement, and observability. Participant applications own model choice, prompts, reasoning, memory, and domain execution.

Central orchestration may be used by applications but is not required by Agora’s model. Integrate with external standards where they fit; do not claim protocol support until implemented and validated.

## Alternatives considered

### Agent framework

Rejected as core scope. Frameworks manage agent execution and reasoning; making that the center would narrow interoperability and duplicate existing ecosystems.

### Workflow engine

Rejected as core scope. Workflow engines remain useful integrations, but Agora’s primary abstraction is communication between independent participants rather than a centrally authored workflow graph.

### Protocol only

Insufficient as complete project definition. A wire protocol alone does not provide runtime persistence, routing, policy, recovery, or operational visibility. Agora may still adopt or bind to an existing protocol.

## Consequences

- Core contracts must be independent of specific agent frameworks.
- Runtime guarantees and protocol semantics must be documented separately.
- Initial architecture should prioritize a small deployable runtime with clear responsibilities.
- A2A, MCP, framework adapters, and workflow engines are integration boundaries, not automatic replacements for Agora.
- Stack, native protocol, delivery guarantees, deployment mode, and security mechanisms remain open and require separate decisions.

## References

- [Project vision](../vision.md)
- [Architecture overview](../architecture.md)
- [Open design questions](../open-questions.md)
