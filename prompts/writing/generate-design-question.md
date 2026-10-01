---
title: Design question generator
id: writing/generate-design-question
category: writing
tags: [instructional-design, questions, learning, cognitive-struggle]
status: draft
version: 1
models: [any]
created: 2026-10-01
updated: 2026-10-01
---

# Design question generator

## Purpose

Turn source text into one design question that makes a learner grapple with the central insight — reason, predict, compare, diagnose, or decide — instead of receiving the explanation passively.

## When to use

- You have an article, lesson, or explanation and want a single question that leads the learner to discover the key idea.
- The goal is productive struggle and application, not a quiz of definitions.

When not to use: to shorten or restructure the text itself, use `writing/edit-for-smart-brevity` or `writing/minto-pyramid-mece`. To brief a topic, use `research/research-briefing`.

## Inputs

| Variable | Meaning |
| --- | --- |
| `{{text}}` | Source text the question must be answerable from |
| `{{output_mode}}` | `full` (question + reasoning target) or `question_only` |

## Prompt

```text
You are an instructional designer. Learning happens when people actively grapple with information rather than passively receive explanations. The brain filters and connects new information through active sense-making, not simply through clear explanations.

Given the following text, create a single design question that leads a learner to discover the key idea for themselves rather than having it explained directly.

Text:
{{text}}

Output mode:
{{output_mode}}

Your task is to identify the central insight and create a question that:
1. Makes the learner think before reading the answer.
2. Exposes a common misconception if answered incorrectly.
3. Requires application rather than memorization.
4. Has no obvious answer from the wording of the question.
5. Reveals the core idea of the text when discussed.

Do:
- Require reasoning, judgment, prediction, comparison, diagnosis, or decision-making.
- Create productive cognitive struggle.
- Make the question answerable using only the information in the text.
- Focus on the most important concept, trade-off, or insight.
- Make the question authentic and relevant to a real-world situation.
- Prefer stems such as: "What would happen if...?", "Why might someone choose...?", "Which option would you recommend and why?", "What problem is this idea trying to solve?", "How would you explain the difference between...?", "What evidence suggests...?"

Do not:
- Ask for recall or definition.
- Explain the key idea in the question stem.
- Ask more than one question.
- Invent facts that are not in the text.
- Write a question whose answer is obvious from how it is worded.

If output_mode is question_only: return only the design question, nothing else.

Otherwise return exactly:
Design Question: <question>
Reasoning Target: <the thinking skill being exercised>
```

## Output

One design question that cannot be answered by restating a definition. In `full` mode, also name the reasoning target (for example prediction, comparison, diagnosis, or decision). In `question_only` mode, the question alone. A weak result is a recall prompt, a multi-part quiz, or a stem that gives the insight away.

## Notes

`full` is the stronger default: it produces questions that create cognitive engagement rather than testing recall. Use `question_only` when you need a paste-ready stem with no commentary.

Related: `writing/edit-for-smart-brevity` (tighten the source), `writing/minto-pyramid-mece` (structure the argument), `research/research-briefing` (summarise for an audience).
