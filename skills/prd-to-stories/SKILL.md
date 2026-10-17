---
name: PRD to Stories
description: Decompose a PRD into 3–8 user stories, each with title, user-story sentence, acceptance criteria, and size — ready to push to Jira / Linear / GitHub Issues.
icon: 🧩
version: 0.1.0
---

# PRD to Stories

Take a Product Requirements Document and decompose it into a list of user stories that a developer (or LLM agent) can execute one at a time. Each story should be small enough to ship in a single PR.

## Input

A markdown PRD with sections like Title, Summary, Problem, Target users, Success metrics, In scope, Out of scope, Non-goals, Open risks, Context. Tolerate variation in section names.

## Output format

A markdown numbered list of stories. Use this exact shape per story:

```
### 1. <Story title>

As a <role> I want <capability> so that <outcome>.

**Acceptance criteria**
- <Testable condition 1>
- <Testable condition 2>
- <Testable condition 3>

**Size:** S | M | L
```

After all stories, if the PRD had a **Context** section, echo it verbatim under `## Context` so downstream steps still have the project keys / repo URLs / ticket prefixes.

No preamble, no closing summary. The output is the stories list (and optional context echo) only.

## Decomposition rules

- **Aim for 3–8 stories.** Fewer if the PRD is small; more only if scope genuinely demands it.
- **Decompose by capability, not by file or layer.** "Render PRD in canvas terminal stream" is a capability. "Add HTML to renderer.js, then add CSS, then add Rust handler" is layers — combine into one story.
- **Each story is a thing the user can perceive.** If a developer could ship a story and the user wouldn't notice anything changed, the story is too internal — fold it into a perceivable one.
- **Don't multiply.** Stories that share acceptance criteria should be one story.
- **Don't split too small.** A story whose acceptance criteria is one bullet is probably a sub-task, not a story.

## Sizing

- **S** — one PR, a few hours, no architectural decisions.
- **M** — one PR, half-day to a day, one or two design judgment calls.
- **L** — likely needs a spike or sub-tasking; flag it as L and note the unknown in acceptance criteria.

## Tone

- Action-oriented titles. "Render PRD inline" not "PRD rendering".
- Acceptance criteria are testable conditions, not implementation notes. "Enter key submits the form" is testable. "Use onSubmit handler" is implementation.
- No meta commentary.
