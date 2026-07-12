# Plans

This directory holds **planning-as-code** artifacts: implementation plans
written as versioned markdown files, one per task.

Each plan is drafted *before* implementation, reviewed as a pull request, and
kept in the repo so the reasoning behind a change is diffable and durable —
not lost in a chat thread or an issue comment.

## Naming

```
plans/<zero-padded-number>-<kebab-case-slug>.md
```

- For a plan drafted from a GitHub issue, use the **issue number**
  (e.g. `plans/0042-add-export-endpoint.md`).
- Otherwise use the next available number in this directory.

## Template

Copy this structure when writing a new plan (the
[`Planning as Code` workflow](../.github/workflows/planning-as-code.yml) does
this automatically):

```markdown
# <Title>

> Status: draft | approved | done
> Source: #<issue-number> (or "manual")

## Summary

One or two sentences: what this change does and why.

## Context

What exists today, and what problem or gap this addresses. Reference real
files and paths in the codebase.

## Approach

The chosen strategy, and briefly why — including alternatives considered and
rejected.

## Step-by-step plan

1. Small, commit-sized step.
2. Next step.
3. ...

## Files to change

- `path/to/file` — what changes and why.

## Risks & open questions

- Risks, unknowns, and anything that needs a human decision.

## Acceptance criteria

- [ ] Observable, testable condition that means "done".
```

## Lifecycle

1. A plan is drafted (by the workflow or by hand) and opened as a PR.
2. Reviewers comment on the **plan** — cheaper than reviewing finished code.
3. Once merged, the plan's `Status` moves to `approved` and implementation
   begins, referencing the plan.
4. When the work ships, the plan is marked `done`.
