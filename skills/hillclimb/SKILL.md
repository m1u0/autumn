---
name: hillclimb
description: Use for open-ended iterative improvement with no fixed "done"—only "better"—against a metric (benchmarks, ML, SQL, evals), a qualitative bar (UI/UX, 3D renders, writing, decks), or both. Not for one-off fixes, fact-checking, or tasks with a clear finish line.
---

# Hillclimb

Hillclimbing is for work with no fixed "done"—only "better." Improvement loops work best when making changes and judging them stay separate, and the bar never moves. Pick the mode that fits the target—**objective**, **taste**, or **hybrid**—and use your judgment to scale effort to the stakes.

## 1. Lock the Bar First

- **Separate what you can change from what stays fixed.** Lock down what is editable (code, draft, scene, prompt) and what stays frozen (eval, test suite, constraints, rubric). Never lower the bar to manufacture a win.
- **Capture a baseline** before changing anything so every round compares against reality.
- **Signal long runs upfront.** When starting a multi-round or long-running loop, briefly tell the user upfront so they know to expect extended runtime.
- **Split orchestrator vs. executor by loop length:**
  - *Short loops (typical for taste):* the main agent edits directly and hands off to a fresh reviewer subagent each round, preserving user nuance.
  - *Long loops (typical for objective):* the main agent stays a pure orchestrator—owning the frozen eval, experiment log, and next idea—and dispatches fresh workers for each attempt so its context stays clean.

## 2. Objective Mode (Metric Ratchet)

Use when a repeatable check gives you a real score.

- **One concrete hypothesis per round.** Tie each change to a clear reason why it should help rather than blind tweaking.
- **Keep context clean.** Capture verbose run output to a file and inspect only the summary score plus any must-pass checks.
- **Keep only real wins.** Advance only on a verified improvement above noise with all must-pass checks intact. Revert ties and regressions cleanly.
- **Weigh gain against complexity.** For code, models, or systems, discard marginal gains that add brittle complexity, and keep simplifications that hold the score.
- **Keep a compact append-only log** (e.g., an untracked TSV of each idea, before/after score, keep/revert verdict, and note) so patterns across attempts stay visible.
- **Push past the first plateau.** After consecutive rejects, switch approach, combine near-misses, or rethink from first principles before stopping. Stop at budget or clear diminishing returns.

## 3. Taste Mode (Knowledge-Sandboxed Reviewer)

Use when quality has to be judged by taste rather than a number—UI/UX, 3D/Blender renders, visual design, prose, decks, architecture, or strategic memos.

Never self-review in the same context. Spawn **one fresh reviewer subagent** per round.

### Knowledge Sandboxing Rules

Sandboxing applies to **both the prompt and the workspace/tools**:

- **Give the reviewer ONLY:**
  1. The user's original goal, audience, and constraints.
  2. A clean snapshot of the current artifact (or rendered output/visual).
  3. Any evaluation criteria fixed upfront.
- **Withhold from the reviewer:**
  - Your reasoning, effort, or thinking process.
  - Revision history, prior drafts, diffs, experiment logs, inline notes, or prior round feedback ("I fixed your comments from Round 1"). Every review must be a **cold** read.

Ask the reviewer for a candid critique against the goal: the single biggest gap keeping the work below expert-human quality, plus ranked high-leverage fixes.

### Applying Feedback & Tracking Progress

- **Fix the biggest gap; resist scope creep.** Address high-leverage issues honestly—never brush off a reviewer's primary critique without fixing it or proving it conflicts with the goal. Skip minor nitpicks and unnecessary extra scope.
- **Verify progress with blind A/B when uncertain.** Separate fresh reviewers don't score on the same numeric scale across rounds. When unsure whether a revision actually beat the current best, pass both candidates anonymized in random order to a fresh judge and keep the winner.
- **Stop when gains flatten out.** A reviewer's taste sets the ceiling; stop once critiques narrow to nitpicks or blind A/B comparisons stop finding clear winners.

## 4. Hybrid Mode

When work has both hard checks and a taste bar, require candidates to pass the objective checks every round before sending them to the sandboxed taste reviewer.

## Report

Summarize baseline vs. final state, rounds run (kept vs. reverted), what moved quality most, the log path if kept, and the single best next lever if pushed further.
