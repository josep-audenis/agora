# Vision and scope

## One-sentence definition

Agora is an open-source communication and coordination runtime for independent AI agents and other software participants.

It gives participants shared infrastructure to discover capabilities, exchange structured messages, request or delegate work, publish events, and inspect outcomes. It should work across frameworks, languages, processes, and machines.

## Problem

Many multi-agent applications are fixed workflows owned by one process. One orchestrator starts every participant and passes each result to the next. This is simple at small scale, but couples participants to one application and execution graph.

Persistent or independently deployed agents need infrastructure questions answered:

- How does a participant find another participant and understand its capabilities?
- How can work continue when sender or receiver is offline?
- How are long-running tasks tracked, retried, cancelled, or inspected?
- How are duplicate work and runaway delegation contained?
- How are access, failures, latency, and cost traced across participants?
- How can agents from different frameworks communicate without sharing internals?

These are distributed-systems concerns around agent execution. Agora focuses on this shared layer.

## Intended users

- Developers connecting independently implemented agents.
- Teams operating agents across services or machines.
- Framework authors adding shared-runtime connectivity.
- Operators who need policy, reliability, audit, and trace visibility.

## Goals

1. Let independent participants register and advertise capabilities.
2. Support direct request/response and asynchronous communication.
3. Represent long-running work as inspectable task lifecycles.
4. Support event publication without sender-managed subscriber lists.
5. Preserve message lineage and task causality across agent boundaries.
6. Make reliability and safety controls part of the communication layer.
7. Interoperate with existing frameworks and protocols where practical.
8. Keep the initial runtime small enough to understand and operate.

## Non-goals

Agora does not aim to:

- Choose models, write prompts, perform reasoning, or manage agent memory.
- Replace agent frameworks such as LangGraph or an application’s own agent loop.
- Replace workflow engines such as Temporal, Dagster, or Prefect.
- Replace MCP’s tool and context integration role.
- Require a central planner to control every interaction.
- Promise autonomous behavior, agent quality, or safe outcomes by itself.
- Become a general-purpose broker for arbitrary application workloads.

These are scope boundaries, not claims that integration is impossible.

## Design principles

### Participants stay independent

An agent can run as a Python or TypeScript service, framework-managed process, deterministic service, local model, or remote system. Agora communicates with participants through stable contracts; it should not require shared process or framework internals.

### Communication is explicit

Messages and tasks have identity, sender/recipient context, lifecycle, and causal links. Model-generated text alone is not sufficient infrastructure metadata.

### Loose coupling is default

Participants should discover, request, publish, and subscribe without hard-coded execution graphs. Central orchestration remains valid when an application needs it.

### Safety is a system property

Routing and delegation need bounded depth, deadlines, quotas, idempotency, authorization, and observable failure paths. Model behavior is not a substitute for runtime controls.

### Standards before reinvention

Agora should reuse mature interoperability contracts where they fit. Its own value should come from runtime services and operational guarantees, not from creating a competing format without need.

## Success criterion

The first meaningful release should demonstrate independent agents built with different technologies communicating through a common runtime. The whole path must be inspectable: discovery, message exchange, task creation, failure or retry, and final result.

The first demo should show infrastructure value, not agent count. A planner, research agent, and deterministic risk service are enough if they use different execution models and communicate reliably.

## Current confidence

Project scope and boundaries are direction. Deployment topology, stack, protocol, persistence model, and exact delivery guarantees are open. See [open design questions](open-questions.md).
