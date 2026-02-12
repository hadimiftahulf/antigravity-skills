---
name: advanced-architecture
description: Implementation of Enterprise patterns: CQRS, Event Sourcing, Domain-Driven Design (DDD).
---

# Advanced Architecture (The Enterprise Core 🏢)

For when MVC is not enough.

## Patterns

### 1. DDD (Domain-Driven Design)
- **Aggregates**: Cluster of objects treated as a unit (e.g., Order + OrderLines).
- **Value Objects**: Objects defined by attributes, not ID (e.g., Money, EmailAddress). Immutability is key.
- **Bounded Contexts**: Sales context vs Inventory context. Do not share models directly.

### 2. CQRS (Command Query Responsibility Segregation)
- **Write Side**: `CreateInvoiceCommand` -> `invoices` table.
- **Read Side**: `InvoiceReadModel` (Optimized JSON column or separate ElasticSearch index).
- **Benefit**: Read performance does not block Write complexity.

### 3. Event-Driven
- **Domain Events**: `OrderPlaced` (Past Tense).
- **Listeners**: `SendEmail`, `UpdateInventory`, `NotifySlack`.
- **Decoupling**: The Order Service doesn't know about Slack.

