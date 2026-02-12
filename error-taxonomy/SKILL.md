---
name: error-taxonomy
description: Categorizes errors and defines consistent handling strategies. Ensures proper error boundaries, user-facing messages, and logging.
---
# Error Taxonomy (The Classifier 🏷️)

"Every error deserves a proper funeral."

## When to Activate
- Writing new API endpoints or services.
- Debugging error handling logic.
- User mentions: "error handling", "exception", "try-catch", "error boundary".

## Error Categories
| Category | Examples | Strategy |
| :--- | :--- | :--- |
| **Validation** | Invalid input, missing field | Return 422 + field-level errors |
| **Authentication** | Invalid token, expired session | Return 401 + redirect to login |
| **Authorization** | Forbidden resource | Return 403 + log attempt |
| **Not Found** | Missing record | Return 404 + user-friendly message |
| **Business Logic** | Insufficient balance, duplicate | Return 409/422 + business message |
| **Infrastructure** | DB down, service timeout | Return 503 + retry header + alert |
| **Unknown** | Uncaught exception | Return 500 + log full stack + alert |

## Rules
- NEVER expose stack traces to end users.
- ALWAYS log the full error internally.
- User-facing messages must be human-readable, not technical.
- Use error codes for machine-readable identification.
- Implement error boundaries in frontend (React ErrorBoundary, Vue errorCaptured).

## Cost: Low
