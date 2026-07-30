# CSP-0001 — Snapshot Specification

| Field | Value |
|-------|-------|
| Specification | CSP-0001 |
| Title | Snapshot Specification |
| Version | 1.0 |
| Status | LOCKED |
| Applies to | All CYSSI implementations |

---

# 1. Abstract

This specification defines the canonical snapshot format used by the CYSSI Framework.

A snapshot represents either:

- a reusable template,
- a change set,
- or a complete canonical project state.

Every compliant CYSSI implementation SHALL support this specification.

---

# 2. Scope

This specification defines:

- Snapshot document structure
- Snapshot document types
- Required and optional fields
- Processing model
- Validation rules
- Conformance requirements

The semantics of individual project sections are defined by their respective CSP specifications.

---

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

---

# 4. Requirements

Every snapshot SHALL contain:

```yaml
snapshot:

  id:
  type:
  version:
  status:
```

## Snapshot Types

| Type | Description |
|------|-------------|
| `template` | Reusable template |
| `change` | Delta relative to a base snapshot |
| `full` | Complete canonical project state |

### Full Snapshot

A Full Snapshot:

- SHALL completely describe the project state.
- SHALL be independently reproducible.
- SHALL NOT require previous snapshots.

### Change Snapshot

A Change Snapshot:

- SHALL declare `base_snapshot`.
- SHALL contain only changed information.
- SHALL NOT be used as the sole restoration source.

Required header:

```yaml
snapshot:

  id:
  type: change
  base_snapshot:
  version:
  status:
```

### Template Snapshot

A Template Snapshot:

- SHALL define the snapshot structure.
- SHALL NOT contain project-specific state.
- SHOULD use commented example values.

---

# 5. Processing Model

A compliant implementation SHALL process snapshots in the following order:

1. Parse YAML
2. Validate syntax
3. Validate snapshot header
4. Determine `snapshot.type`
5. Validate type-specific requirements
6. Process the document

---

# 6. Validation Rules

Implementations SHALL verify:

- Valid YAML
- Presence of all required header fields
- Valid `snapshot.type`
- Valid `snapshot.status`
- Presence of `base_snapshot` for Change Snapshots

Unknown optional fields MAY be ignored.

Malformed mandatory fields SHALL produce a validation error.

---

# 7. Conformance

A CYSSI implementation is conformant if it:

- supports all snapshot types,
- correctly validates this specification,
- processes snapshots according to the Processing Model,
- accepts all valid snapshots,
- rejects invalid snapshots.

---

# Appendix A — Minimal Full Snapshot

```yaml
snapshot:

  id: S0001
  type: full
  version: 0.18.0
  status: LOCKED
```

---

# Appendix B — Minimal Change Snapshot

```yaml
snapshot:

  id: S0002
  type: change
  base_snapshot: S0001
  version: 0.18.0
  status: DRAFT
```

---

# Appendix C — Minimal Template Snapshot

```yaml
snapshot:

  id: TEMPLATE
  type: template
  version: 1.0
  status: TEMPLATE
```

---

# Notes

This specification serves as the structural foundation for all subsequent CYSSI Project Specifications (CSPs). Future CSP documents SHALL follow the canonical document structure introduced by CSP-0001 unless explicitly stated otherwise.
