---
title: Job description matcher
id: job-search/match-resume-to-job
category: job-search
tags: [resume, keywords, ats, tailoring]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Job description matcher

## Purpose

Identify missing keywords in a resume against a job description and rewrite the resume so it matches the role as closely as possible while staying honest.

## When to use

- You are applying to a specific posting and need the resume aligned to that JD.
- You want a keyword gap analysis before you submit.

When not to use: for a general resume rewrite with no posting, use `job-search/rewrite-resume-for-callbacks`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{job_description}}` | Full job posting |
| `{{resume}}` | Current resume text |
| `{{must_keep}}` | Facts, titles, or sections that must not change (or `none`) |

## Prompt

```text
Match this resume to this job description as closely as possible while staying honest.

Job description:
{{job_description}}

Resume:
{{resume}}

Must keep:
{{must_keep}}

Do:
- Extract required skills, tools, domain terms, and repeated phrases from the job description.
- Identify which of those keywords are missing, weakly evidenced, or already present.
- Rewrite the resume so relevant experience uses the employer's language where it is truthful.
- Reorder or emphasize bullets that map to the role's top requirements.
- Stay honest: only include keywords the candidate can defend from the resume or clearly related work.

Do not:
- Invent experience, certifications, tools, or metrics.
- Keyword-stuff or copy the job description verbatim into bullets.
- Hide weak matches; mark them as gaps instead of faking coverage.

Return markdown with these sections:
1. Keyword gap analysis — present / missing / stretch (do not claim stretch items)
2. Tailored resume — paste-ready rewrite
3. Honest mismatches — requirements the candidate does not meet
4. Optional add-ons — true facts the candidate could add if they have them
```

## Output

A keyword gap table, a tailored paste-ready resume, and an explicit list of requirements the candidate does not meet. Stretch keywords stay in gaps, not in the rewrite.
