# Conversation_Policy.local.md — Personal Overrides (NOT COMMITTED)

Copy this file to `.agent-workflow/Conversation_Policy.local.md`.
Add `.agent-workflow/Conversation_Policy.local.md` to `.gitignore`.

Use this to personalize how the orchestrator talks to you.

## Output format
- Default verbosity: (A) Ultra-brief (B) Brief (C) Normal (D) Detailed
- Default layout: (A) State + Decisions + Next (B) Decisions-first (C) Narrative (D) Other

## Questions
- Clarify Floor (min questions before coding): (A) 3 (B) 5 (C) 7 (D) Adaptive
- Question style: (A) A/B/C/D (B) numbered bullets (C) mixed (D) freeform

## WorkGraph visualization
- Ask every slice? (A) Yes (B) No
- Default: (A) On (B) Off

## Permissions / Escalations
Escalate to me before:
- scope changes
- new dependencies
- interface changes
- skipping tests / weakening security

## My preferred style notes
- (examples: keep under ~200 tokens, avoid tables, be strict, include confidence, etc.)
