# Prompt-library

Versioned library of reusable AI prompts and Cursor rules.

Use **prompts** for a single task in chat. Use **rules** as project-level Cursor instructions. Authoring conventions live in [RULES.md](RULES.md).

## Layout

```text
.
├── RULES.md              # How to write and maintain entries
├── templates/            # Skeletons for new files
├── prompts/              # Task prompts, by category
└── rules/                # Reusable Cursor rules, by category
```

Categories (shared by `prompts/` and `rules/`):

| Category | When to reach for it |
| --- | --- |
| [coding](prompts/coding/) | Implement, refactor, debug, tests |
| [review](prompts/review/) | Code review, security review, PR feedback, proposal critique |
| [planning](prompts/planning/) | Specs, architecture, task breakdown, thinking sessions |
| [writing](prompts/writing/) | Docs, presentations, hierarchical restructuring |
| [research](prompts/research/) | Explain, compare, investigate, briefings |
| [agents](prompts/agents/) | System prompts and agent instructions |
| [job-search](prompts/job-search/) | Resume rewrites, role targeting, outreach, application strategy |

## Use a prompt

1. Open the category folder (or its `README.md` index).
2. Copy the **Prompt** fenced block.
3. Replace `{{variable_name}}` placeholders.
4. In Cursor, you can `@`-mention the file instead of pasting.

## Add a prompt or rule

1. Copy [templates/prompt.md](templates/prompt.md) or [templates/rule.mdc](templates/rule.mdc).
2. Save it under the matching category with a kebab-case name.
3. Follow the checklist in [RULES.md](RULES.md).
4. Add a row to that category’s `README.md`.

## Example

- Prompt: [prompts/review/code-review.md](prompts/review/code-review.md)
- Rule: [rules/coding/prefer-small-diffs.mdc](rules/coding/prefer-small-diffs.mdc)
