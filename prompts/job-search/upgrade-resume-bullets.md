---
title: Bullet point upgrader
id: job-search/upgrade-resume-bullets
category: job-search
tags: [resume, bullets, recruiters, rewriting]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Bullet point upgrader

## Purpose

Rewrite resume bullet points so they are clearer, more results-focused, and more impressive to recruiters, in under two lines each.

## When to use

- Existing bullets are vague, duty-based, or too long.
- You want line-level edits without a full resume overhaul.

When not to use: to rewrite the whole document, use `job-search/rewrite-resume-for-callbacks`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{bullet_points}}` | The bullets to rewrite |
| `{{role_context}}` | Job title, company, and years if not obvious from the bullets (or `none`) |
| `{{audience}}` | Target role or industry (or `general recruiters`) |

## Prompt

```text
Rewrite these resume bullet points. Make them clearer, more results-focused, and more impressive to recruiters in under 2 lines each.

Bullet points:
{{bullet_points}}

Role context:
{{role_context}}

Audience:
{{audience}}

Do:
- Keep one accomplishment per bullet.
- Lead with a strong verb, then the action, then the result.
- Add quantification only when the source supports a number, range, scale, or frequency.
- Stay under two lines per bullet at a normal resume width (roughly 20–28 words).
- Match tone to recruiters: concrete, scannable, no fluff.
- Preserve the original meaning. If a bullet is only a duty, tighten it rather than inventing impact.

Do not:
- Merge unrelated bullets into one claim.
- Invent metrics, tools, awards, or scope.
- Use first-person, adverbs as filler, or phrases like "responsible for".
- Exceed two lines.

Return markdown with these sections:
1. Upgraded bullets — one rewritten line per input bullet, in the same order
2. Before → after notes — only where the change needs a one-line explanation
3. Still weak — bullets that need a real metric or scope from the candidate before they will land
```

## Output

A 1:1 rewrite of each input bullet, each under two lines, plus notes only where needed and a Still weak list for bullets that lack evidence. No invented results.
