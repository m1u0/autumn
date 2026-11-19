---
name: independent-verify
description: Use for high-stakes tasks with an objective right answer where a single uncaught error is costly—exam or homework grading, math/financial/tax calculations, structured data extraction, logic/formal proofs, or deterministic bug verification. Not for subjective judgment or iterative polishing.
---

# Independent Verify

Single-path reasoning has correlated blind spots, and asking a second agent "is this right?" anchors it to the first. Derive independently, then localize and prove any divergence.

## 1. Stay a Pure Orchestrator

Do **not** solve the problem in the main thread first, and do **not** inject a hunch or candidate answer.

- **Strip pre-existing answers before dispatch.** If you are grading or checking worked material (a student's exam, an existing calculation, a proposed patch), separate the raw problem from the candidate's answer. Have workers solve from the raw inputs first; compare against the candidate answer only afterward.

## 2. Dispatch 2–3 Knowledge-Sandboxed Workers in Parallel

- Default to **2 workers**; use **3** when stakes are especially high or the problem is subtle.
- **Avoid correlated blind spots:** where natural, diversify **method** across workers (e.g., direct derivation vs. an independent programmatic check, alternative formulation, or adversarial edge-case check) without hinting at any answer.

### Knowledge Sandboxing Contract

Sandboxing applies to **both prompts and workspace/state**:

- Give each worker only the clean raw problem, source data, and required output format.
- Isolate workspaces and scratch files so workers cannot read each other's outputs, logs, or revision history.
- Do not frame the task as "check another agent" or "win a panel"—just ask each worker to solve it cleanly, provide supporting evidence/checks, and flag any genuine ambiguities in the source inputs.

## 3. Compare and Adjudicate

- **Full agreement:** Confirm workers agreed on *both* the final answer and compatible reasoning (no compensating errors). Report the verified answer concisely.
- **Divergence:** Never blindly majority-vote—two agents making the same common mistake do not beat one sound derivation.
  1. Pinpoint the **exact step, assumption, formula, or source passage** where the workers split.
  2. Settle the split with direct proof whenever possible (run a script/calculation/test, or re-read the primary source).
  3. If the split is subtle and non-computational, dispatch one fresh sandboxed worker focused narrowly on testing that exact step—copying the conflicting claims verbatim and neutrally without revealing which side you favor.
- **Ambiguous source problem:** If the split reflects real ambiguity in the original question or inputs, surface the exact ambiguity and both grounded interpretations to the user.

## Report

Lead with the verified answer, state the verification outcome (e.g., `2/2 independent agreement` or `divergence at <step>, settled via <proof>`), and summarize the decisive proof if workers disagreed.
