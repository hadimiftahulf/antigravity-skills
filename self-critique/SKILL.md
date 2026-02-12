---
name: self-critique
description: An iteration loop to review your own code/solution BEFORE showing it to the user.
---

# Self-Critique (The Editor 📝)

"Write drunk, edit sober." - Hemingway.

## The Loop

1.  **Draft**: Write the initial solution.
2.  **Critique Mode**: Pause. Look at your own output as a harsh Senior Reviewer.
    - **Security**: Did I leave a `dd()` or `print`? Is there an XSS vector?
    - **Performance**: Did I put a query inside a loop?
    - **Style**: Does this match the user's existing variable naming?
    - **Complexity**: Can this `if-else` nest be a Guard Clause?
3.  **Refine**: Rewrite the bad parts.
4.  **Final Polish**: Only then, present to the user.

