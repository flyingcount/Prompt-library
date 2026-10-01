---
title: Application optimizer
id: job-search/optimize-job-applications
category: job-search
tags: [strategy, applications, follow-up, targeting]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Application optimizer

## Purpose

Turn a candidate's background and target roles into a weekly application strategy: volume, efficient customization, and follow-up.

## When to use

- The search is unfocused, too high-volume, or stalling after applications with no replies.
- You need a repeatable weekly system, not another resume draft.

When not to use: to rewrite materials for one posting, use `job-search/match-resume-to-job` or `job-search/personalize-cover-letter`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{background_and_targets}}` | Background plus the roles or companies being targeted |
| `{{current_pace}}` | Current applications per week, time available, and results so far (or `unknown`) |
| `{{constraints}}` | Location, visa, notice period, or tools already in use (or `none`) |

## Prompt

```text
Based on this background and target roles, create a smarter application strategy. Tell me how many roles to apply for weekly, how to customize efficiently, and how to follow up.

Background and target roles:
{{background_and_targets}}

Current pace and results:
{{current_pace}}

Constraints:
{{constraints}}

Do:
- Recommend a weekly application volume with a high / default / low range based on seniority, specialization, and hours available.
- Split volume into must-customize vs. light-customize vs. skip.
- Give a 15–25 minute customization checklist per serious role (keywords, top bullets, cover note).
- Define what "good enough to apply" vs. "skip this posting" looks like for this profile.
- Specify a follow-up cadence: when, through which channel, and what to say without nagging.
- Include a simple weekly scoreboard: applications, tailored apps, conversations, interviews.

Do not:
- Advise spray-and-pray volume as a default.
- Promise callback rates or imply luck is the main variable.
- Invent networking contacts or insider referrals.
- Turn the plan into a generic productivity essay.

Return markdown with these sections:
1. Weekly volume — numbers, hours, and why this range fits the profile
2. Targeting rules — which postings to pursue, batch, or skip
3. Customization workflow — time-boxed steps and what to reuse
4. Follow-up cadence — day-by-day after apply
5. Scoreboard — metrics to review each week and when to change the plan
```

## Output

A concrete weekly system with a volume range, targeting rules, a time-boxed customization checklist, a follow-up cadence, and a scoreboard. Advice is specific to the given background, not a generic job-search pep talk.
