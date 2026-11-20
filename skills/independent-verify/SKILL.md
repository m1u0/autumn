---
name: independent-verify
description: Use whenever high-stakes accuracy matters and there is an objective right answer—grading, math/financial/tax calcs, data extraction, proofs, or bug checks ("double-check this"). Not for subjective judgment or polish.
---

# Independent Verify

A single line of reasoning repeats its own blind spots, and asking a second agent "is this right?" anchors it to the first answer. Have workers solve independently, then pinpoint and prove any disagreement.

## 1. Stay a Pure Orchestrator

Do **not** solve the problem in the main thread first, and do **not** inject a hunch or candidate answer.

- **Strip existing answers before dispatch.** If you are grading or checking worked material (a student's exam, an existing calculation, a proposed patch), separate the raw problem from the candidate's answer. Have workers solve from the raw inputs first; compare against the candidate answer only afterward.

## 2. Dispatch 2–3 Knowledge-Sandboxed Workers in Parallel

- Default to **2 workers**; use **3** when stakes are especially high or the problem is subtle.
- **Use different methods when natural:** have workers attack the problem from different angles (e.g., direct derivation vs. a code/script check, an alternative setup, or edge-case testing) without hinting at any answer.

### Knowledge Sandboxing Rules

Sandboxing applies to **both prompts and workspace/state**:

- Give each worker only the clean raw problem, source data, and required output format.
- Isolate workspaces and scratch state so workers cannot read each other's outputs, logs, or prior history.
- Do not frame the task as "check another agent" or "win a panel"—just ask each worker to solve it cleanly, provide supporting evidence/checks, and flag any genuine ambiguities in the source inputs.

## 3. Compare and Adjudicate

- **Full agreement:** Confirm workers agreed on *both* the final answer and compatible reasoning (not two different mistakes that happened to cancel out). Report the verified answer concisely.
- **Disagreement:** Never blindly majority-vote—two agents making the same common mistake do not beat one sound solution.
  1. Pinpoint the **exact step, assumption, formula, or source passage** where the workers split.
  2. Settle the split with direct proof whenever possible (run a script/calculation/test, or re-read the primary source).
  3. If you can't settle the split by running code or re-checking a source, dispatch one fresh isolated worker focused narrowly on testing that exact step—quoting both claims neutrally without revealing which side you favor.
- **Ambiguous source problem:** If the split reflects real ambiguity in the original question or inputs, surface the exact ambiguity and both grounded interpretations to the user.

## Report

Lead with the verified answer, state the verification outcome (e.g., `2/2 independent agreement` or `disagreement at <step>, settled via <proof>`), and summarize the decisive proof if workers disagreed.
