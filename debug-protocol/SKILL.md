---
name: debug-protocol
description: A systematic, scientific debugging workflow to isolate and fix bugs efficiently without guessing.
---

# Debug Protocol (The Fixer 🕵️‍♂️)

Stop guessing. Follow the scientific method to solve bugs definitively.

## Phase 1: Reproduction & Isolation
*Goal: Make it fail reliably.*
1.  **Analyze the Error**: Read the *entire* stack trace. Identify the EXACT file and line number.
2.  **Create Reproduction Step**: Can you trigger it with a curl command? A specific UI click? A unit test?
    - *If you can't reproduce it, you can't fix it.*
3.  **Isolate Environment**: Is it a data issue? A code issue? A config issue?
    - *Binary Search*: Comment out half the code/modules to find the culprit.

## Phase 2: Root Cause Analysis (RCA)
*Goal: Understand WHY it fails.*
1.  **Trace the Data**: Log the state at entry, middle, and exit points of the suspicious function.
2.  **Challenge Assumptions**: "This variable *should* be an array" -> *Is it actually?*
3.  **Check Recent Changes**: Did this work yesterday? What changed? (`git log`)

## Phase 3: The Fix & Verification
*Goal: Fix it and ensure it stays fixed.*
1.  **Apply Minimal Fix**: Don't refactor the whole system. Fix the specific bug first.
2.  **Verify Reproduction**: Run the reproduction step from Phase 1. It must pass now.
3.  **Regression Test**: Run related tests to ensure you didn't break anything else.
4.  **prevent recurrence**: Can you add a type guard, validaton, or test case to prevent this forever?

