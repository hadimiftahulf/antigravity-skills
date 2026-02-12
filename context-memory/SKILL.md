---
name: context-memory
description: Manages a persistent context file to track high-level decisions and project state across sessions. Includes strategies for summarizing long conversations and maintaining focus.
---
# Context Memory (The Scribe 📜)

Merged: `context-memory` + `context-compressor`.

## Memory Function
Tracks high-level decisions (Tech Stack, Conventions, Architecture Choices) to maintain consistency across long sessions and conversations.

## Compression Function (formerly context-compressor)
When conversation grows long:
1.  **Extract**: Key decisions, constraints, and action items.
2.  **Discard**: Exploratory discussion, rejected ideas, verbose explanations.
3.  **Summarize**: Compress into structured notes (Decision + Rationale + Status).

## Rules
- Update context file when major decisions are made.
- Compress proactively, not reactively.
- Never discard user constraints or preferences.

## Cost: Low
