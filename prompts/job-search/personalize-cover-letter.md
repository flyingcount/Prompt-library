---
title: Cover letter personalizer
id: job-search/personalize-cover-letter
category: job-search
tags: [cover-letter, applications, writing, tailoring]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Cover letter personalizer

## Purpose

Write a short, tailored cover letter for a specific role that sounds human, confident, and specific rather than generic or AI-written.

## When to use

- You have a job description (and preferably a resume) and need a concise letter for that posting.
- The default letter sounds templated and you want a specific hook.

When not to use: for a LinkedIn or email opener to a recruiter, use `job-search/write-recruiter-hook`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{job_description}}` | Full job posting, including company and title if present |
| `{{resume_or_background}}` | Resume or short background the letter must draw from |
| `{{why_this_role}}` | Genuine reason for interest, if known (or `infer carefully from the posting`) |
| `{{constraints}}` | Length, tone, or facts to include/avoid (or `none`) |

## Prompt

```text
Write a short, tailored cover letter for this role. Make it sound human, confident, and specific, not generic or AI-written.

Job description:
{{job_description}}

Resume or background:
{{resume_or_background}}

Why this role:
{{why_this_role}}

Constraints:
{{constraints}}

Do:
- Open with a specific hook tied to this company, product, team, or problem — not "I am excited to apply".
- Pick 2–3 proof points from the background that map to the posting's actual requirements.
- Sound like a competent colleague writing to a hiring manager: direct, warm, no hype.
- Keep it short: about 200–280 words, three or four short paragraphs.
- Stay honest. Do not claim motivation or experience the source does not support.
- Close with a clear, low-pressure next step (interest in a conversation), not begging.

Do not:
- Use stock phrases: "passionate about", "leverage", "synergy", "I am writing to express my interest", "dynamic environment".
- Restate the resume chronologically.
- Flatter the company with empty praise.
- Invent metrics, titles, or connection to the mission.

Return markdown with these sections:
1. Cover letter — paste-ready, no subject line unless the posting asks for email
2. Why this version works — 3 bullets naming the hook and proof points used
3. Optional swap-ins — 2 alternate opening lines the candidate could use
```

## Output

A short paste-ready letter that a hiring manager could believe a human wrote, plus a brief rationale and two alternate openings. Specific proof beats generic enthusiasm.
