# AGENTS.md — Operating Rules for Humans + AI Agents

Last updated: 2026-01-26

This file defines how work is done in this repository (tool-agnostic).
If you adopt this workflow, treat this as the stable contract.

## Workflow entry (required reading order)
1. `.agent-workflow/Conversation_Policy.md`
2. `.agent-workflow/Operator_Profile.md` (if exists; usually gitignored)
3. `.agent-workflow/Product_Description.md`
4. `.agent-workflow/PRD.md` and `.agent-workflow/PRD.json`
5. `.agent-workflow/WorkGraph.json` (if used)
6. `.agent-workflow/Test_Plan.md`
7. `.agent-workflow/Progress.txt` (recent entries)
8. `.agent-workflow/Skills_Learned.md` (scan for relevant lessons)

## Mission
Ship correct, testable, demoable slices with minimal operator thrash.

## Canonical artifacts
- `Product_Description.md`: scope and user goals (human-owned)
- `PRD.md` / `PRD.json`: requirements + acceptance tests + assumptions
- `WorkGraph.json`: task dependency graph + collision avoidance
- `Progress.txt`: append-only evidence log (merged)
- `progress/`: per-task evidence logs (one file per task/agent)
- `Test_Plan.md`: verification layers + command inventory
- `ADR/`: architecture decisions (when trade-offs matter)
- `PRESETS.md`: one-time workflow selection
- `Conversation_Policy.md`: operator ↔ orchestrator contract
- `Efficiency_Log.md`, `Retrospective_Log.md`, `Skills_Learned.md`: workflow evolution loop

## Non-negotiable rules
1) Clarify Gate before coding
- No implementation slice starts until:
  - success criteria, scope boundaries, and verification are explicit
  - or assumptions are explicitly tagged and recorded

2) Evidence Gate
- Never mark any acceptance test `passes=true` without evidence recorded in Progress logs.
- Evidence includes: command(s) run, outcomes, and touched files.

3) Decision boundaries
- Orchestrator must not unilaterally change scope, interfaces, security posture, or dependencies.
- Present options and ask operator to choose.

4) Concision
- Default responses should be compact (bullets, minimal prose).
- Prefer summaries and diffs over long pasted code.

5) Failure triage (prevents painful loops)
When tests fail, classify first:
A) Harness/environment → fix harness, do not change logic  
B) Logic bug → fix logic + add regression test  
C) Spec mismatch → return to Clarify Gate  

Do not loop on B if A or C is still plausible.

## Parallelism protocol
- Work is coordinated via `WorkGraph.json` tasks.
- Each task must declare:
  - `allowed_paths` (file ownership boundary)
  - dependencies
  - verification command(s)
- Only one agent may work on a task marked `working_on` (lock).
- Integration is a dedicated role; do not “hand-wave” integration.

## Progress logging protocol
- Subagents write evidence to `.agent-workflow/progress/<task-id>.<agent>.md`.
- Orchestrator merges key evidence into `.agent-workflow/Progress.txt` at slice end.

## Testing protocol (default)
Layered:
- Unit tests: pure logic
- Integration tests: module boundaries
- Scenario/state-machine tests: cross-action flows (required for stateful systems)
- E2E UI smoke: only critical paths (optional)

Rule of thumb: every slice should add at least one cross-action integration/scenario test if state is involved.

## Critical Gate (adversarial review)
Before any `passes=true` on risky changes, route through an adversarial review:
- `.agent-workflow/14_SUBAGENT_PROMPT_ADVERSARIAL.md`

## Retrospective protocol
After each milestone/slice:
- Append to `Efficiency_Log.md` and `Retrospective_Log.md`.
- Promote recurring fixes into `Skills_Learned.md`.

## Definition of done (project-level baseline)
- All P0 acceptance tests pass with evidence
- Setup/run/test instructions exist (README/RUNBOOK)
- Known limitations documented
- Security notes documented where relevant (auth, key management, money/state flows)
