# .agent-workflow

Purpose: repository-local workflow assets for agentic SDLC (slice-based, evidence-driven, non-waterfall).

Quick start
1) Pick a workflow preset in `PRESETS.md` (once per repo).
2) Fill `Product_Description.md` and `PRD.md` minimally (Slice S01).
3) Keep `PRD.json` small and current (slice-by-slice).
4) Use `WorkGraph.json` to coordinate concurrent tasks (optional but recommended).
5) Log evidence:
   - subagents → `.agent-workflow/progress/<task-id>.<agent>.md`
   - orchestrator merges → `.agent-workflow/Progress.txt`

Key policies
- `Conversation_Policy.md`: how Sisyphus must talk to the operator (3-question rule, state snapshot, decision boundaries).
- `Workflow_Isolation.md`: how to run multiple parallel workflows without Progress bottlenecks.
- `Tools`: `tools/render_workgraph.mjs` generates `WorkGraph_visualize.md` (optional, default OFF).

Recommended repo root files
- `AGENTS.md` in repo root can point to this folder, but the workflow is tool-agnostic.
