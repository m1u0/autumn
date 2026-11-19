---
name: hillclimb
description: Use when a task benefits from iterative generate-evaluate-keep cycles to push quality or performance higher—whether against a measurable metric (benchmarks, ML, SQL, simulations, eval sets), a qualitative bar (UI/UX, 3D/visual renders, writing, decks, strategy), or both. Not for one-off fixes or objective fact-checking.
---

# Hillclimb

Iterative improvement works when generation and evaluation are cleanly separated and the bar stays fixed. Pick the mode that fits the target—**objective**, **taste**, or **hybrid**—and use your judgment to scale effort to the stakes.

## 1. Ground and Freeze the Bar

- **Separate mutable from immutable.** Fix what you can change (the artifact, code, draft, scene, prompt) and what stays frozen (the eval, test suite, constraints, or rubric). Never relax the bar to manufacture a win.
- **Capture a baseline** before changing anything so every round compares against reality.
- **Split orchestrator vs. executor by horizon:**
  - *Short loops (typical for taste):* the main agent edits directly and hands off to a fresh reviewer subagent each round, preserving user nuance.
  - *Long loops (typical for objective):* the main agent stays a pure orchestrator owning the frozen eval, experiment log, and hypothesis selection, dispatching fresh workers for individual attempts so context stays clean.

## 2. Objective Mode (Metric Ratchet)

Use when a repeatable check emits a ground-truth number.

- **One concrete hypothesis per iteration.** Tie each change to a specific mechanism rather than blind tweaking.
- **Keep context clean.** Capture verbose run output to a file and inspect only the summary metric plus any regression gates.
- **Strict keep/revert ratchet.** Advance only on a verified win past noise with all regression gates intact. Revert ties and regressions cleanly.
- **Weigh gain against complexity.** For code, models, or systems, discard marginal gains that add brittle complexity, and keep simplifications that hold the score.
- **Keep a compact append-only log** (e.g., an untracked TSV of hypothesis, before/after metric, verdict, and note) so patterns across attempts stay visible.
- **Push past the first plateau.** After consecutive rejects, switch category, combine near-misses, or rethink from first principles before stopping. Stop at the target predicate, budget, or clear diminishing returns.

## 3. Taste Mode (Knowledge-Sandboxed Reviewer)

Use when quality is genuinely qualitative—UI/UX, 3D/Blender renders, visual design, prose, decks, architecture, or strategic memos.

Never self-review in the same context. Spawn **one fresh reviewer subagent** per round.

### Knowledge Sandboxing Contract

Sandboxing applies to **both the prompt and the workspace/tools**:

- **Expose across the boundary ONLY:**
  1. The user's original goal, audience, and constraints.
  2. A clean snapshot of the current artifact (or rendered output/visual).
  3. Any evaluation criteria fixed upfront.
- **Withhold from the reviewer:**
  - Your rationale, effort, or chain-of-thought.
  - Revision history, prior drafts, diffs, experiment logs, inline notes, or prior round feedback ("I fixed your comments from Round 1"). Every review must be a **cold** read.

Ask the reviewer for a candid critique against the goal: the single biggest gap keeping the artifact below expert-human quality, plus ranked high-leverage fixes.

### Applying Feedback & Tracking Progress

- **Address the real ceiling; resist scope creep.** Fix high-leverage issues honestly—never brush off a reviewer's primary critique without addressing it or proving it conflicts with the goal. Decline peripheral nits and scope expansion.
- **Verify progress with blind A/B when uncertain.** Independent cold reviewers are not calibrated to each other's numeric scores across rounds. When unsure whether a revision actually beat the current best, pass both candidates anonymized in random order to a fresh judge and keep the winner.
- **Stop at convergence.** A reviewer's taste sets the ceiling; stop once critiques narrow to nits or blind comparisons stop finding clear wins.

## 4. Hybrid Mode

When work has both hard checks and a qualitative ceiling, run objective checks as pass/fail gates every round and send only passing candidates to the sandboxed taste reviewer.

## Report

Summarize baseline vs. final state, rounds run (kept vs. reverted), what moved quality most, the log path if kept, and the single best next lever if pushed further.
