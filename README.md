# autumn

A minimal, general-purpose agent skill set built around information boundaries, verification, and lightweight autonomy.

## Philosophy

Most agent setups micromanage *how* models think inside a turn—stacking brittle rules, rigid playbooks, and heavy multi-agent councils that become dead weight as models continue to improve in taste and competency.

`autumn` is designed with future, more capable models in mind, betting on what stays durable:

> **Don't micromanage how a model thinks inside a turn. Control what each agent can see and how results are checked across turns.**

- **General-purpose first.** Works across software engineering, deep research, strategic/game-theoretic analysis, writing, visual/3D design, math, and personal ops.
- **Goal-first, minimal steering.** State what done looks like and what constraints hold; let the model use its judgment on how to get there.
- **Knowledge sandboxing & verification at the core.** Reviewing your own work in the same context makes you overconfident, and a single line of reasoning repeats its own blind spots. Isolating what reviewers see—in both the prompt and the workspace—fixes both structurally.
- **Lean autonomy.** Bias toward action on reversible work, pause only on irreversible actions, and keep agent teams small (1–3 max).
- **Tiny context footprint, flexible triggers.** Five non-overlapping skills with clear triggers so always-on overhead stays tiny—whether called directly by the user or picked up by the agent.

## Structure

```text
autumn/
├── AGENTS.md                        # Short always-on guidelines
└── skills/
    ├── hillclimb/SKILL.md           # Open-ended improvement loops (metrics, taste, or both)
    ├── independent-verify/SKILL.md  # 2–3 isolated workers solving independently, then proving disagreements
    ├── grounded-judgment/SKILL.md   # Primary-source research -> one clear recommendation
    ├── frame/SKILL.md               # Clarify key upstream decisions before acting
    └── run-to-done/SKILL.md         # Long or unattended runs with a concrete end condition
```

## Skills at a Glance

| Skill | How It Works | Example Uses |
| :--- | :--- | :--- |
| **`hillclimb`** | Open-ended improvement (no "done," only "better"): keep only verified wins against a fixed eval, a fresh isolated reviewer + blind A/B, or both | Benchmarks, ML/SQL tuning, UI polish, Blender renders, essays, decks, strategy memos |
| **`independent-verify`** | 2–3 isolated workers using different approaches with existing answers stripped out; pinpoint and prove any disagreement | Exam/homework grading, math/financial/tax calcs, structured data extraction, deterministic bugs |
| **`grounded-judgment`** | Check primary sources from active practitioners -> commit to one best recommendation | Strategy, game-theoretic analysis, career/business calls, frontier tech tradeoffs |
| **`frame`** | Look up facts first + run cheap checks + ask upstream questions with recommended defaults | Ambiguous specs, strategic plans, sharpening shallow prompts |
| **`run-to-done`** | Tasks with a concrete end condition: observable pass/fail check + real-output verification + compact decision log | Unattended multi-step builds, migrations, research deliverables, ops workflows |

## Setup

`autumn` uses the standard `skills/<name>/SKILL.md` layout and works across harnesses. Paste this into your agent to install it:

```text
Install autumn from https://github.com/m1u0/autumn into this harness: install the skills under skills/ and merge AGENTS.md into my global agent instructions.
```

## Built for Deletion

Every line in `autumn` must earn its keep:
1. **Behavior test:** Does removing this sentence change what a strong model does? If not, delete it.
2. **Context cost:** Does this skill earn a permanent slot in always-on skill descriptions? If not, merge or delete it.
3. **Structural vs. temporary:** Does this fix a structural weakness of how models work (context clutter, anchoring, self-review bias, unverified claims) or patch a temporary flaw? Keep only the former.
