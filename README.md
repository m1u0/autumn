# autumn

A minimal, general-purpose agent skill set built around information boundaries, verification, and lightweight autonomy.

## Philosophy

Most agent setups micromanage *how* models think inside a turn—stacking brittle rules, rigid playbooks, and heavy multi-agent councils that become dead weight as models continue to improve in taste and competency.

`autumn` is designed with future, more capable models in mind, betting on what stays durable:

> **Don't micromanage reasoning inside a turn. Engineer information boundaries and exit predicates across turns and agents.**

- **General-purpose first.** Works across software engineering, deep research, strategic/game-theoretic analysis, writing, visual/3D design, math, and personal ops.
- **Goal-first, minimal steering.** State what done looks like and what boundaries hold; let the model use its judgment on how to get there.
- **Knowledge sandboxing & verification at the core.** Self-evaluation in a shared context is systematically optimistic, and single-path reasoning has correlated blind spots. Clean prompt *and* workspace boundaries fix both structurally.
- **Lean autonomy.** Bias toward action on reversible work, pause only on irreversible boundaries, and keep active agents small (1–3 max).
- **Model-invoked, low context load.** Five orthogonal skills with crisp trigger boundaries so always-on overhead stays tiny and agents pull the right trigger reliably.

## Structure

```text
autumn/
├── AGENTS.md                        # Minimal always-on posture (pure runtime signal)
└── skills/
    ├── hillclimb/SKILL.md           # Objective ratchet + sandboxed taste reviewer (with blind A/B)
    ├── independent-verify/SKILL.md  # 2-3 sandboxed parallel workers + proof-based divergence resolution
    ├── grounded-judgment/SKILL.md   # Primary-source practitioner research -> single best call
    ├── frame/SKILL.md               # Frontier clarification + premise sharpening
    └── run-to-done/SKILL.md         # Long-horizon / unattended execution with falsifiable exit predicates
```

## Skills at a Glance

| Skill | Core Lever | Example Uses |
| :--- | :--- | :--- |
| **`hillclimb`** | Frozen eval ratchet (objective), cold knowledge-sandboxed reviewer + blind A/B (taste), or both | Benchmarks, ML/SQL tuning, UI polish, Blender renders, essays, decks, strategy memos |
| **`independent-verify`** | 2–3 isolated workers (method-diverse where natural) with stripped answers; localize and prove any split | Exam/homework grading, math/financial/tax calcs, structured data extraction, deterministic bugs |
| **`grounded-judgment`** | Boots-on-the-ground primary sources -> taste-driven single recommendation | Strategy, game theory, career/business calls, frontier tech tradeoffs |
| **`frame`** | Silent reversible defaults + fact lookup + default-backed frontier questions | Ambiguous specs, strategic plans, sharpening shallow prompts |
| **`run-to-done`** | Falsifiable done predicate + real-artifact verification + lightweight audit trail | Unattended multi-step builds, migrations, research deliverables, ops workflows |

## Setup

`autumn` uses the standard `skills/<name>/SKILL.md` layout and works across harnesses. Paste this into your agent to install it:

```text
Install autumn from https://github.com/m1u0/autumn into this harness: install the skills under skills/ and merge AGENTS.md into my global agent instructions.
```

## Maintenance Discipline (Built for Deletion)

Every line in `autumn` must earn its keep:
1. **No-op test:** Does removing this sentence change what a frontier model does? If not, delete it.
2. **Context-load test:** Does this skill earn a permanent slot in always-on skill descriptions? If not, merge or delete it.
3. **Durability test:** Is this fixing a structural property of generation (context pollution, anchoring, unverified claims) or patching a temporary limitation? Keep only the former.
