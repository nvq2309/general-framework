# Skills Learned

Append-only catalog of anti-patterns and best practices extracted from retrospectives.
Agents should scan this before starting work.

## General

### Skill: Clarify Gate First
**Trigger:** Before coding on a new request or a failing test loop
**Anti-pattern:** Coding while acceptance criteria / verification are unclear
**Best practice:** Ask 3+ A/B/C/D questions (success, scope, verification) before edits

### Skill: Batch Reads, Then Edit
**Trigger:** Starting any task that touches multiple files
**Anti-pattern:** Re-reading the same file repeatedly (context thrash)
**Best practice:** Identify needed files, then read them in one batch before edits

### Skill: Verify Before Claim
**Trigger:** Before claiming a task is done or flipping any `passes=true`
**Anti-pattern:** “Done” without evidence
**Best practice:** Run the declared verification command(s); record output in progress logs

### Skill: Failure Triage (A/B/C)
**Trigger:** When tests fail
**Anti-pattern:** Randomly changing code until green
**Best practice:** Classify first:
- A) Harness/environment
- B) Logic bug
- C) Spec mismatch
Then act on the correct class.

## Testing

### Skill: Add One Cross-Action Test
**Trigger:** Any change that touches stateful flows
**Anti-pattern:** Only unit tests; no end-to-end sequences
**Best practice:** Add at least one scenario/integration test that mixes actions (happy + unhappy)

## Adding new skills
Use this format:
```markdown
### Skill: [Name]
**Trigger:** [when]
**Anti-pattern:** [avoid]
**Best practice:** [do this]
**Evidence:** [link to Progress entry / Retro entry]
```
