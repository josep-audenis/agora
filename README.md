# Agora

**Communication infrastructure for autonomous agents.**

Agora is an open-source runtime for communication and coordination between independent agents. It aims to let agents discover capabilities, exchange messages, delegate long-running work, publish events, and inspect interactions across frameworks, processes, and machines.

Agora is in the definition and design stage. This repository currently contains project documentation, not a working runtime. Architecture sketches and roadmap items below describe direction, not shipped behavior.

## Why Agora

Agent systems often pass outputs through one application-owned workflow. That works for small, fixed pipelines. It becomes limiting when agents are persistent, asynchronous, independently deployed, or built with different frameworks.

Agora explores shared communication infrastructure for those systems. Agents remain independent participants; infrastructure handles discovery, routing, durable work, policy, and traceability.

## Project direction

- Treat agents as independent network participants.
- Make communication structured, attributable, and traceable.
- Support synchronous requests and asynchronous messaging, tasks, and events.
- Keep model choice, prompting, reasoning, and agent execution inside agent frameworks.
- Prefer interoperability with existing standards over a closed protocol.
- Put reliability and safety before large agent demos.

## Documentation

Start at [project wiki](docs/index.md). Key pages:

- [Vision and scope](docs/vision.md)
- [Core concepts](docs/concepts.md)
- [Architecture overview](docs/architecture.md)
- [Communication model](docs/communication.md)
- [Reliability and safety](docs/reliability.md)
- [Security model](docs/security.md)
- [Observability](docs/observability.md)
- [Interoperability](docs/interoperability.md)
- [MVP and roadmap](docs/roadmap.md)
- [Open design questions](docs/open-questions.md)
- [Decision records](docs/decisions/0001-runtime-scope.md)

## Current status

Agora is an experimental project. Initial goal: define and then build the smallest runtime that lets heterogeneous agents discover one another, communicate synchronously and asynchronously, and make each interaction observable.

No install, run, or test commands exist yet. Stack, wire contract, delivery guarantees, deployment model, and security mechanisms remain design choices. Track unresolved choices in [open questions](docs/open-questions.md); record costly-to-reverse decisions as [ADRs](docs/decisions/).

## License

See [LICENSE](LICENSE).
