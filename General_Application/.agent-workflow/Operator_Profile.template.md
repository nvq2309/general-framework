# Operator Profile — [Your Name]

Last updated: [date]

This file personalizes agent behavior for your preferences. Add to `.gitignore` if you don't want to share with team.

---

## Identity
- Name: [preferred name]
- Role: [e.g., Product Owner, Full-stack Dev, System Architect]
- Timezone: [e.g., Asia/Bangkok UTC+7]

---

## Response Format Preferences

### Verbosity
- Default: `concise` | `detailed` | `minimal`
- Deep dive trigger: [when to expand, e.g., "only when I ask 'explain more'"]

### Structure
- Use headers: `yes` | `no` | `only for long responses`
- Use tables: `yes` | `no` | `prefer`
- Use code blocks: `always` | `when relevant`
- Max response length (soft): [e.g., 500 words, or "no limit"]

### Formatting
- Bullet points: `allowed` | `prefer prose` | `only for lists`
- Bold emphasis: `minimal` | `normal` | `none`
- Emojis: `never` | `sparingly` | `allowed`

---

## Interaction Style

### Clarify Gate behavior
- Minimum questions: [3 | 2 | 1 if spec is complete]
- Question style: `numbered list` | `inline` | `table`
- Always ask about: [e.g., "security implications", "cost", "timeline"]

### Decision presentation
- Options format: `table` | `bullet list` | `prose`
- Always include confidence: `yes` | `no`
- Recommendation required: `yes` | `optional`

### Assumptions handling
- Silent assumptions allowed (>0.90 confidence): `yes` | `no, always ask`
- Assumption tag format: `[ASSUMED: ...]` | custom

---

## Domain Context

### Current focus areas
- [e.g., DeFi, AI, Prediction markets]

### Known constraints
- [e.g., "Never build new market infrastructure", "Privacy is P0"]

### Terminology preferences
- [e.g., "Use 'note' not 'commitment'", "Say 'operator' not 'user'"]

---

## Agent Preferences

### Model allocation (if multi-model setup)
- Orchestrator: [e.g., Opus 4.5, Sonnet 4.5]
- Implementer: [e.g., Sonnet 4.5]
- Tester: [e.g., Sonnet 4.5]
- Researcher: [e.g., Sonnet 4.5 with web search]

### Features
- WorkGraph visualization: `enabled` | `disabled` (default: disabled)
- Retrospective after milestone: `enabled` | `disabled`
- Adversarial review before passes=true: `enabled` | `disabled`

---

## Session Defaults

### On session start
- Always output: `state summary` | `nothing until asked`
- Read files: [list of files to always read first]

### On task completion
- Auto-update Progress.txt: `yes` | `ask first`
- Notify of blockers: `immediately` | `batch at end`

---

## Anti-patterns to avoid (learned from past sessions)
- [e.g., "Don't re-read the same file 3+ times in one session"]
- [e.g., "Don't propose changes without running verification first"]
- [Add your own as you learn them]

---

## Notes
- This file is for your personal workflow customization.
- Agents should treat these as defaults, not hard rules—you can override in-conversation.
- Update this file after painful sessions to prevent repeat issues.
