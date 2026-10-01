# Prompt Library Rules

These rules govern how this repository is organized and how prompts and Cursor rules are written, updated, and used. Follow them when adding or changing anything in this library.

## Purpose

This repository is a versioned library of reusable AI prompts and Cursor rules.

- **Prompts** are copy-paste (or `@`-mention) instructions for a single task.
- **Rules** are reusable Cursor rule files (`.mdc`) that can be dropped into a project's `.cursor/rules/` directory.
- Git is the source of truth. Do not encode “latest” or “final” in filenames.

## Layout

```text
.
├── README.md                 # How to use the library
├── RULES.md                  # This file: authoring and usage rules
├── templates/
│   ├── prompt.md             # Canonical prompt skeleton
│   └── rule.mdc              # Canonical Cursor rule skeleton
├── prompts/                  # Task prompts, grouped by category
│   ├── coding/
│   ├── review/
│   ├── planning/
│   ├── writing/
│   ├── research/
│   ├── agents/
│   └── job-search/
└── rules/                    # Reusable Cursor rules, grouped by category
    ├── coding/
    ├── review/
    ├── planning/
    ├── writing/
    ├── research/
    ├── agents/
    └── job-search/
```

Do not add a new top-level folder without updating this section and `README.md`.

## Categories

| Folder | Use for |
| --- | --- |
| `coding/` | Implement, refactor, debug, generate tests |
| `review/` | Code review, security review, PR feedback, proposal or argument critique |
| `planning/` | Specs, architecture, task breakdown, structured thinking sessions |
| `writing/` | Docs, presentations, hierarchical restructuring |
| `research/` | Explain, compare, investigate, briefings |
| `agents/` | System prompts and agent instructions |
| `job-search/` | Resume rewrites, role targeting, outreach, application strategy |

Put a file in the category that matches **when you would reach for it**, not the domain of the code it happens to mention. If none fit, add a category: create the folder, add a `README.md` index, and update this table.

## Naming

- Use **kebab-case** filenames: `code-review.md`, `prefer-small-diffs.mdc`.
- One prompt or rule per file.
- The filename (without extension) must match the last segment of the `id` in frontmatter.
- Do not put version numbers, dates, or words like `final`, `new`, or `copy` in filenames.
- Keep names verb- or outcome-oriented: `implement-feature.md`, not `my-prompt.md`.

## Prompt files

Every prompt lives under `prompts/<category>/<name>.md` and starts with YAML frontmatter.

### Required frontmatter

```yaml
---
title: Human-readable title
id: category/kebab-name
category: coding
tags: [tag-one, tag-two]
status: active
version: 1
---
```

| Field | Rules |
| --- | --- |
| `title` | Short, sentence case, no trailing period |
| `id` | `<category>/<filename-without-extension>` |
| `category` | Must match the parent folder name |
| `tags` | Lowercase kebab-case; 2–6 tags |
| `status` | `draft`, `active`, or `deprecated` |
| `version` | Integer. Increment on breaking changes to the prompt text |

Optional fields: `models` (list), `created` (`YYYY-MM-DD`), `updated` (`YYYY-MM-DD`).

### Required sections

Use these headings, in this order:

1. **Purpose** — one or two sentences: what this prompt does.
2. **When to use** — situations where it is the right tool. Include a “when not to use” line if the prompt is easy to misuse.
3. **Inputs** — named variables the user must fill in.
4. **Prompt** — the exact text to send to the model. Put it in a fenced code block.
5. **Output** — the shape of a good response (format, sections, constraints).

Optional sections after **Output**: **Examples**, **Notes**.

### Variables

- Declare every placeholder in **Inputs**.
- Use double-curly syntax in the prompt body: `{{variable_name}}`.
- Names are `snake_case`.
- Do not leave undeclared placeholders in the **Prompt** block.
- Do not hard-code secrets, private URLs, or personal data. Pass those as inputs at use time.

### Prompt text style

- One job per prompt. Split combined workflows into separate files.
- Lead with the goal, then constraints, then the output contract.
- Write instructions the model can follow without extra conversation.
- Prefer checklists and explicit “do / do not” over vague quality adjectives.
- Keep the copyable **Prompt** block self-contained. Do not rely on text outside that block being pasted.

## Rule files

Every reusable Cursor rule lives under `rules/<category>/<name>.mdc`.

### Required frontmatter

```yaml
---
description: One sentence on when this rule applies.
globs:
alwaysApply: false
title: Human-readable title
id: category/kebab-name
category: coding
tags: [tag-one]
status: active
version: 1
---
```

Set `alwaysApply: true` only when the rule should load in every conversation. Otherwise set `globs` to the file patterns it should attach to (for example `**/*.{ts,tsx}`).

The body is the rule text itself — what the agent should do — not a wrapper explaining how to install it. Installation belongs in `rules/README.md` and the category index.

## Indexes

Each category folder has a `README.md` that lists its files:

```markdown
| ID | Title | Status | When to use |
| --- | --- | --- | --- |
| `review/code-review` | Code review | active | Review a diff or pull request |
```

When you add, rename, deprecate, or remove a file, update:

1. The category `README.md`
2. `prompts/README.md` or `rules/README.md` if you added a category

## Adding a prompt or rule

1. Copy `templates/prompt.md` or `templates/rule.mdc`.
2. Place it in the matching category folder with a kebab-case name.
3. Fill in frontmatter. New entries start as `status: draft` until you have used them once.
4. Fill every required section. The **Prompt** block must be paste-ready.
5. Add a row to the category `README.md`.
6. Set `status: active` after a successful real use.

## Updating

- Edit in place for clarifications, typo fixes, and tighter wording. Bump `updated` if present; keep `version` the same.
- Increment `version` when the instructions, inputs, or expected output change in a way that would surprise someone using an old copy.
- Do not keep parallel files such as `code-review-v2.md`. History lives in git.

## Deprecating

1. Set `status: deprecated` in frontmatter.
2. Add a **Notes** line pointing to the replacement `id`, if any.
3. Update the category index.
4. Leave the file in place until nothing references it, then delete it in a later change.

## Using prompts

1. Find the prompt via the category `README.md` or by searching `id:` / `title:`.
2. Copy only the **Prompt** fenced block.
3. Replace every `{{variable_name}}` before sending.
4. In Cursor, you can also `@`-mention the markdown file so the agent reads the full file.

## Using rules

Copy a `.mdc` file into a project’s `.cursor/rules/` directory. Keep the Cursor frontmatter (`description`, `globs`, `alwaysApply`). Trim library-only fields (`id`, `category`, `tags`, `status`, `version`) if the target project does not need them.

## What not to commit

- API keys, tokens, passwords, session cookies
- Private customer data, credentials, or internal URLs that are not meant to be shared
- One-off chat dumps that were never cleaned into the template
- Duplicate prompts that differ only by model name — use the `models` field instead

## Quality bar

A prompt or rule is ready for `active` when:

- A new reader can use it without asking the author questions
- Inputs are complete and the **Prompt** block is self-contained
- The output contract is specific enough to judge success
- It does one job and names that job in `title` and `id`
