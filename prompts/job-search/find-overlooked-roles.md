---
title: Role fit finder
id: job-search/find-overlooked-roles
category: job-search
tags: [roles, career, demand, targeting]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Role fit finder

## Purpose

From a candidate's experience and skills, list 10 roles they are qualified for that they might be overlooking, ranked by hiring demand and response likelihood.

## When to use

- The search is stuck on one title and you need adjacent roles that still fit.
- You want a demand-ranked target list before rewriting materials.

When not to use: to rewrite a resume for a role you already chose, use `job-search/rewrite-resume-for-callbacks` or `job-search/match-resume-to-job`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{experience_and_skills}}` | Resume, skills list, or career summary |
| `{{constraints}}` | Location, seniority, industry, visa, or salary bounds (or `none`) |
| `{{already_targeting}}` | Titles already in the search (or `none`) |

## Prompt

```text
Based on this experience and skills, list 10 roles the candidate is qualified for that they might be overlooking. Rank them by hiring demand and response likelihood.

Experience and skills:
{{experience_and_skills}}

Constraints:
{{constraints}}

Already targeting:
{{already_targeting}}

Do:
- Infer transferable strengths, tools, domain knowledge, and seniority from the source.
- Propose 10 concrete job titles (not vague buckets like "tech" or "operations").
- Prefer roles the candidate is already qualified for now, not stretch careers that need a degree or years of new experience.
- Skip titles already listed under Already targeting unless a close variant is materially different.
- Rank by likely hiring demand and callback odds for this profile, not by prestige.
- For each role, explain the fit in one or two sentences using evidence from the source.

Do not:
- Suggest roles that require credentials, licenses, or years of experience the source does not show.
- Pad the list with near-duplicates of the same title.
- Invent employers, metrics, or skills.

Return markdown with these sections:
1. Ranked roles (1–10) — for each: title, demand/response rank rationale, why they qualify, likely employers or teams, main gap if any
2. Roles to skip — 3 titles that look adjacent but are a poor fit, with why
3. How to search — 8–12 Boolean or keyword phrases for the top 5 roles
```

## Output

Exactly 10 ranked, non-duplicate titles the candidate can defend today, plus a short skip list and search phrases. Rank rationale is about demand and callback odds, not preference.
