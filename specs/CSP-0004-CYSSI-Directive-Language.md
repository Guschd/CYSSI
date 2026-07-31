# CSP-0004 - CYSSI Directive Language (CDL)

  Field           Value
  --------------- --------------------------------
  Specification   CSP-0004
  Title           CYSSI Directive Language (CDL)
  Version         1.1
  Status          LOCKED
  Applies to      All CYSSI implementations

------------------------------------------------------------------------

# 1. Abstract

This specification defines the CYSSI Directive Language (CDL), a
deterministic instruction layer used to control snapshot processing and
project-state handling.

CDL directives SHALL be evaluated before conversational inference.

------------------------------------------------------------------------

# 2. Scope

This specification defines:

-   directive syntax;
-   processing order;
-   validation rules;
-   conflict handling;
-   conformance requirements.

------------------------------------------------------------------------

# 3. Terminology

## Directive

A structured instruction interpreted deterministically by a CYSSI
implementation.

## Directive Set

The collection of directives supplied for a processing cycle.

## Conversational Inference

Reasoning performed after deterministic directive processing.

------------------------------------------------------------------------

# 4. Core Principles

-   Directives SHALL be processed before conversational inference.
-   Directive processing SHALL be deterministic.
-   Unknown directives SHALL NOT modify the canonical project state.
-   Directives SHALL NOT bypass the Project Contract (CSP-0002).

------------------------------------------------------------------------

# 5. Processing Model

1.  Extract snapshot according to CSP-0010.
2.  Parse directives.
3.  Validate directive syntax.
4.  Execute valid directives deterministically.
5.  Replay snapshots if required (CSP-0011).
6.  Continue with conversational reasoning.

------------------------------------------------------------------------

# 6. Validation Rules

Implementations SHALL verify:

-   valid directive syntax;
-   supported directive names;
-   valid parameters;
-   absence of conflicting deterministic operations.

Unsupported directives MAY be ignored but SHALL NOT change the canonical
project state.

------------------------------------------------------------------------

# 7. Conflict Resolution

If two directives conflict:

1.  Validation SHALL detect the conflict.
2.  No partial execution SHALL occur.
3.  Explicit user resolution SHALL be required before continuation.

------------------------------------------------------------------------

# 8. Conformance

A CYSSI implementation conforms if it:

-   evaluates directives deterministically;
-   executes directives before inference;
-   preserves canonical project integrity;
-   rejects invalid deterministic operations.

------------------------------------------------------------------------

# 9. Security Considerations

Directive execution SHALL NOT permit implicit modification of Locked
Facts, Decision Logs or Project History.

Only explicitly accepted changes MAY affect the canonical project state.

------------------------------------------------------------------------

# 10. Compatibility

This specification complements:

-   CSP-0001 Snapshot Specification
-   CSP-0002 Project Contract
-   CSP-0003 Locked Facts Specification
-   CSP-0010 Snapshot Transport Format
-   CSP-0011 Snapshot Replay Specification

------------------------------------------------------------------------

# Future Work

Future revisions MAY standardize individual directive keywords,
namespaces and extension mechanisms while preserving deterministic
processing semantics.

------------------------------------------------------------------------

# Notes

The CYSSI Directive Language provides a deterministic control layer
separating machine-processable instructions from conversational
reasoning, ensuring reproducible project evolution.
