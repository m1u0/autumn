---
name: frame
description: Use when a request has meaningful ambiguity, irreversible stakes, or a premise worth sharpening before acting—or when the user asks to be grilled or challenged on a plan. Not for routine tasks where sensible defaults are reversible (act autonomously instead).
---

# Frame

Clarification should focus on decisions that meaningfully shape the outcome, leaving routine or easily reversible defaults to your own judgment.

## 1. Ground Before Asking

- **Resolve discoverable facts yourself.** Check files, configs, docs, or external sources before asking; delegate bulky lookups to a fresh read-only subagent.
- **Test cheap forks directly.** When a local, reversible probe or check settles a question faster than debating it, run it and report what you observed.
- **Restate tangled goals.** If the request is noisy or sprawling, open with a 1–2 sentence plain-English restatement so any misread surfaces immediately.

## 2. Sharpen the Premise (When It Earns Its Place)

If the request leaves obvious leverage on the table, briefly consider what a top practitioner would do differently—rawer primary material, a stronger external proof, or a sharper angle—and propose making the task **deeper, not bigger**.

## 3. Weigh What to Decide vs. Ask

- **Decide silently:** obvious, standard, or easily reversible choices. Pick the strongest default and briefly list non-obvious assumptions so the user can override if needed.
- **Ask the frontier:** use your judgment on which irreversible, taste-defining, or path-splitting decisions belong to the user, keeping each round to the frontier whose prerequisites are already settled (hold downstream questions whose answers depend on an open upstream fork).

## 4. Ask Default-Backed Questions

- Ask what genuinely merits user input rather than exhausting every branch; scale depth to the stakes and how thorough the user wants to be.
- Attach a **clear recommended default** to each question, phrased so "yes" accepts your defaults and lets you proceed immediately.
- Once the key decisions are settled, stop framing and execute (handing off to `run-to-done` or `hillclimb` if the work calls for it).
