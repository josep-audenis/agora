# Interoperability

Agora should connect heterogeneous agent systems while avoiding unnecessary protocol fragmentation. It has two separate jobs to consider: runtime services for a network and wire contracts that let independent systems communicate.

## Relationship to A2A

[Agent2Agent (A2A)](https://a2a-protocol.org/latest/specification/) defines an open interoperability protocol for independent agent systems. Its current specification covers agent discovery, messaging, tasks, streaming/update delivery, artifacts, protocol bindings, and security considerations.

Agora’s intended emphasis is runtime operation: registration and routing within a network, durable coordination, policy, reliability controls, and cross-agent observability. These responsibilities overlap at boundaries. Agora must not assume A2A lacks task or discovery concepts.

Open choice: implement Agora-native contracts, expose A2A bindings, use A2A internally, or combine approaches. Compare semantic fit, conformance cost, compatibility, security, and ability to preserve Agora runtime guarantees before deciding.

## Relationship to MCP

[Model Context Protocol (MCP)](https://modelcontextprotocol.io/specification/2026-07-28) standardizes interactions between host/client applications and servers that expose context and capabilities, including tools, resources, and prompts. MCP also evolves; verify current core specification and extensions before implementation.

Agora focuses on communication and coordination between participants. MCP can expose an Agora runtime to an agent as tools/resources, or an Agora adapter can connect an MCP-enabled system. MCP is not a replacement target, and Agora should not claim MCP cannot represent asynchronous or task-oriented behavior.

## Relationship to frameworks

Framework adapters should translate at boundary while leaving framework-specific execution inside participant. Adapter must preserve identity, deadlines, task state, errors, trace context, and cancellation semantics where possible. It must clearly report any semantics it cannot preserve.

## Compatibility principles

- Keep protocol bindings separate from runtime guarantees.
- Prefer adapters over framework-specific core behavior.
- Version schemas and document compatibility windows.
- Preserve unknown metadata where safe and defined.
- Build conformance cases against independent implementations.
- Re-check official sources and versions when work begins; protocols change.

## Reference freshness

Links above point to current official specifications as of documentation review on 2026-10-18. Protocol versions and extension status can change. These links describe external standards; they do not imply Agora has selected or implemented support.
