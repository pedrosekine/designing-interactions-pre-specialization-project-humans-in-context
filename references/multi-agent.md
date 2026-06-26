# Multiple Agents and Models

Experienced users rarely stay loyal to one tool. They treat models as a toolkit and play each to its strengths. You don't need elaborate orchestration to benefit — even informally mixing tools meaningfully improves results.

## Pick the tool for the job

Different models and tools genuinely differ. Rough, opinionated starting points (verify against current tools, which change fast):

- **Heavy coding / agentic editing:** a strong dedicated coding agent.
- **Quick structured Q&A, explanations, small lookups:** a chat model with good structured output and follow-up memory.
- **Huge / whole-repository context:** a model with a very large context window when you need it to see everything at once.

The skill is knowing what each is good at and routing work accordingly — not finding one tool that does everything.

## Use one agent to check another

A practical pattern: have a second agent judge the first one's output. Give the reviewer your rules and constraints explicitly — "here are my guardrails and standards; evaluate what this other agent produced" — and let them go back and forth fixing each other's issues. An independent model is more likely to catch what the original missed than the original is to catch its own.

This complements human verification; it doesn't replace it. The judge agent can surface issues fast, but you still own the final check.

## Divide work for reviewable chunks

When an agent produces more than you can review in one sitting (say, changes across many files), use an agent to *divide the work into pieces* for you, then review piece by piece. You stay in control of verification without drowning in a single giant diff. The point isn't to review less — it's to make thorough review humanly possible.

## Combine, don't collect

Running multiple tools is a means, not an end. The value comes from complementing them — using one to accelerate, another to check, another to explain — so the whole is faster and more reliable than any single one. Switching tools constantly without a reason just adds overhead. Have a reason each time.
