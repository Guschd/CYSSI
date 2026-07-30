# Introduction

> **The chat is temporary. The project state is forever.**

Welcome to **CYSSI** — the **Canonical Project State Management Framework**.

CYSSI is an open-source framework that enables long-running projects between humans and AI systems without relying on chat history or model-specific memory.

Instead of treating conversations as the source of knowledge, CYSSI stores the complete project state in a structured, version-controlled snapshot.

This allows any compatible AI model to continue work from exactly the same canonical state.

---

# Why CYSSI?

Large Language Models are excellent at reasoning within a conversation.

However, conversations are inherently temporary.

Over time they become:

- too long
- inconsistent
- difficult to search
- expensive to maintain
- prone to information drift

As projects grow, important decisions disappear into chat history and context windows become the limiting factor instead of the project itself.

CYSSI addresses this problem by separating **communication** from **project state**.

Instead of reconstructing knowledge from previous conversations, the project is reproduced from a canonical snapshot.

---

# Core Philosophy

CYSSI is built around one fundamental principle.

> **Chats are communication. Snapshots are knowledge.**

A conversation is only a transport medium.

The snapshot is the project's memory.

This distinction allows conversations to end without losing information.

Every important decision is transferred into the canonical project state before the session ends.

---

# Design Principles

CYSSI follows a small set of guiding principles.

## Canonical State

There is exactly one authoritative project state.

No hidden memory exists outside the snapshot.

---

## Human Readable

All project information is stored in plain YAML.

No proprietary database is required.

Snapshots can be read, edited and version-controlled using any text editor.

---

## Machine Readable

Snapshots are deterministic.

Every compatible implementation can parse and validate them.

---

## Model Independent

CYSSI is not tied to any specific AI provider.

Any model capable of understanding YAML and the CYSSI specification can continue a project.

---

## Explicit Decisions

Architectural decisions are never inferred.

Important changes become explicit entries in the decision log.

---

## Version Controlled

Snapshots evolve over time.

Each snapshot represents a complete project state that can be archived, compared and restored.

---

# How CYSSI Works

The workflow is intentionally simple.

```mermaid
flowchart LR

A[Start Conversation]
-->B[Load Snapshot]

B
-->C[Restore Project State]

C
-->D[Work With AI]

D
-->E[Update Project State]

E
-->F[Generate New Snapshot]

F
-->G[End Conversation]
```

The chat may disappear.

The snapshot remains.

---

# Repository Overview

The repository is organised into four major areas.

| Directory | Purpose |
|-----------|----------|
| `docs/` | Human-readable documentation |
| `specs/` | Normative CYSSI specifications (CSP series) |
| `schema/` | Machine-readable validation schemas |
| `examples/` | Reference snapshots and sample projects |

---

# Typical Workflow

1. Create a new project.
2. Generate the initial snapshot.
3. Work with one or more AI systems.
4. Record decisions.
5. Generate a new snapshot.
6. Continue the project later using only the newest snapshot.

Previous conversations are optional.

The latest snapshot is sufficient.

---

# Who Is CYSSI For?

CYSSI is useful for projects that span multiple sessions or multiple AI models.

Typical examples include:

- Software engineering
- Research projects
- Documentation
- Technical writing
- Infrastructure planning
- Long-term creative work
- AI-assisted engineering

---

# Goals

The long-term objectives of CYSSI are:

- Provide a vendor-neutral project state format
- Eliminate dependence on conversation history
- Enable deterministic AI collaboration
- Improve reproducibility
- Simplify long-running AI projects
- Establish an open specification for canonical project state management

---

# Open Source

CYSSI is developed as an open-source project.

The framework is intentionally model-independent and designed for community contributions.

Everyone is welcome to improve the specification, propose extensions and implement compatible tools.

See `CONTRIBUTING.md` for contribution guidelines.

---

# Next Steps

Continue with:

- **Architecture.md** — Framework architecture
- **Project_Contract.md** — Canonical project contract
- **CDL.md** — CYSSI Directive Language
- **Snapshots.md** — Snapshot structure and lifecycle
- **Best_Practices.md** — Recommended workflows

Or, if you want to implement CYSSI, start with the **CSP specifications** located in the `specs/` directory.