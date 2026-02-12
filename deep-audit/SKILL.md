---
name: deep-audit
description: Performs deep architectural audits to enforce separation of concerns. Specialized for Filament ERP 5-layer structure but adaptive to React, Flutter, and other frameworks to ensure UI vs. Business Logic separation.
---

# Deep Audit Workflow

This skill enforces strict architectural boundaries. It adapts its checks based on the detected project framework.

## Phase 1: Context Detection & Setup

1.  **Identify Framework**: Look for key indicators (`composer.json` for Laravel, `package.json` with react, `pubspec.yaml` for Flutter).
2.  **Define Layers**: Based on the framework, establish what constitutes "UI", "State", and "Logic/Service".

---

## Phase 2: Audit Execution

### SCENARIO A: Laravel / Filament ERP (The "5-Layer" Structure)
*Trigger: Presence of `app/Filament` or user request for "Service/State" audit.*

**Target Files**:
- Service: `app/Services/<Domain>/<Module>Service.php`
- State: `app/Filament/Clusters/<Cluster>/State/<Module>State.php`

**Invariants**:
1.  **Service Scope (Layer 3)**:
    - MUST handle: Business logic, Model mutations, `static function xxxAction(): Closure`.
    - MUST NOT contain: UI callbacks (`isVisible`, `getOptions`), Helper Hints (`callable $get`), HTML/CSS.
2.  **State Scope (Layer 2)**:
    - MUST handle: UI callbacks, Visibility, Modals, Navigation/Redirects, Notifications.
    - MUST be STATIC.
    - **Factory Pattern**: UI callbacks must return a `Closure`, not execute logic directly.
3.  **Schema (Layer 1)**:
    - **Zero Service Reference**: NEVER import `*Service` classes directly.
    - **Container Pattern**: Use `::make()` for wrappers, `::schema()` for lists.

**Action**: Run `grep` / `ripgrep` to find violations like `Notification::make` in Services.

---

### SCENARIO B: React / Vue / Frontend
*Trigger: `package.json` with React/Vue/Next.js/Nuxt.*

**Target Files**:
- Components: `src/components/**/*.tsx|vue`
- Logic: `src/hooks/*.ts`, `src/stores/*.ts`, or `src/services/*.ts`

**Invariants**:
1.  **Component (UI)**:
    - MUST: Be purely presentational or handle transient UI state (e.g., form input).
    - MUST NOT: Contain complex business logic, data transformation, or specific API implementations.
2.  **Hooks/Store (State/Logic)**:
    - MUST: Handle data fetching, state mutations, and business rules.
    - MUST NOT: Return JSX/Template code (unless it's a render prop pattern, but generally discourage).

**Action**: Scan components for `fetch(`, `axios.`, or inline complex reduce/map logic that belongs in a utility/hook.

---

### SCENARIO C: Flutter
*Trigger: `pubspec.yaml`.*

**Target Files**:
- Widgets: `lib/ui/**` or `lib/pages/**`
- Logic: `lib/bloc/**`, `lib/providers/**`, or `lib/cubit/**`

**Invariants**:
1.  **Widgets (UI)**:
    - MUST NOT: Make HTTP requests directly or handle database transactions.
    - MUST: Delegate events to Bloc/Provider/Controller.
2.  **Logic Layer**:
    - MUST NOT: Import `package:flutter/material.dart` (unless absolutely necessary for UI-specific models, but ideally keep pure Dart).

---

## Phase 3: Reporting & Fixes

1.  **Report**: Group findings by "Layer Violation" (Critical) or "Code Smell" (Warning).
2.  **Refactor**:
    - **Laravel**: Move logic from Service -> State or Schema -> State.
    - **JS/Dart**: Extract logic into Custom Hooks, Composables, or Service classes.
3.  **Verify**: Ensure no circular dependencies were created.

