CSP-0010 — Snapshot Transport Format (STF)

Document ID: CSP-0010
Title: Snapshot Transport Format (STF)
Status: Draft
Version: 0.1.0
Category: Normative Specification

⸻

1. Abstract

This specification defines the canonical transport format for CYSSI Snapshots.

Its purpose is to guarantee deterministic and lossless transmission of canonical project states between humans, Large Language Models (LLMs), software tools, repositories and future CYSSI Builder implementations.

This specification governs only the transport of snapshots and does not define the snapshot structure itself.

⸻

2. Motivation

Large Language Models frequently interpret plain text semantically.

During normal conversation they may:

* modify indentation,
* collapse whitespace,
* reflow paragraphs,
* alter formatting,
* merge or split lines,
* reconstruct instead of reproducing.

Such modifications prevent deterministic replay and reliable parser implementations.

A standardized transport format ensures that snapshots remain immutable during transmission.

⸻

3. Scope

This specification applies whenever a canonical CYSSI Snapshot is exchanged between:

* Human ↔ AI
* AI ↔ AI
* Human ↔ Software
* Software ↔ Software

This specification does not define the internal snapshot schema.

⸻

4. Terminology

Snapshot

A canonical representation of the complete or partial project state.

⸻

Transport

The act of transferring a snapshot from one system to another.

⸻

Transport Format

The external representation used during transport.

⸻

Fenced Code Block

A Markdown code block enclosed by triple backticks.

Example:

```yaml
snapshot:
  id: S0021
```

⸻

5. Specification

STF-001

Canonical Snapshots SHALL be transported as exactly one fenced Markdown code block.

⸻

STF-002

The language identifier SHALL be:

yaml

Example:

```yaml
...
```

⸻

STF-003

The complete snapshot SHALL be contained inside the fenced code block.

No snapshot content SHALL exist outside the block.

⸻

STF-004

The snapshot content SHALL be transmitted without semantic modification.

Transport systems SHALL reproduce the snapshot exactly as received.

⸻

STF-005

Whitespace, indentation, ordering and line structure SHALL be preserved.

⸻

STF-006

Transport systems SHALL NOT:

* rewrite
* summarize
* optimize
* reformat
* normalize
* reorder
* reconstruct

the snapshot during transport.

⸻

STF-007

Transport systems MAY validate snapshot syntax after extraction.

Validation SHALL NOT modify snapshot content.

⸻

STF-008

Snapshot identifiers, Decision identifiers, Locked Facts and Project History SHALL remain unchanged during transport.

⸻

STF-009

Transport formatting SHALL be considered external representation only.

It SHALL NOT become part of the canonical snapshot itself.

⸻

6. Rationale

Using a fenced yaml code block provides several advantages:

* deterministic LLM behaviour
* preservation of indentation
* parser compatibility
* reliable copy-and-paste
* future YAML compatibility
* reproducible replay
* lossless archival

The transport layer is therefore separated from the snapshot specification itself.

⸻

7. Examples

Valid

```yaml
snapshot:
  id: S0021
  type: full
```

⸻

Invalid

snapshot:
id: S0021

Reason:

The snapshot is not enclosed in a fenced YAML block.

⸻

8. Security Considerations

Transport systems SHALL treat snapshots as immutable data.

Automatic formatting, beautification or semantic rewriting may invalidate deterministic replay and SHALL therefore be avoided.

⸻

9. Compatibility

This specification complements:

* CSP-0001 Snapshot Specification
* future Snapshot Schema specifications
* future Snapshot Replay specifications

It does not replace them.

⸻

10. Future Work

Future CYSSI specifications are expected to define:

* Snapshot Replay Specification
* Snapshot Validation Specification
* Snapshot Builder Specification
* Snapshot Schema Specification

These specifications will operate on snapshots transported according to this document.

⸻

11. Compliance

A transport implementation is considered STF compliant if it:

* transmits snapshots inside exactly one fenced yaml code block,
* preserves the snapshot content without modification,
* does not perform semantic reconstruction,
* reproduces the transmitted snapshot deterministically.

⸻

End of Specification