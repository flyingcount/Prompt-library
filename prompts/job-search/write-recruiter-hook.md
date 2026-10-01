---
title: Recruiter hook message
id: job-search/write-recruiter-hook
category: job-search
tags: [recruiter, linkedin, email, outreach]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Recruiter hook message

## Purpose

Write a concise LinkedIn or email message to a recruiter for a specific role whose goal is to spark interest and get a reply, not to ask for a favor.

## When to use

- You found a recruiter or hiring contact for a live role and need a short opener.
- Cold outreach should lead with fit, not a request.

When not to use: for a full cover letter, use `job-search/personalize-cover-letter`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{role}}` | Job title, company, link, or pasted posting |
| `{{resume_or_background}}` | Short background or resume highlights |
| `{{channel}}` | `linkedin` or `email` |
| `{{recruiter_context}}` | Recruiter name, team, or prior contact (or `unknown`) |

## Prompt

```text
Write a concise LinkedIn or email message to a recruiter for this role. The goal is to spark interest and get a reply, not ask for a favor.

Role:
{{role}}

Background:
{{resume_or_background}}

Channel:
{{channel}}

Recruiter context:
{{recruiter_context}}

Do:
- Lead with who the candidate is and the strongest proof of fit for this role in one sentence.
- Add one concrete result or credential a recruiter can scan in two seconds.
- Name the role (and company if known) so the message is not a generic networking ask.
- Ask for a next step that is easy to answer: a short chat, or whether the profile is a match.
- Keep LinkedIn messages under 80 words; emails under 120 words plus a specific subject line.
- Sound like a peer, not a salesperson or a mentee asking for help.

Do not:
- Ask for a referral, intro, or "any advice" as the main ask.
- Attach a life story, salary demands, or a full resume dump in the body.
- Use "I hope this finds you well", "circle back", "leverage", or "passionate".
- Invent a personal connection or shared history.

Return markdown with these sections:
1. Message — subject line only if channel is email; then the body, paste-ready
2. Shorter variant — 40–50 words for a LinkedIn connection note
3. Why it should get a reply — 2 bullets on the hook and the easy ask
```

## Output

A paste-ready short message (plus subject if email), a tighter LinkedIn-note variant, and a two-bullet explanation of the hook. The ask is a reply about fit, not a favor.
