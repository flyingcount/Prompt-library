---
title: Resume conversion fixer
id: job-search/rewrite-resume-for-callbacks
category: job-search
tags: [resume, ats, rewriting, interviews]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Resume conversion fixer

## Purpose

Rewrite a resume to maximize interview callbacks using strong action verbs, quantified results, and ATS-friendly formatting, without exaggeration.

## When to use

- You have a full resume and want a stronger, more scannable version before applying.
- The current draft is duty-heavy, vague, or poorly formatted for applicant tracking systems.

When not to use: to tailor one resume to a specific posting, use `job-search/match-resume-to-job`. To rewrite only a few bullets, use `job-search/upgrade-resume-bullets`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{resume}}` | Full current resume text |
| `{{target_roles}}` | Target titles or industries (or `general`) |
| `{{constraints}}` | Length, format, or facts that must not change (or `none`) |

## Prompt

```text
Rewrite this resume to maximize interview callbacks.

Resume:
{{resume}}

Target roles:
{{target_roles}}

Constraints:
{{constraints}}

Do:
- Use strong action verbs and lead each bullet with an accomplishment, not a duty.
- Quantify results wherever the source supports a number, range, or scale.
- Use ATS-friendly formatting: standard section headings, no tables, no columns, no icons, no headers/footers as the only place for contact info.
- Keep the rewrite honest. Infer reasonable phrasing from the source; do not invent employers, titles, dates, skills, or metrics.
- Preserve true chronology, education, and contact details unless the source is clearly malformed and you are only cleaning layout.
- Prefer a clean reverse-chronological layout unless the source is a functional resume the user asked to keep.

Do not:
- Exaggerate impact, seniority, or tools.
- Add keywords the candidate did not demonstrate.
- Use first-person pronouns, clichés ("team player", "results-driven"), or dense paragraphs.
- Hide important facts in graphics or multi-column layouts.

Return markdown with these sections:
1. Rewritten resume — paste-ready, ATS-safe
2. Changes made — bullet list of the highest-leverage edits
3. Gaps to fill — facts or metrics the candidate should add if they have them
```

## Output

A paste-ready rewritten resume, a short list of what changed and why, and a Gaps to fill list for missing numbers or proof. No invented metrics or job history.
