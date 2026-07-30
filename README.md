<img src="assets/banner.PNG" width="100%">

🌍 **Language / Sprache**
🇬🇧 **English** (default) • [🇩🇪 Deutsch](README.de.md)

# CYSSI Framework

> **The chat is temporary.  
> The project state is forever.**

---

## Every AI project eventually hits the same wall.

You start a new conversation.

The AI is brilliant.

It helps you design software, write documentation and solve difficult problems.

A week later you open a new chat.

The project is gone.

Important decisions have vanished.
Documentation slowly drifts apart.
The AI makes different assumptions than before.

Nothing is technically broken.

The conversation was never meant to be your project's memory.

**CYSSI exists because of that simple observation.**

---

# What is CYSSI?

CYSSI is an open framework for preserving the **canonical state** of long-running Human–AI projects.

Instead of treating conversations as memory, CYSSI treats them as transport.

Every conversation begins by restoring the project.

Every conversation ends by updating it.

The project—not the chat—becomes the single source of truth.

---

# How it works

```text
Conversation
      │
      ▼
Conversation Compiler
      │
      ▼
Canonical Project State
      │
      ▼
Snapshot
      │
      ▼
Next Conversation
```

Every session starts from a snapshot and produces a new one.

---

# Without CYSSI

```text
Conversation A
    │
Decision: Use Python
    │
Conversation B
    │
Decision forgotten
    │
Project begins to drift
```

# With CYSSI

```text
Conversation A
    │
Snapshot
    │
Conversation B
    │
Snapshot restored
    │
Decision preserved
```

---

# The Building Blocks

### Project Contract

Defines the rules every implementation follows.

### Locked Facts

Information that must never change accidentally.

### Conversation Compiler

Transforms natural language into structured project knowledge.

### Canonical Project State

The authoritative representation of the entire project.

### Snapshot

A portable representation of the current project state.

### CYSSI Directive Language (CDL)

Allows deterministic modifications to the canonical project state.

Example:

```text
@set project.name "CYSSI"
@add locked_facts "Framework name is CYSSI."
@snapshot
```

---

# Repository

```text
docs/
specs/
schema/
examples/
assets/
```

Detailed specifications live inside `docs/` and `specs/`.

The README is intentionally focused on understanding the framework before exploring its internals.

---

# Design Principles

- Canonical before conversational.
- Explicit before implicit.
- Deterministic before heuristic.
- Human-readable and machine-readable.
- Model independent.
- Long-term project continuity.

---

# Current Status

Version: **0.17.0**

Status: **Public Pre-Release**

---

# Vision

CYSSI is not another AI.

It is not another chatbot.

It is not another programming language.

It is a framework for preserving project state across conversations, sessions and language models.

If conversations are temporary, projects shouldn't be.
