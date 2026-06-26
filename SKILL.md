---
name: working-with-agents
description: Field-tested practices for getting reliable results out of agentic AI coding tools (Claude Code, Cursor, Codex, and similar). Use this whenever you are about to delegate a non-trivial coding or building task to an AI agent, when an agent's output is breaking things or drifting from what you asked, when you are setting up rules/guardrails for a project, or when you want to decide how much of a task to hand off versus keep. Consult it even if the user just says "the agent keeps messing this up" or "how should I prompt this" — the failure modes it addresses are usually upstream of the prompt itself.
---

# Working With Agents

A practitioner's playbook for delegating work to agentic AI. It distils recurring practices reported by people who work with agents regularly. The throughline: the human stays the engineer, and the agent executes. Your role shifts from writing the work to specifying, bounding, and verifying it — and that role does not get easier as the agent gets more capable, it gets more important.

Use the workflow below as the default. The reference files go deeper on specific situations.

> This skill is a working artifact intended to be tested and refined in use. Treat its claims as practitioner heuristics, not validated rules — try them, keep what holds up, and revise what doesn't.

## The core loop

Run every non-trivial delegation through these five stages. Skipping straight to "do this for me" is the single most common reason output disappoints.

1. **Plan before you prompt.** Decide what you want *before* the agent is involved. Write the goal, the constraints, and the rough shape of the solution in your own words first — a notebook, a scratch file, a spec. Agents are excellent at executing a plan and poor at deciding what the plan should be. If you outsource the thinking, you get a confident solution to the wrong problem.

2. **Make the agent restate the task.** Before it writes anything, have it ask you clarifying questions and confirm its understanding. A good opening instruction: *"Ask me questions until you're confident you understand the requirement, then propose a plan. Don't write code yet."* This catches misalignment while it's free to fix, not after 500 lines exist.

3. **Work in small iterations.** Approve one small step, review it, then release the next. Large single-shot outputs are hard to review and harder to unpick when they're wrong — and they usually are wrong in at least one place you'd never have chosen. Small diffs keep you in control and keep mistakes cheap.

4. **Verify the output, not the agent's reasoning.** You don't need to reconstruct how it got there — that's often genuinely hard and not worth it. You do need to confirm *what it produced* is correct: run it, read it, test it. Verification is the part you cannot delegate. (See `references/verification.md`.)

5. **Own the result.** Whatever ships under your name is your responsibility, regardless of who typed it. This isn't a moral nicety — it's the mindset that makes you verify properly. If you'd be embarrassed to defend a line in code review, you're not done.

## Set up guardrails once, reuse them everywhere

Front-loading rules so you don't re-explain yourself every session is one of the highest-leverage habits available.

- **Keep a reusable rules/skills file.** A standing set of project rules ("follow this structure," "don't touch these modules," "match the existing patterns," "ask before doing anything destructive") that you carry from task to task. Most agent tools support this natively (rules files, skills, system prompts, `CLAUDE.md`-style configs). Maintain it like code — every time the agent makes a mistake worth preventing, add a rule.
- **Constrain scope explicitly.** Tell it what *not* to do as clearly as what to do. "Only edit these files." "Don't refactor anything I didn't ask about." Unbounded agents wander.
- **Define structure up front.** Agents perform dramatically better when there's already a clean structure to work within. (More on why in `references/context-and-scope.md`.)

## Match the task to what agents are actually good at

Delegation is a judgment call, not a default. Calibrate by task type and complexity:

- **Great fit:** well-scoped tasks inside a clean, existing structure; boilerplate; mechanical refactors with explicit rules; first drafts and scaffolding you'll refine; getting oriented in an unfamiliar area.
- **Poor fit:** large tasks in messy or poorly structured codebases; complex work starting from scratch with no structure; anything where a subtle wrong answer is expensive and hard to detect; production-critical decisions where "faster" quietly becomes "worse."
- **The MVP trap:** an agent can get you to a working demo astonishingly fast. That speed does not mean the same approach gets you to production. Treat fast first results as a prototype to be hardened, not a finished thing.

When a task is too big or complex, don't hand it over whole. Break it into explicit, bounded steps and delegate them one at a time. "Turn this monolith into modules" fails; "extract this specific responsibility into a module, here are the constraints" works.

See `references/context-and-scope.md` for managing context windows, big projects, and why agents degrade as context grows.

## Communication habits that actually move the needle

- **Be specific over polite.** Manners don't change output quality; precision does. Spend your effort on clear requirements, not pleasantries.
- **Avoid showering the agent with praise mid-task.** Reflexively agreeing ("perfect, you're right!") can bias it toward defending its current answer instead of finding the better one — especially with long memory or persistent context. Stay neutral and evaluative.
- **Re-align rather than wrestle.** When output drifts, you have two clean moves: restate and realign, or start a fresh session. Don't pour tokens into patching a conversation that's gone off the rails — a clean restart with a better prompt is often faster.
- **Use models for what each does best.** Different tools and models have different strengths (raw coding, structured Q&A, large context, judging another agent's work). Running more than one and playing them to their strengths is often more effective than staying loyal to a single tool. (See `references/multi-agent.md`.)

## Keep your own skills alive

A quieter risk: delegate everything and you stop being able to evaluate the work — which destroys your ability to do stage 4. Deliberately keep doing some things yourself, especially in areas you want to stay sharp in. The goal is to stay the most capable person in the loop, not the least.

## Reference files

- `references/verification.md` — How to actually check agent output: version control as a safety net, reading vs. running, what to do when you don't understand the code, restricting edits, keeping a fallback copy.
- `references/context-and-scope.md` — Working with context windows, big projects, clean vs. messy codebases, breaking down large tasks, detecting context overflow.
- `references/multi-agent.md` — Using multiple agents/models together, agent-as-judge setups, dividing work for review, choosing the right tool per task.
