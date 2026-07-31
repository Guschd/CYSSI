# CSP-0003 - Locked Facts Specification

  Field           Value
  --------------- ----------------------------
  Specification   CSP-0003
  Title           Locked Facts Specification
  Version         1.1
  Status          LOCKED
  Applies to      All CYSSI implementations

------------------------------------------------------------------------

# 1. Abstract

This specification defines the concept of **Locked Facts** within the
CYSSI Framework.

Locked Facts represent canonical project statements that have been
explicitly accepted and SHALL be treated as immutable until superseded
by a later accepted decision.

------------------------------------------------------------------------

# 2. Scope

This specification defines:

-   the purpose of Locked Facts;
-   creation and lifecycle;
-   processing rules;
-   validation requirements;
-   conformance requirements.

------------------------------------------------------------------------

# 3. Terminology

## Locked Fact

A canonical statement describing an accepted property of the project.

## Mutable Information

Information that may change without becoming a Locked Fact.

## Supersession

The replacement of an existing Locked Fact by an explicitly accepted
newer fact.

------------------------------------------------------------------------

# 4. Requirements

Locked Facts:

-   SHALL represent accepted canonical knowledge.
-   SHALL be stored in the `locked_facts` section of a snapshot.
-   SHALL be written as atomic statements.
-   SHALL be independent of conversation history.
-   SHALL remain valid until explicitly superseded.

------------------------------------------------------------------------

# 5. Lifecycle

1.  Proposal
2.  Review
3.  Explicit Acceptance
4.  Inclusion in a Full Snapshot
5.  Canonical State
6.  Optional Supersession by a later accepted fact

------------------------------------------------------------------------

# 6. Processing Model

Implementations SHALL:

1.  Load Locked Facts from the canonical snapshot.
2.  Treat them as immutable during reasoning.
3.  Reject implicit modification.
4.  Apply only explicitly accepted replacements.
5.  Preserve historical facts through Project History.

------------------------------------------------------------------------

# 7. Validation Rules

Implementations SHALL verify:

-   presence of the `locked_facts` section when applicable;
-   each fact is represented as a single canonical statement;
-   duplicate facts MAY be ignored or consolidated;
-   contradictory facts SHALL require explicit resolution before
    acceptance.

------------------------------------------------------------------------

# 8. Conformance

A CYSSI implementation conforms if it:

-   preserves Locked Facts across replay;
-   never modifies them implicitly;
-   supports explicit supersession;
-   includes accepted Locked Facts in every Full Snapshot.

------------------------------------------------------------------------

# 9. Security Considerations

Implicit modification, deletion or reconstruction of Locked Facts SHALL
be treated as a violation of canonical project integrity.

------------------------------------------------------------------------

# 10. Compatibility

This specification complements:

-   CSP-0001 Snapshot Specification
-   CSP-0002 Project Contract
-   CSP-0011 Snapshot Replay Specification

------------------------------------------------------------------------

# Notes

Locked Facts are the stable knowledge foundation of a CYSSI project.
They enable deterministic reasoning independent of conversation context
and ensure long-term consistency across snapshots.