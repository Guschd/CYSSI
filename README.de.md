<img src="assets/banner.PNG" width="100%">

🌍 **Sprache / Language**
🇩🇪 **Deutsch** • [🇬🇧 English](README.md)

# CYSSI Framework

> **Der Chat ist vergänglich.  
> Der Projektzustand bleibt.**

---

## Jedes KI-Projekt stößt früher oder später auf dasselbe Problem.

Du beginnst eine neue Unterhaltung.

Die KI ist beeindruckend leistungsfähig.

Sie hilft dir beim Entwickeln von Software, beim Schreiben von Dokumentationen und beim Lösen komplexer Probleme.

Ein paar Tage später öffnest du einen neuen Chat.

Plötzlich scheint dein Projekt verschwunden zu sein.

Wichtige Entscheidungen fehlen.
Die Dokumentation entwickelt sich in unterschiedliche Richtungen.
Die KI trifft andere Annahmen als zuvor.

Das ist kein Fehler der KI.

Chats waren nie dafür gedacht, den dauerhaften Wissensstand eines Projekts zu speichern.

**Genau hier setzt CYSSI an.**

---

# Was ist CYSSI?

CYSSI ist ein offenes Framework zur Verwaltung des **kanonischen Projektzustands** langfristiger Mensch-KI-Projekte.

Anstatt Unterhaltungen als Gedächtnis zu verwenden, behandelt CYSSI sie als Transportweg für Informationen.

Jede Unterhaltung beginnt mit der Wiederherstellung des aktuellen Projektzustands.

Jede Unterhaltung endet mit dessen Aktualisierung.

Damit wird nicht der Chat, sondern das Projekt selbst zur einzigen verbindlichen Quelle der Wahrheit.

---

# So funktioniert CYSSI

```text
Unterhaltung
      │
      ▼
Conversation Compiler
      │
      ▼
Kanonischer Projektzustand
      │
      ▼
Snapshot
      │
      ▼
Nächste Unterhaltung
```

Jede Sitzung beginnt mit einem Snapshot und erzeugt am Ende einen neuen Snapshot.

---

# Ohne CYSSI

```text
Unterhaltung A
      │
Entscheidung:
Python verwenden
      │
Unterhaltung B
      │
Entscheidung vergessen
      │
Das Projekt beginnt auseinanderzulaufen
```

# Mit CYSSI

```text
Unterhaltung A
      │
Snapshot
      │
Unterhaltung B
      │
Snapshot geladen
      │
Entscheidung bleibt erhalten
```

---

# Die wichtigsten Bausteine

### Project Contract

Legt die Regeln fest, denen jede CYSSI-Implementierung folgen muss.

### Locked Facts

Informationen, die sich nicht unbeabsichtigt ändern dürfen.

### Conversation Compiler

Überführt natürliche Sprache in strukturiertes Projektwissen.

### Kanonischer Projektzustand

Die vollständige und verbindliche Beschreibung des Projekts.

### Snapshot

Eine portable Darstellung des aktuellen Projektzustands.

### CYSSI Directive Language (CDL)

Ermöglicht deterministische Änderungen am Projektzustand.

```text
@set project.name "CYSSI"
@add locked_facts "Der Frameworkname lautet CYSSI."
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

Die vollständigen Spezifikationen befinden sich in `docs/` und `specs/`.

Diese README soll zunächst das Konzept vermitteln und den Einstieg erleichtern.

---

# Grundprinzipien

- Kanonisch vor konversationell.
- Explizit vor implizit.
- Deterministisch statt heuristisch.
- Für Menschen und Maschinen lesbar.
- Modellunabhängig.
- Auf langfristige Projekte ausgelegt.

---

# Aktueller Stand

**Version:** 0.17.0

**Status:** Public Pre-Release

---

# Vision

CYSSI ist keine KI.

CYSSI ist kein Chatbot.

CYSSI ist keine Programmiersprache.

CYSSI ist ein Framework, das den Projektzustand über Unterhaltungen, Sitzungen und verschiedene KI-Modelle hinweg bewahrt.

Denn wenn Chats vergänglich sind, sollten Projekte es nicht sein.