---
title: Smart Brevity revision
id: writing/smart-brevity-revision
category: writing
tags: [smart-brevity, revision, editing, scanability]
status: draft
version: 1
models: [any]
created: 2026-09-19
updated: 2026-09-19
---

# Smart Brevity revision

## Purpose

Rewrite a draft to Smart Brevity standards: shorter, scannable, and action-first, without changing facts, figures, dates, commitments, or the author's intent.

## When to use

- You have a memo, email, update, brief, or announcement that buries the point.
- You want a tighter revision plus a scorecard (word-count reduction, remaining gaps, publish readiness).

When not to use: to force a MECE logic tree, use `writing/minto-pyramid-mece`. To cut a dump into one headline and three pillars, use `writing/slide-hierarchy`. To move text up or down the abstraction ladder, use `writing/ladder-of-abstraction`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{source_document}}` | The draft to revise |

## Prompt

```text
You are a Smart Brevity editor. Revise the source document so the key message is visible within 10 seconds, actions and deadlines are obvious, and unnecessary words are gone. Meaning, facts, and the author's intent must stay unchanged.

Source document:
{{source_document}}

Revision method:
1. Find the one thing that matters. Lead with it in a complete-sentence headline.
2. Follow with Why it matters (one or two short sentences).
3. Use short paragraphs, bullets, and bold on names, dates, figures, and next steps.
4. Make every required action obvious: who does what, by when.
5. Cut throat-clearing, filler, and repeated context. Keep qualifications that change the meaning.
6. End with What's next so the reader knows the immediate next move.

Success criteria — the revision is successful when:
- The key message is visible within 10 seconds.
- Readers can scan the document quickly.
- Actions are obvious.
- Deadlines are clear.
- Unnecessary words are removed.
- The document is shorter and clearer.
- Meaning remains unchanged.
- The reader knows exactly what to do next.

Non-negotiable rules — always:
- Preserve factual accuracy
- Preserve technical meaning
- Preserve commitments
- Preserve dates
- Preserve figures and metrics
- Improve scanability
- Reduce complexity
- Improve actionability

Non-negotiable rules — never:
- Invent information
- Remove critical qualifications
- Alter commitments
- Change dates
- Change numerical values
- Add unsupported claims
- Change the author's intent

Return exactly two parts, in this order:

Part 1 — Revised document
The full rewritten draft. Do not include commentary in this part.

Part 2 — Scorecard
Use this exact structure:

**Original Word Count:** X
**Revised Word Count:** X
**Reduction:** X%

---

## Highest-Impact Improvements
1. ...
2. ...
3. ...

---

## Remaining Opportunities
- ...
- ...
- ...

---

## Final Verdict
**Smart Brevity Compliance:** XX%
**Reader Experience:** Excellent / Good / Fair / Poor
**Recommendation:** Ready to publish / Minor edits recommended / Significant revision still needed
```

## Output

Two parts only. Part 1 is the revised document: headline, why it matters, scannable body, obvious actions and deadlines. Part 2 is the scorecard: original/revised word counts and reduction percent, three highest-impact improvements, remaining opportunities, then Smart Brevity Compliance, Reader Experience (Excellent / Good / Fair / Poor), and Recommendation (Ready to publish / Minor edits recommended / Significant revision still needed). Facts, dates, figures, commitments, and intent are unchanged.

## Notes

Related: `writing/slide-hierarchy` (three-pillar trim without a scorecard), `writing/minto-pyramid-mece` (logic tree, not a prose rewrite).
