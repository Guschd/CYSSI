 CSP-0001 - Snapshot Specification

  Field           Value
  --------------- ---------------------------
  Specification   CSP-0001
  Title           Snapshot Specification
  Version         1.1
  Status          LOCKED
  Applies to      All CYSSI implementations

------------------------------------------------------------------------

# 1. Abstract

This specification defines the canonical snapshot format used by the
CYSSI Framework.

A snapshot represents either:

-   a reusable template,
-   a change set,
-   or a complete canonical project state.

Every compliant CYSSI implementation SHALL support this specification.

Snapshot transport is defined separately by CSP-0010 (Snapshot Transport
Format). Replay semantics are defined by CSP-0011 (Snapshot Replay
Specification).

------------------------------------------------------------------------

# 2. Scope

This specification defines:

-   Snapshot document structure
-   Snapshot document types
-   Required and optional fields
-   Processing model
-   Validation rules
-   Conformance requirements

The semantics of individual project sections are defined by their
respective CSP specifications.

------------------------------------------------------------------------

# 3. Terminology

## Snapshot

A YAML document representing a CYSSI project state.

## Full Snapshot

A complete canonical project state that can be restored independently.

## Change Snapshot

A document containing only changes relative to another snapshot.

## Template Snapshot

A reusable snapshot template without project-specific state.

## Canonical Project State

The authoritative representation of a project.

## Snapshot Transport Format (STF)

The external representation used to exchange snapshots between systems.

The canonical transport mechanism is specified by CSP-0010.

------------------------------------------------------------------------

# 4. Requirements

Every snapshot SHALL contain:

``` yaml
snapshot:
  id:
  type:
  version:
  status:
```

## Snapshot Types

  Type         Description
  ------------ ----------------------------------
  `template`   Reusable template
  `change`     Delta relative to a predecessor
  `full`       Complete canonical project state

### Full Snapshot

A Full Snapshot:

-   SHALL completely describe the project state.
-   SHALL be independently reproducible.
-   SHALL NOT require previous snapshots.

### Change Snapshot

A Change Snapshot:

-   SHALL reference its predecessor through the project history.
-   SHALL contain only changed information.
-   SHALL NOT be used as the sole restoration source.
-   SHALL be replayed onto a Full Snapshot as specified by CSP-0011.

Required header:

``` yaml
snapshot:
  id:
  type: change
  version:
  status:

history:
  predecessor:
```

### Template Snapshot

A Template Snapshot:

-   SHALL define the snapshot structure.
-   SHALL NOT contain project-specific state.
-   SHOULD use commented example values.

------------------------------------------------------------------------

# 5. Processing Model

1.  Extract the Snapshot Transport Format as defined by CSP-0010.
2.  Parse the enclosed snapshot document.
3.  Validate snapshot syntax.
4.  Validate the snapshot header.
5.  Determine `snapshot.type`.
6.  Validate type-specific requirements.
7.  Process the snapshot according to its type.
8.  If applicable, perform replay as specified by CSP-0011.
9.  Produce the resulting canonical project state.

------------------------------------------------------------------------

# 6. Validation Rules

Implementations SHALL verify:

-   Valid YAML
-   Presence of all required header fields
-   Valid `snapshot.type`
-   Valid `snapshot.status`
-   Presence of `history.predecessor` for Change Snapshots

Unknown optional fields MAY be ignored.

Malformed mandatory fields SHALL produce a validation error.

------------------------------------------------------------------------

# 7. Conformance

A CYSSI implementation is conformant if it:

-   supports all snapshot types,
-   correctly validates this specification,
-   processes snapshots according to the Processing Model,
-   accepts all valid snapshots,
-   rejects invalid snapshots.

------------------------------------------------------------------------

# Appendix A --- Minimal Full Snapshot

``` yaml
snapshot:
  id: S0001
  type: full
  version: 0.18.0
  status: LOCKED
```

------------------------------------------------------------------------

# Appendix B --- Minimal Change Snapshot

``` yaml
snapshot:
  id: S0002
  type: change
  version: 0.18.0
  status: DRAFT

history:
  predecessor: S0001
```

------------------------------------------------------------------------

# Appendix C --- Minimal Template Snapshot

``` yaml
snapshot:
  id: TEMPLATE
  type: template
  version: 1.0
  status: TEMPLATE
```

------------------------------------------------------------------------

# Notes

This specification serves as the structural foundation for all
subsequent CYSSI Project Specifications (CSPs).

Transport SHALL conform to CSP-0010.

Snapshot replay SHALL conform to CSP-0011.

Future schema-specific requirements MAY further constrain the snapshot
format without changing the semantics defined by this specification.
