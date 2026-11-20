---
name: run-to-done
description: Use for long-horizon or unattended tasks where the user delegates an end-to-end outcome ("keep going until done", "handle this end-to-end", overnight work). Not for quick single-turn or ambiguous requests.
---

# Run to Done

Own the exit condition across a long or unattended run. Move decisively on reversible work, verify each milestone against reality, and leave a trail clear enough to trust on return.

## 1. Lock a Falsifiable Exit Predicate

Before diving in, define **done** as an observable check that cleanly passes or fails—not a vague state like "improved" or "handled."

- If an irreversible or direction-splitting ambiguity blocks defining done, resolve that frontier with the user first (using a framing skill if available); otherwise proceed with sensible defaults.
- **Signal the long run upfront.** Briefly tell the user you are starting an extended run (and what done looks like) before diving in, so they know to expect a long runtime.
- Sequence multi-part work into small, independently verifiable units, tackling the riskiest unknown first. Verify each unit before starting the next.

## 2. Own Mid-Run Obstacles

- Fix reversible side-issues, broken tooling, or intermediate blockers that stand in the way of the main goal rather than parking them for the user.
- Compose other available skills when subtasks call for them (e.g., iterative optimization/polish or independent verification for correctness-critical checkpoints).
- Pause **only** for irreversible external actions, a genuine preference fork no evidence can settle that changes the whole outcome, or a real dead end after trying concrete alternatives.

## 3. Hold Verification Discipline

- **Attack the premise on repeated failure.** If two attempts fail against the same check for the same underlying reason, stop patching—state the shared assumption and test it directly. If progress stalls across distinct failures or budget runs thin, checkpoint and pause rather than thrashing.
- **Keep worker bars tight.** When delegating a subtask, state the goal, clean inputs, and exact acceptance bar—and make clear that bar is the whole bar (no invented extra gates).
- **Cold final check.** Before declaring a substantial deliverable done, pass a clean snapshot of the final artifact (without diffs, logs, or rationale) plus the exit predicate to a fresh, knowledge-sandboxed reviewer subagent rather than self-certifying.

## 4. Keep a Lightweight Audit Trail

For runs the user will review asynchronously, keep a compact append-only decision log (e.g., a scratch or untracked TSV kept separate from deliverables, recording step, decision, why, evidence pointer, and status). Log major forks, assumptions, pivots, reverts, and verification pointers—skip trivial actions.

## Report

Lead with the exit predicate and verdict (`verified` | `blocked` | `inconclusive`), direct proof pointers, non-obvious decisions made for the user, the audit-log path if created, and anything still open.
