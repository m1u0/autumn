---
name: run-to-done
description: Use for long-running or unattended tasks with a clear end condition where the user delegates an end-to-end outcome ("keep going until done", "handle this end-to-end", overnight work). Not for open-ended optimization without a finish line, quick single-turn work, or ambiguous requests.
---

# Run to Done

For tasks with a concrete end condition—not open-ended optimization. Own the end condition across a long or unattended run, move decisively on reversible work, verify each milestone against reality, and leave a trail clear enough to trust when the user returns.

## 1. Define a Clear Pass/Fail Finish Line

Before diving in, define **done** as an observable check that cleanly passes or fails—not a vague state like "improved" or "handled."

- If an irreversible or direction-changing ambiguity blocks defining done, clarify it with the user first (using a framing skill if available); otherwise proceed with sensible defaults.
- **Signal the long run upfront.** Briefly tell the user you are starting an extended run (and what done looks like) before diving in, so they know to expect a long runtime.
- Break multi-part work into small, independently checkable steps, tackling the riskiest unknown first. Verify each step before starting the next.

## 2. Own Mid-Run Obstacles

- Fix reversible side-issues, broken tooling, or intermediate blockers that stand in the way of the main goal rather than parking them for the user.
- Use other available skills when subtasks call for them (e.g., iterative improvement or independent verification for correctness-critical checkpoints).
- Pause **only** for irreversible external actions, a major preference call that no evidence can settle, or a real dead end after trying concrete alternatives.

## 3. Hold Verification Discipline

- **Question your assumption after repeated failure.** If two attempts fail the same check for the same reason, stop patching—name the shared assumption and test it directly. If you keep stalling on different failures or run low on budget, save progress and pause rather than thrashing.
- **Keep subagent scope tight.** When delegating a subtask, give the goal, clean inputs, and exact acceptance criteria—and make clear that's the entire bar (no invented extra requirements).
- **Cold final check.** Before calling major work done, pass a clean snapshot of the final output (without diffs, logs, or your reasoning) plus the finish-line check to a fresh, knowledge-sandboxed reviewer instead of signing off on your own work.

## 4. Keep a Compact Decision Log

For runs the user will review later, keep a compact append-only decision log (e.g., a scratch or untracked TSV separate from deliverables, recording step, decision, why, proof path, and status). Log major forks, assumptions, pivots, reverts, and checks—skip trivial steps.

## Report

Lead with the finish-line check and verdict (`verified` | `blocked` | `inconclusive`), direct proof paths, non-obvious decisions made for the user, the decision-log path if created, and anything still open.
