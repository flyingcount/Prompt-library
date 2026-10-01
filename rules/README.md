# Rules

Reusable Cursor rules (`.mdc`) grouped by when they should apply. Copy a file into a project’s `.cursor/rules/` directory.

Keep Cursor frontmatter (`description`, `globs`, `alwaysApply`). Library fields (`id`, `category`, `tags`, `status`, `version`) are optional in the destination project.

| Category | For |
| --- | --- |
| [coding](coding/) | Implement, refactor, debug, tests |
| [review](review/) | Code review, security review, PR feedback, proposal critique |
| [planning](planning/) | Specs, architecture, task breakdown, thinking sessions |
| [writing](writing/) | Docs, presentations, hierarchical restructuring |
| [research](research/) | Explain, compare, investigate, briefings |
| [agents](agents/) | System prompts and agent instructions |
| [job-search](job-search/) | Resume, outreach, and application-workflow instructions |

Add new rules with [templates/rule.mdc](../templates/rule.mdc). Follow [RULES.md](../RULES.md).
