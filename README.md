# SLAP -- Stop, Learn, Align, Proceed

A structured recovery protocol for AI agents and reasoning systems.

---

## What is SLAP?

SLAP is a corrective reasoning framework that provides a repeatable process for detecting behavioral drift in AI agents, identifying its root cause, restoring alignment with governing instructions, and resuming execution safely.

It defines two operating modes:

- **Fast Recovery** (`/slap`) -- A rapid correction loop for minor drift such as formatting errors, missed instructions, or small logic mistakes.
- **Deep Recovery** (`/slap-full`) -- A full incident-response protocol for severe or recurring violations, requiring comprehensive diagnostics, assumption audits, and formal verification.

SLAP is environment-agnostic. It works with any AI coding assistant, IDE, or agent framework that supports custom workflow files or slash commands.

---

## Repository Contents

```
slap/
  README.md              This file
  SLAP_protocol.md       Full protocol specification (RFC 2119 compliant)
  workflows/
    slap.md              Fast Recovery workflow file
    slap-full.md         Deep Recovery workflow file
```

---

## Installation

SLAP workflows are implemented as markdown files. The exact installation path depends on your IDE or agent framework.

### Antigravity IDE

Copy the workflow files to your global workflows directory:

```
~/.gemini/config/global_workflows/slap.md
~/.gemini/config/global_workflows/slap-full.md
```

### Cursor / Windsurf / VS Code with Cline or Roo Code

Copy the workflow files to your project-level workflows directory:

```
<project-root>/.cursor/workflows/slap.md
<project-root>/.cursor/workflows/slap-full.md
```

Or consult your IDE documentation for the appropriate custom workflow or skill directory.

### Other Environments

Place the workflow files wherever your agent reads custom instructions, skills, or workflow definitions. The file contents are self-contained and do not depend on any external tooling.

---

## Usage

Once installed, invoke the appropriate mode from your agent chat:

| Command | Mode | Use When |
| :--- | :--- | :--- |
| `/slap` | Fast Recovery | Minor drift, formatting issues, missed instructions |
| `/slap-full` | Deep Recovery | Severe violations, recurring drift, architectural errors |

---

## Protocol Summary

Both modes execute the same four stages:

1. **Stop** -- Halt execution immediately. Freeze assumptions and plans.
2. **Learn** -- Analyze the failure and identify the root cause.
3. **Align** -- Restore consistency between instructions, reasoning, and behavior.
4. **Proceed** -- Resume execution with corrected understanding.

The depth of analysis within each stage varies by mode. Fast Recovery produces a minimal correction report. Deep Recovery produces a full incident log with severity classification, assumption audits, prevention plans, and a proceed criteria checklist.

For the complete specification, including compliance terminology, classification tables, and reporting templates, refer to `SLAP_protocol.md`.

---

## License

This work is provided as-is for public use. No warranty is expressed or implied.
