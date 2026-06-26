# Verification

Verification is the part of agentic work you cannot delegate. The agent will make mistakes — sometimes obvious, sometimes things it doesn't even register *as* mistakes. Catching them is your job, and it's why you keep the editor open instead of just reading a summary.

## Use version control as your safety net

Commit before you let an agent loose, and commit in small increments as you go. Two reasons:

- **You can see exactly what changed.** Diffing the agent's edits against your last commit is the fastest way to spot something you didn't ask for — a deleted section, a renamed thing, an "improvement" you didn't want.
- **You can undo cleanly.** Some agent editors make it hard to revert their changes through the tool itself. Version control gives you a reliable way back regardless of what the tool supports.

If you're not using version control with an agent that edits files directly, you're working without a net.

## Keep a fallback copy of anything you can't afford to lose

Beyond commits, keep a known-good duplicate of critical work before a big agent operation. Cheap insurance against the agent mangling something in a way that's annoying to reconstruct.

## Read it, then run it

Two layers, both needed:

1. **Read the output.** Go through what it produced. For code, that means actually reading the functions, not skimming and assuming you know what they do — the bugs live precisely in the lines you skip because you're tired and it "looks fine."
2. **Run it.** Execute, test against real cases, confirm it does what it claims. "It compiles" is not "it's correct."

## Verify *what*, not necessarily *how*

You generally don't need to trace the agent's full reasoning path — modern agents pull on many things and reconstructing every step is often impractical. What matters is whether the *output* is right. Check the result against your requirements and your tests. Reserve deep how-did-you-get-here scrutiny for when the output is wrong and you need to debug it.

## When you don't understand the output

If the agent produces something you can't follow, don't ship it on faith. Options, in rough order of preference:

- Ask it to explain a specific file, function, or block — "explain what this function does and why."
- Ask a *different* model to explain it, as a cross-check.
- Take the time (even half an hour) to understand it yourself before accepting it.
- If it's doing something you don't understand and didn't ask for: **don't touch it / don't ship it.** Code you can't follow is a sound thing to reject by default — unexplained output you can't defend is a liability with your name on it.

## Restrict what the agent can edit when misunderstanding is likely

If you suspect your instruction could be misread, get specific about *where* and *what* to edit before releasing it. Narrow the blast radius: name the exact file and the exact change. The more room you leave, the more creative — and wrong — the agent can get.

## Tie responsibility to the artifact

A concrete habit worth adopting: when code is agent-generated, note it (in the commit message or a comment) *and* note that you reviewed it. This isn't bureaucracy — it forces the review to actually happen and keeps the line of responsibility visible to everyone downstream.
