---
description: Full diagnostic and recovery protocol for serious agent drift.
---

# SLAP-FULL (Deep Recovery Mode)

This workflow is triggered via `/slap-full`.

## Purpose
Use SLAP-FULL when there is significant instruction violation, recurring drift, or architectural errors. This is a full incident-response protocol.

---

# STEP 1: STOP
Immediately halt execution.
* Stop generating output and pause all progress.
* Freeze current assumptions and plan.

---

# STEP 2: LEARN (FULL DIAGNOSTIC)
Perform a full analysis. Determine:
* Severity: [S1 (Critical) / S2 (Major) / S3 (Minor)]
* Failure Type: [Instruction / Execution / Mixed]
* Drift Pattern: [First occurrence / Repeat / Recurring]

Conduct an Assumption Audit (list assumptions and whether they are Supported / Unsupported / Contradicted).

---

# STEP 3: ALIGN (SYSTEM-LEVEL FIX)
* **Instruction Alignment**: Clarify, resolve, or propose updates to instructions.
* **Behavior Alignment**: Correct reasoning chain and execution plan.
* **Prevention Plan**: Define safeguards to prevent recurrence.
* **Verification**: Confirm consistency between intent, instructions, and behavior.

---

# STEP 4: REPORT (FULL INCIDENT LOG)
Output the following structured report (do not use markdown formatting inside code blocks for the report to ensure it renders correctly):

    SLAP-FULL REPORT
    
    Severity: [S1 / S2 / S3]
    Failure Type: [Instruction / Execution / Mixed]
    Symptom: 
    Root Cause: 
    Evidence: 
    
    Assumption Audit:
    - [Assumption]: [Supported / Unsupported / Contradicted]
    
    Drift Pattern:
    - [Pattern analysis]
    
    Instruction Alignment:
    - Changes made: 
    - Changes recommended: 
    - Justification: 
    
    Behavior Alignment:
    - Corrections applied: 
    
    Prevention Plan:
    - Measures added: 
    
    Verification:
    - Alignment status: 
    
    Escalation Required: [YES / NO]
    - If YES: [Explanation]
    
    Confidence: [High / Medium / Low]
    - Reason: 
    
    Proceed Criteria Checklist:
    [ ] Root cause identified
    [ ] Evidence collected
    [ ] Instructions reviewed
    [ ] Alignment completed
    [ ] Prevention defined
    [ ] Confidence acceptable

If ANY checklist item is false, do not proceed.

---

# STEP 5: PROCEED (CONTROLLED RESUME)
* If Confidence is LOW -> ask clarification.
* If Escalation = YES -> pause and request user input.
* If major scope changes required -> request approval.

Otherwise, resume execution with corrected understanding.
