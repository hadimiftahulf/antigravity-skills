---
name: skill-activation-policy
description: Defines rules for skill activation, including input requirements, output contracts, conflict lists, and performance costs. Enforces Lean Execution mode by default.
---
# Skill Activation Policy (The Gatekeeper 🚪)

"Efficiency is intelligent laziness."

## 0. Core Invariants
- `meta-governor` is **always active** and **cannot be disabled**.
- `indonesian-communicator` is **always active**. All user-facing output in Bahasa Indonesia.
- `output-discipline` is **always active**. Professional formatting enforced.
- `hallucination-guard` is **always active**. Verification before generation.

## 1. Activation Matrix
| Category | Skills | Behavior |
| :--- | :--- | :--- |
| **Always-On** | `meta-governor`, `indonesian-communicator`, `output-discipline`, `hallucination-guard` | Every request. Cannot disable. |
| **Conditional** | `context-memory` (long chat), `task-orchestrator` (multi-step only), `clarification-enforcer` (ambiguity >40%), `constraint-enforcer` (code output only) | When condition met. |
| **On-Demand** | All other skills | Trigger word or escalation. |

## 2. Authority Scope (Anti-Overlap)
| Skill | Scope | Does NOT |
| :--- | :--- | :--- |
| `meta-governor` | Skill lifecycle & selection | Plan tasks, Solve problems |
| `task-orchestrator` | Multi-step task decomposition | Select skills, Reason logic |
| `structured-reasoning` | Complex problem solving | Plan tasks, Select skills |

## 3. Definitions
- **Evaluator**: Skill that reviews/audits/critiques/scans/profiles.
- **Execution Skill**: Skill that creates/modifies/fixes code (not counted as evaluator).

## 4. Single Authority Rule 👑
Overlap → lower-cost skill runs. Higher-cost needs explicit escalation.

| Tier | Skills | Auto? |
| :--- | :--- | :--- |
| **Low** | `output-discipline`, `indonesian-communicator`, `constraint-enforcer`, `hallucination-guard`, `error-taxonomy`, `i18n-localizer`, `stakeholder-translator` | ✅ |
| **Medium** | `structured-reasoning`, `debug-protocol`, `refactor-code`, `migration-planner` | ✅ |
| **High** | `deep-audit`, `advanced-architecture`, `optimize-perf`, `security-scan` | ❌ |

## 5. Conflict Resolution Table ⚔️
| Conflict | Winner | Reason |
| :--- | :--- | :--- |
| `clarification-enforcer` vs `task-orchestrator` | `clarification-enforcer` | Clarify before planning |
| `constraint-enforcer` vs `refactor-code` | `constraint-enforcer` | Contract lock |
| `hallucination-guard` vs `output-discipline` | `hallucination-guard` | Correctness > brevity |
| `debug-protocol` vs `optimize-perf` | `debug-protocol` | Fix first, optimize later |
| `security-scan` vs `optimize-perf` | `security-scan` | Security > performance |
| `migration-planner` vs `refactor-code` | `migration-planner` | Data safety > code cleanliness |
| `indonesian-communicator` vs `output-discipline` | `indonesian-communicator` | Language rule overrides format |

## 6. Escalation Authority 🔑
Only **User** or **`meta-governor`** may escalate to High-tier.
Auto-escalate ONLY if: Security risk, Data loss risk, or Architecture violation.

## 7. Execution Modes

### Lean Mode (Default) 💚
Max 2 Evaluators/cycle. Self-Critique 1x. Ambiguity >40%. Refinement 1x. Shortest Correct Path.

### Deep-Cycle Mode 🔴
Trigger: "deep review", "enterprise audit", "full analysis".
Max 4 Evaluators. Critique 2x. High-tier auto-allowed. Auto-revert after task.

## 8. Decision Freeze 🧊
Plan selected → No re-evaluation unless user introduces new variable.

## 9. System Optimization Protocol 🚀
Lean Mode default. No redundant layers. No governance stacking.

## 10. Trigger Words
| Skill | Keywords |
| :--- | :--- |
| `deep-audit` | "audit", "review architecture", "check layers" |
| `security-scan` | "security check", "vulnerability" |
| `optimize-perf` | "slow", "optimize", "performance" |
| `advanced-architecture` | "DDD", "Event Sourcing", "Enterprise" |
| **Deep-Cycle Mode** | "deep review", "enterprise audit", "full analysis" |

