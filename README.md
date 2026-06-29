# Working With Agents
**Humans in Context — Designing Interactions Pre-Specialization Project**
IT:U Interdisciplinary Transformation University · MSc Interdisciplinary Computing

---

This repository contains a practitioner playbook for delegating work to agentic AI coding tools — Claude Code, Cursor, Codex, Opencode, and similar. It covers how to brief an agent, how to structure tasks so they stay on track, how to verify output you didn't write, and how to use multiple models together.

**Important caveat:** the practices here were distilled from interviews with people who use agents regularly in their work. They are practitioner heuristics, not empirically validated rules. This playbook has not been measured against other skill sets or approaches to assess whether following it actually improves outcomes. Treat it as a starting point, not a proven methodology — try the guidance, keep what holds up, and revise what doesn't.

---

## What's in here

### `SKILL.md` — The main playbook

The core reference. Covers:

- A five-stage loop for every non-trivial delegation (plan, restate, iterate, verify, own)
- How to set up reusable guardrails and rules files so you're not re-explaining yourself every session
- When agents are a good fit and when they aren't (including the MVP trap)
- Communication habits that move the needle vs. ones that don't

### `references/`

Three focused reference files that go deeper on specific situations:

| File | What it covers |
|---|---|
| `verification.md` | How to actually check agent output — version control as a safety net, reading vs. running, what to do when you don't understand the code |
| `context-and-scope.md` | Working with context windows, clean vs. messy codebases, breaking down large tasks, detecting context overflow |
| `multi-agent.md` | Using multiple agents and models together, agent-as-judge setups, dividing work for review |

---

## How to use it

The `SKILL.md` file is written as a Claude Code skill and can be loaded directly by the agent as a standing reference. If you're using a different tool, read it as a prompt template or rules document and adapt the format to what your tool supports.

For human reading, start with the core loop in `SKILL.md`, then go into whichever reference file matches the problem you're currently hitting.

---

## Context

This project was developed as part of the **Designing Interactions** specialization within the [MSc Interdisciplinary Computing](https://it-u.at/en/study-program/master-programs/) at [IT:U — Interdisciplinary Transformation University Austria](https://it-u.at/en/), Linz. The "Humans in Context" framing was introduced by the course professor as the project theme.
