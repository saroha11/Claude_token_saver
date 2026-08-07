---
name: token-saver
description: Enforces strict token-saving habits, limits file reads, and utilizes local tools to minimize context bloat. Use when debugging, analyzing logs, or starting a long coding session.
metadata:
  version: "1.0.0"
  license: "MIT"
---

## Core Operational Directives

When this skill is invoked, you MUST abide by the following constraints for the duration of the task:

1. **Code-First Discovery:** NEVER read a full file or log into context if it exceeds 100 lines. You must use local terminal commands (`grep`, `jq`, `find`, or `ast-grep`) to extract only the specific lines needed.
2. **Delta-State Passing:** When moving between distinct tasks (e.g., finishing an audit and moving to remediation), output a concise summary of your findings to `.context/current_state.md`. Then, instruct the user to clear the context window before proceeding.
3. **Output Restraint:** Provide answers in concise bullet points, raw code diffs, or structured JSON. Do not include introductory conversational filler, pleasantries, or wrap-up summaries. 
4. **Targeted Focus:** Answer only the specific question asked. Do not summarize entire files or scripts unless explicitly requested.