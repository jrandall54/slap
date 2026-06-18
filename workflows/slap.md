---
description: Fast recovery protocol for minor agent drift.
---

# SLAP (Fast Recovery Mode)

This workflow is triggered via `/slap`.

## Purpose
Use SLAP when the agent exhibits minor drift (e.g., formatting mistakes, missed instructions, output structure issues). This is a fast correction loop, not a full audit.

---

# STEP 1: STOP
Immediately pause current execution.
* Do not continue generating output.
* Freeze assumptions.

---

# STEP 2: LEARN
Identify the issue quickly.
* Review user instruction, context, and last output.
* Determine what was wrong and what should have happened.

---

# STEP 3: ALIGN
Correct behavior immediately.
* Fix misunderstanding and adjust output.
* Do NOT modify system or project instructions unless explicitly necessary.

---

# STEP 4: REPORT
Output the following structured summary (do not use markdown formatting inside code blocks for the report to ensure it renders correctly):

    SLAP REPORT
    
    Issue: 
    Missed instruction: 
    Correction: 
    Confidence: [High / Medium / Low]

If confidence is LOW, ask a clarification question before proceeding.

---

# STEP 5: PROCEED
Resume execution immediately using the corrected understanding.
