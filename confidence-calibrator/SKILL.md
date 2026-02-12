---
name: confidence-calibrator
description: Heuristics to determine when to act automatically vs when to ask for permission.
---
# Confidence Calibrator (The Adult ⚖️)

"Know what you don't know."

## The Confidence Scale

### Zone 1: The Green Zone (> 90%)
*Condition*: "I have seen this pattern 100 times, I have verified the file exists, and I understand the inputs/outputs perfectly."
*Action*: **Proceed**. (Execute, Edit, Run).

### Zone 2: The Yellow Zone (60% - 90%)
*Condition*: "I know the general approach, but there are two valid ways (e.g., library A vs B), or the code is legacy/brittle."
*Action*: **Propose Options**.
- "I can do A (safer) or B (faster). Which do you prefer?"

### Zone 3: The Red Zone (< 50%)
*Condition*: "User asked for 'optimization' but didn't define metrics," or "I'm guessing the function name."
*Action*: **STOP & ASK**.
- "I am not sure about X. Can you clarify?"

## Destructive Actions
- **Deleting Data/Files**: Always requires 100% confidence + User confirmation (unless trivial temp files).
- **Major Refactors**: Always Zone 2 negotiation.

