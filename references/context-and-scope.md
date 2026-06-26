# Context and Scope

Most "the agent got worse" complaints are really context and scope problems. Agents don't degrade randomly — they degrade predictably as context grows, as structure disappears, and as tasks get too big to hold at once.

## Structure first, agent second

Agents perform far better when there's already something clean to build within. A well-organized, modular codebase gives the agent patterns to follow and boundaries to respect. A messy, unstructured one gives it nothing to anchor to — so it piles more mess on top of the mess.

Practical consequence:

- **On a clean codebase:** ask the agent to read the existing structure for context, then work within it. It will usually match your patterns well.
- **On a messy or poorly structured codebase:** expect trouble. Asking an agent to extend a tangled structure tends to produce more tangle, and "fix this part" often breaks several others. Impose structure first, or scope the agent to a small, isolated piece.

This is also why starting *from scratch* with no structure is hard mode. If you can, give the agent a skeleton — even a rough one — rather than a blank page.

## Break big tasks into bounded steps

A large task handed over whole is a recipe for drift. Decompose it and delegate one explicit step at a time, each with its own constraints.

- Bad: "Refactor this monolithic project into modules."
- Good: "Extract [this specific responsibility] into its own module. Don't change behavior. Here are the constraints. Show me the plan before editing."

Being explicit about *how* you want it done — the steps, the limits — is the difference between a clean result and a mess you have to untangle.

## Manage the context window deliberately

Agents have a finite context window. As it fills, they start to "forget" earlier instructions, lose track of what they've done, and contradict themselves. Large context also makes "go back and fix that earlier part" risky — the fix tends to break things elsewhere.

Tactics:

- **One session, one focused task.** Don't let a single conversation sprawl across many unrelated jobs. Scope tightly, finish, start fresh.
- **Detect overflow with a canary.** Plant a small standing instruction the agent should always honor — for example, have it open every reply with a fixed marker word, or restate a key constraint each turn. The moment it drops that marker, you know the context window has overflowed and it's no longer holding your earlier instructions. Time to restart.
- **Restart instead of fighting.** When context is exhausted, a fresh session with a tight prompt beats trying to wrestle a confused one back on track.

## Guardrails control context drift too

Standing rules and skills aren't only about quality — they're how you keep an agent on-target across a long or context-heavy task. Rules re-assert your constraints even as the conversation grows, so the agent has less room to wander as its memory of the original instruction fades. Maintain them actively: each time the agent does something you want to prevent, add a rule so it never happens twice.
