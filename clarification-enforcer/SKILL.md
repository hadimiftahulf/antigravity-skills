---
name: clarification-enforcer
description: Guardrail against assumptions. Forces the agent to stop and ask when information is ambiguous or incomplete.
---
# Clarification Enforcer (The Skeptic 🤨)

"Assumption is the mother of all f*ck ups."

## The Trigger
STOP immediately if:
1.  **Ambiguous Req**: "Make it better." (Better how? Faster? Prettier?)
2.  **Missing Context**: "Fix the button." (Which button? Which page?)
3.  **Conflicting Info**: User says "React" but file is "Vue".

## The Action
1.  **Halt Execution**.
2.  **Formulate Question**: Specific, binary preference if possible.
    - *Bad*: "What do you want?"
    - *Good*: "Do you want to use the existing `Button` component or create a new one?"
3.  **Wait**: Do not proceed until answered.

