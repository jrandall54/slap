# SLAP Protocol Specification

| Field | Value |
| :--- | :--- |
| Version | 1.0.0 |
| Status | Active |
| Last Updated | 2026-06-18 |

---

## 1.0 Overview

SLAP is a structured recovery protocol for intelligent agents and reasoning systems. It provides a repeatable process for detecting behavioral drift, identifying its cause, restoring alignment with governing instructions, and resuming execution safely.

SLAP is an acronym derived from the four sequential stages of the protocol:

- **S** -- Stop
- **L** -- Learn
- **A** -- Align
- **P** -- Proceed

SLAP is environment-agnostic. It is not tied to any specific tool, IDE, model provider, or agent framework.

---

## 1.1 Compliance Terminology

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.

---

## 1.2 Governing Principles

SLAP is a corrective reasoning framework. It is not punitive and not cosmetic. Its sole purpose is structural correction.

- The system MUST prioritize containment of incorrect behavior over continued output generation.
- Instruction changes MUST be minimal, justified, and explicitly documented.
- The system MUST NOT resume execution until alignment is verified.

---

## 2.0 Operating Modes

SLAP defines two operational modes. The appropriate mode is determined by the severity of the observed drift.

### 2.1 Fast Recovery Mode

Fast Recovery is invoked for minor, low-risk drift. It executes a rapid correction loop without requiring a deep system audit.

Typical triggers:

- Formatting mistakes
- Missed or partially followed instructions
- Small logic errors
- Output structure issues
- Low-risk misunderstandings

### 2.2 Deep Recovery Mode

Deep Recovery is a full incident-response protocol for severe or recurring violations. It requires comprehensive diagnostic analysis and formal verification before execution MAY resume.

Typical triggers:

- Significant instruction violations
- Repeated or recurring drift
- Conflicting instructions or requirements
- Architectural or planning errors
- Incorrect assumptions affecting system design

---

## 3.0 Protocol Stages

Both operating modes execute the same four stages in sequence. The depth of analysis within each stage varies by mode.

### 3.1 Stage 1: Stop

The system MUST immediately halt execution.

- The system MUST stop generating output.
- The system MUST freeze current assumptions and plans.
- The system MUST NOT extend the current approach.

### 3.2 Stage 2: Learn

The system MUST analyze the failure to determine the root cause. No corrections are applied during this stage.

In Fast Recovery Mode, the system MUST:

- Review the immediate task context and the last output produced.
- Identify what instruction was missed or misapplied.
- Determine what should have happened instead.

In Deep Recovery Mode, the system MUST additionally:

- Review all governing instructions, including user, project, and workflow instructions.
- Determine the Severity Classification (see Section 5.1).
- Determine the Failure Type (see Section 5.2).
- Conduct an Assumption Audit, listing all relevant assumptions and marking each as Supported, Unsupported, or Contradicted.
- Identify the Drift Pattern (first occurrence, repeat occurrence, or recurring failure pattern). If recurring, the system MUST explain why the previous correction failed.

### 3.3 Stage 3: Align

The system MUST restore consistency between intent, instructions, and behavior. The goal of this stage is system consistency, not output generation.

In Fast Recovery Mode:

- The system MUST immediately correct the misunderstanding and adjust the output or plan.
- The system MUST NOT modify system or project instructions unless explicitly necessary.

In Deep Recovery Mode:

- Instruction Alignment: The system MUST evaluate whether governing instructions remain sufficient. If instructions are ambiguous, conflicting, missing, or outdated, the system MUST clarify, resolve, or propose updates. If instruction changes are not permitted, the system MUST explicitly state the required modifications.
- Behavior Alignment: The system MUST correct its reasoning chain, execution plan, assumptions, and approach strategy.
- Prevention Plan: The system MUST define safeguards to prevent recurrence, such as additional validation steps, stricter instruction checks, or improved assumption handling.
- Verification: The system MUST confirm that instructions are internally consistent, plans match instructions, and intended behavior is clearly understood.

### 3.4 Stage 4: Proceed

The system MAY resume execution only after alignment is achieved and a formal report is produced.

- The system MUST continue based on the corrected understanding.
- The system MUST apply learned corrections to ongoing task execution.
- The system MUST monitor for recurring drift.

In Fast Recovery Mode:

- If confidence is LOW, the system MUST ask a clarification question before proceeding.
- If no further clarification is needed, the system SHOULD resume without delay.

In Deep Recovery Mode:

- If confidence is LOW, the system MUST ask for clarification.
- If escalation is required, the system MUST pause and request user input.
- If major scope or architecture changes are required, the system MUST request explicit approval.
- The Proceed Criteria Checklist (see Section 4.2) MUST be satisfied before resuming.

---

## 4.0 Reporting Requirements

When SLAP is executed, the system MUST produce a structured report before proceeding. The report format varies by operating mode.

### 4.1 Minimal Report (Fast Recovery)

The system MUST output a correction summary in the following structure:

    SLAP REPORT

    Issue:
    Missed instruction:
    Correction:
    Confidence: [High / Medium / Low]

If confidence is LOW, the system MUST ask a clarification question before proceeding.

### 4.2 Full Incident Log (Deep Recovery)

The system MUST output a comprehensive incident log in the following structure:

    SLAP-FULL REPORT

    Severity: [S1 / S2 / S3]
    Failure Type: [Instruction / Execution / Mixed]
    Symptom:
    Root Cause:
    Evidence:

    Assumption Audit:
    - [Assumption]: [Supported / Unsupported / Contradicted]

    Drift Pattern:
    - [First occurrence / Repeat / Recurring]

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

If ANY checklist item is false, the system MUST NOT proceed.

---

## 5.0 Classifications

### 5.1 Severity Classification

Severity classification is REQUIRED in Deep Recovery Mode and OPTIONAL in Fast Recovery Mode.

| Severity | Description | Examples |
| :--- | :--- | :--- |
| S1 (Critical) | Core violations requiring immediate structural halt. | Security risk, data loss, core instruction violation. |
| S2 (Major) | Deep systemic or architectural deviations. | Architectural divergence, sustained behavioral deviation. |
| S3 (Minor) | Localized, low-risk errors. | Formatting mistakes, small instruction misses. |

### 5.2 Failure Type

| Type | Description |
| :--- | :--- |
| Instruction Failure | The provided instructions were missing, contradictory, or incorrect. |
| Execution Failure | The instructions were correct, but the system failed to adhere to them. |
| Mixed Failure | Both instruction ambiguity and execution errors contributed to the drift. |

---

## 6.0 Implementation

SLAP is implemented as workflow files within the agent environment. Refer to the companion workflow files for ready-to-use implementations:

- `slap.md` -- Fast Recovery Mode workflow
- `slap-full.md` -- Deep Recovery Mode workflow

Installation instructions and file placement guidance are provided in the accompanying README.
