# Core concepts

This page defines vocabulary for design discussions. Terms describe intended concepts; they are not yet wire schemas or implemented entities.

| Term | Meaning | Boundary |
|---|---|---|
| **Participant** | Addressable actor in Agora network: agent, deterministic service, or later human endpoint | A participant may have several running instances |
| **Agent** | Software participant that performs agentic work | Agora does not define its model or reasoning loop |
| **Instance** | One live process or connection for a registered participant | Presence is operational state, not identity |
| **Identity** | Stable name and authority context for a participant | Authentication proves identity; authorization decides allowed actions |
| **Capability** | Declared kind of work a participant can perform | Capability discovery does not guarantee quality or availability |
| **Message** | One communication envelope between participants or through a channel | A message can report information without creating work |
| **Request** | Message that asks recipient to perform an operation and return a result | Usually has caller-visible completion or failure |
| **Task** | Durable representation of requested work with owner, state, and lifecycle | A task can outlive request connection or participant process |
| **Event** | Published fact that interested subscribers may consume | Publisher need not know every subscriber |
| **Mailbox** | Durable, address-scoped queue or history for a participant | Exact retention and acknowledgement semantics remain open |
| **Channel** | Named event stream for multiple publishers or subscribers | Subscription delivery and replay semantics remain open |
| **Artifact** | Durable result such as report, dataset, image, or file | Messages should reference large or durable payloads instead of embedding them by default |
| **Conversation** | Related exchange of messages among participants | Conversation groups discussion; it does not itself define executable work |
| **Trace** | End-to-end record of causally related operations | Trace spans can cross requests, tasks, and agents |
| **Correlation ID** | Identifier joining operations that belong to one broader activity | Correlation groups activity; parent links preserve direct causality |

## Message versus task

Use message when meaning is “communicate this information.” Use task when meaning is “perform this work and track its outcome.” A task may create messages and events; messages can reference a task or artifact.

## Capability versus task type

Capability describes what participant offers. Task type describes requested work instance. Multiple participants may advertise same capability; one capability may accept several task types. Naming and matching rules remain open.

## Identity, presence, and endpoint

Stable identity should survive process restart. Presence describes current availability. Endpoint describes how runtime reaches an active instance. These concepts must remain separate so registry data does not confuse “who this is” with “where it is now.”

## Causality fields

Future envelopes should preserve enough lineage to answer:

- Who initiated this operation?
- Which message or task caused it?
- Which trace contains it?
- Which deadline or budget applies?
- Which policy decision permitted or denied it?

Exact field names and representation belong in protocol design, not in this glossary.
