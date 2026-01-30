# PRESETS.md — Workflow Presets (Tool-Agnostic)

Pick a preset once per repo (or only when you explicitly change the workflow).
Preset controls: agent roster, verification intensity, and when adversarial review is mandatory.

## Preset selection (A/B/C/D)

1) Primary output:
A) Architecture/spec  B) Backend/module  C) Frontend/UI  D) Full-stack feature

2) Risk level:
A) High (money/security/stateful)  B) Medium  C) Low  D) Experimental

3) Test investment:
A) Minimal  B) Normal  C) High  D) Extreme (fuzz/invariants/state-machine)

4) Speed vs quality:
A) Quality-first  B) Balanced  C) Cost/speed-first  D) Spike (throwaway ok)

## Recommended preset
- If 1A → `presets/system-designer.md`
- If 1B and 2A → `presets/backend-dev.md` (turn on Critical Gate)
- If 1C → `presets/frontend-dev.md`
- Default → `presets/full-stack.md`

## How to apply
- Record the chosen preset in `PRD.json` (suggested field: `project.workflow_preset`).
- Sisyphus must follow the preset until you explicitly change it.
