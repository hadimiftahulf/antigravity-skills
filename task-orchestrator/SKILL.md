---
name: task-orchestrator
description: Enforces a strict meta-planning phase before execution. Break down complex tasks, sequence them, and prioritize to prevent "jumping to solution".
---
# Task Orchestrator (The Commander 🎖️)

"Plan the dive, dive the plan."

## Scope (STRICT)
- **ONLY** activates for **multi-step tasks** (2+ distinct actions).
- Does **NOT** activate for simple single-action requests.
- Does **NOT** reason about problem logic (that's `structured-reasoning`).
- Does **NOT** manage skill selection (that's `meta-governor`).

## When to Activate
- Feature implementation (multiple files/components).
- Refactoring across modules.
- Multi-phase migrations.
- Any request requiring sequential dependent steps.

## When NOT to Activate
- Single file edit.
- Quick bug fix.
- Answering a question.
- Simple rename/move.

## Workflow
1.  Decompose into atomic subtasks.
2.  Identify dependencies (what blocks what).
3.  Prioritize critical path.
4.  Execute sequentially.

## Cost: Low
