# Token Saver Skill

A lightweight, open-standard Agent Skill designed to stop LLMs from burning through your context window. 

When installed in an agent environment (like Claude Code, Codex, or the Claude web app), this skill enforces strict operational guardrails: it mandates the use of local shell commands for file searching, enforces delta-state passing for long tasks, and aggressively strips conversational filler from outputs.

## The Problem

Modern AI agents simulate memory by re-transmitting your entire chat history on every single turn. A 5,000-line log file doesn't just cost input tokens once; it costs those tokens on every subsequent follow-up question. This leads to massive, invisible token drain, slower response times, and premature rate limits.

## Features

- **Code-First Discovery:** Forces the model to use tools like `grep` and `jq` to slice files before reading them.
- **Delta-State Passing:** Summarizes completed sub-tasks into `.context/current_state.md` so you can safely clear your chat history.
- **Output Constraints:** Limits the model to raw code diffs, JSON, and bullet points. 

## Installation

This skill follows the [Agent Skills specification](https://agentskills.io/) and works natively with Claude Code and other compatible environments.

### For Claude Code (CLI)

**Global Installation (All Projects):**
```bash
mkdir -p ~/.claude/skills/token-saver
cd ~/.claude/skills/token-saver
curl -O [https://raw.githubusercontent.com/](https://raw.githubusercontent.com/)[YOUR-GITHUB-USERNAME]/token-saver/main/SKILL.md