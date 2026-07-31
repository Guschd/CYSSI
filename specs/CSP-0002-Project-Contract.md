# CSP-0002 - Project Contract

  Field           Value
  --------------- ---------------------------
  Specification   CSP-0002
  Title           Project Contract
  Version         1.1
  Status          LOCKED
  Applies to      All CYSSI implementations

------------------------------------------------------------------------

# 1. Abstract

This specification defines the normative principles governing every
CYSSI project.

The Project Contract establishes the immutable rules for maintaining a
canonical project state across human and AI collaboration.

------------------------------------------------------------------------

# 2. Scope

This specification defines:

-   Canonical project state
-   Conversation semantics
-   Decision principles
-   Closed-loop development
-   Conformance requirements

Implementation details are defined by other CSP specifications.

------------------------------------------------------------------------

# 3. Terminology

## Canonical Project State

The single authoritative representation of a project.

## Conversation

A temporary working environment used only to exchange information.

## Project History

The collection of accepted historical snapshots preserved for
traceability.

## Closed-Loop Cycle

A reasoning cycle ending with an accepted snapshot.

------------------------------------------------------------------------

# 4. Core Principles

## 4.1 Canonical Project State

The canonical project state SHALL be the sole source of truth.

## 4.2 Conversation as Transport

Conversations SHALL transport information only and SHALL NOT be treated
as durable project storage.

## 4.3 Deterministic Before Creative

Deterministic processing SHALL take precedence over creative
reconstruction.

## 4.4 Reproduce Before Reconstruct

Implementations SHALL reproduce canonical information before attempting
inference.

## 4.5 Explicit Decisions

Normative project decisions SHALL require explicit acceptance before
becoming canonical.

## 4.6 Closed-Loop Development

Every completed reasoning cycle SHALL conclude with an accepted
snapshot.

------------------------------------------------------------------------

# 5. Normative Requirements

Implementations SHALL:

-   maintain exactly one canonical project state;
-   preserve accepted project history;
-   exchange snapshots according to CSP-0010;
-   replay snapshots according to CSP-0011;
-   validate snapshots according to CSP-0001.

------------------------------------------------------------------------

# 6. Processing Model

1.  Receive information.
2.  Evaluate proposed changes.
3.  Require explicit acceptance of normative decisions.
4.  Update the canonical project state.
5.  Generate a snapshot.
6.  Archive the previous state in project history.

------------------------------------------------------------------------

# 7. Conformance

A CYSSI implementation conforms if it:

-   maintains a canonical project state;
-   distinguishes conversations from project state;
-   supports deterministic replay;
-   preserves project history;
-   generates canonical snapshots.

------------------------------------------------------------------------

# 8. Security Considerations

Loss or modification of the canonical project state SHALL be treated as
a critical integrity violation.

Conversation history SHALL NOT be relied upon for project recovery.

------------------------------------------------------------------------

# 9. Compatibility

This specification complements:

-   CSP-0001 Snapshot Specification
-   CSP-0010 Snapshot Transport Format
-   CSP-0011 Snapshot Replay Specification

------------------------------------------------------------------------

# 10. Future Work

Future specifications may extend governance, collaboration workflows and
automated validation while preserving the principles defined herein.

------------------------------------------------------------------------

# Notes

The Project Contract defines the constitutional principles of the CYSSI
Framework. All future CSP specifications SHALL remain compatible with
this contract unless explicitly superseded by a future normative
revision.
