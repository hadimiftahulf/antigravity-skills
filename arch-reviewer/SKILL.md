---
name: arch-reviewer
description: Enforces modularity, reusability (DRY), and high-level architectural patterns. Focuses on SOLID principles, Design Patterns, and Scalability.
---

# Architecture Reviewer (The Architect 🏛️)

This skill focuses on the **Structure**, ensuring code is clean, modular, and reusable. It enforces **DRY (Don't Repeat Yourself)** and **Separation of Concerns**.

## Review Checklist

### 1. Modularity & Cohesion (The "Lego" Principle)

- **Single Responsibility (SRP)**:
  - Does this Class/Function have only _one reason to change_?
  - _Violation_: A `User` model handling PDF export. -> _Fix_: Extract to `UserPdfExporter`.
- **High Cohesion**:
  - Do methods in this class relate to each other?
  - _Violation_: `OrderService` containing `sendEmail()` and `calculateTax()`. -> _Fix_: Use `NotificationService` and `TaxCalculator`.
- **Loose Coupling**:
  - Can I change one module without breaking others?
  - _Strategy_: Use Interfaces, Events, or Dependency Injection instead of hard dependencies.

### 2. Reusability (DRY - Don't Repeat Yourself)

- **Abstraction**:
  - Are you copying code blocks? -> _Fix_: Extract to a reusable `Trait`, `Mixin`, `BaseClass`, or `Utility`.
- **Composition over Inheritance**:
  - Prefer composing small behaviors (Traits/Components) over deep inheritance hierarchies.
- **Generic Components**:
  - Is this UI component too specific? -> _Fix_: Make it generic (accept props/slots) so it works in other contexts.
- **Configuration over Hardcoding**:
  - Avoid magic numbers/strings deep in code. Move to config files or constants.

### 3. SOLID Compliance

- **Open/Closed (OCP)**:
  - Can I add new behavior (e.g., new Payment Method) without modifying existing code? -> _Fix_: Use Polymorphism/Strategy Pattern.
- **Dependency Inversion (DIP)**:
  - Depend on _Abstractions_ (Interfaces), not _Concretions_ (Classes).
  - _Check_: Inject `MailerInterface`, not `SmtpMailer`.

### 4. Scalability & Performance

- **State Management**:
  - Is the app properly stateless where needed? (e.g., API tokens vs Session).
- **Async Processing**:
  - Are heavy tasks (Emails, Reports, 3rd Party APIs) blocking the main thread? -> _Fix_: Dispatch to a Job Queue.
- **Database Optimization**:
  - Check for N+1 queries. Use Eager Loading (`with()`) or Batch Inserts.

### 5. Design Patterns

- **Factory**: For creating complex objects with varying logic.
- **Observer/Event**: For decoupling side effects (e.g., `OrderPlaced` -> `SendEmail`, `UpdateInventory`).
- **Repository**: For abstracting complex database queries (if applicable to stack).
- **Strategy**: For swapping algorithms at runtime (e.g., `DiscountCalculator`).
