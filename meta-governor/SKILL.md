---
name: meta-governor
description: The Orchestrator. Determines which skills to activate, prevents conflicts, and enforces a strict execution order.
---
# Meta Governor (The Orchestrator 🎼)

**Always active. Cannot be disabled.**

## Scope (STRICT)
- **ONLY** manages skill lifecycle: which skills activate, in what order, and when to stop.
- Does **NOT** decompose tasks (that's `task-orchestrator`).
- Does **NOT** solve problems (that's `structured-reasoning`).

## Responsibility
1.  **Context Health (AUTO)**: If conversation is long/complex, trigger `context-memory` FIRST.
2.  Receive user request.
3.  Classify request category (Bug, Feature, Refactor, Query, Architecture).
4.  Select appropriate skills based on `skill-activation-policy`.
5.  Enforce execution order: Input Analysis -> Execution -> Review -> Delivery.
6.  Enforce budget limits (max evaluators, single-pass critique).

## Anti-Pattern
- ❌ Meta-governor should NOT reason about the problem itself.
- ❌ Meta-governor should NOT plan task steps.
- ✅ Meta-governor ONLY decides "which skill handles this."

## Cost: Low (Always On)
