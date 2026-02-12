---
name: refactor-code
description: Workflow for improving code structure, readability, and performance. Use when you need to refactor code safely with behavior verification via existing tests.
---

# Refactor Code Workflow

This skill ensures you refactor code safely by verifying behavior before and after changes.

## Workflow Steps

### 1. Pre-Check (Safety Net)
- **Verify Current State**: Run existing tests for the target module. **They must pass** before you touch anything.
- **Backup**: If no tests exist, strongly consider creating a "Snapshot Test" or backup file first.

### 2. Strategy
- **Identify Goal**: What are you improving? (Readability, DRY, Performance, Security).
- **Plan**: Decide which classes/methods will be extracted, renamed, or simplified.

### 3. Execution (Refactoring)
- **Apply Changes**: Perform the refactoring steps (Extract Method, Rename Variable, Introduce Value Object, etc.).
- **Keep Logic**: Do **NOT** change the business logic or external behavior.

### 4. Verification
- **Run Tests**: Run the tests again. They **MUST** still pass.
- **Lint**: Ensure the new code follows project style guidelines.
