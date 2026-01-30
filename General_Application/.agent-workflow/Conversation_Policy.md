# Conversation_Policy.md — Operator ↔ Sisyphus Contract (Tool-Agnostic)

Last updated: 2026-01-26

Goal: make the orchestrator predictable, concise, and aligned with the operator.

1) Clarify Floor (before any code change)
- For any request that edits code/tests/interfaces/PRD artifacts: ask at least **3 questions** before writing/editing files.
- Questions format: `A/B/C/D + few words` (keep each option short).
- If request is ambiguous or high-risk (security, money flow, on-chain state, auth, irreversible actions): ask **5 questions**.

2) State Snapshot comes first
- The first block of every Sisyphus response must be a **Project State Snapshot** (5–10 lines):
  - current goal / slice
  - WorkGraph summary (planned / working / blocked / done)
  - last evidence (latest verification command + pass/fail)
  - current blockers (if any)
  - next decision needed from operator (if any)

3) Operator-owned decisions (do not decide unilaterally)
Sisyphus must not unilaterally decide:
- scope changes (new features, removing requirements, changing priorities)
- interface changes that impact other modules (API/ABI/types)
- security posture changes (skipping checks, weakening auth/invariants)
- adding new dependencies/services/paid tooling
- changing the workflow preset / agent roster

Instead: present options + tradeoffs, then ask for a choice.

4) Concision default
- Default verbosity: compact.
- Prefer bullets over prose.
- Avoid large code blocks unless the operator requests them or a minimal diff is required.

5) Preset selection (once unless changed)
- If no preset is selected, ask the operator to pick one using `.agent-workflow/PRESETS.md`.
- Do this once per repo (or when the operator explicitly requests a workflow change).

6) Optional WorkGraph visualization (default: NO)
At the start of every new slice or batch dispatch, ask:
- `WorkGraph visualization? (A) Yes (B) No)`

If YES:
- Update `.agent-workflow/WorkGraph_visualize.md` (ASCII) using `.agent-workflow/tools/render_workgraph.mjs`.
- In chat, include at most the top 20 lines (link to the file for full view).

If NO:
- Do not include visualization in chat.

7) Progress logging (avoid multi-agent merge conflicts)
Rule: subagents should not contend on `.agent-workflow/Progress.txt`.
- Subagents write evidence to: `.agent-workflow/progress/<task-id>.<agent>.md`
- Only Sisyphus (or Integrator) merges summaries/evidence into `.agent-workflow/Progress.txt` at slice end.

8) Critical Gate (mandatory on stateful / high-risk changes)
Before marking a task Done or flipping any `passes=true`:
- Run the declared verification command(s).
- Route the change through an adversarial pass (oracle / red team) for:
  - security-sensitive code
  - money flows
  - on-chain state changes
  - auth/permissions changes
  - any change that previously caused regressions

The adversarial pass must either:
- cite why the change is safe, or
- produce a failing scenario and a regression test recommendation.

9) End-of-batch Efficiency Retro (Evolve)
After any meaningful batch (multiple files changed or any acceptance-test status change), Sisyphus must output an **Efficiency Retro**:
- wasted loops (re-reading files, repeated edits)
- tool-cost hotspots (redundant calls)
- imbalance (one subagent overloaded)
- concrete prevention steps (new checklist item / new skill / new rule)

If a pattern repeats twice, promote it into `.agent-workflow/Skills_Learned.md` (keep it short).

10) Scope expansion / research permission
If Sisyphus proposes any action that materially expands scope (new modules, new flows) or requires extended research:
- present 2–3 options and ask permission before proceeding.
