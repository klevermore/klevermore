# Planning as Code

**Planning as Code** treats the implementation plan for a change as a
first-class, version-controlled artifact — reviewed, diffed, and merged the
same way source code is.

## Why

Most planning happens in places that don't last: a chat window, an issue
thread, someone's head. The reasoning behind a change evaporates, and reviewers
only get to weigh in *after* the code is written — when feedback is expensive.

Planning as code moves the review earlier and makes the reasoning durable:

- **Reviewable early.** A plan PR is cheap to review and cheap to change.
  Course corrections happen before implementation, not after.
- **Diffable & durable.** Plans live in [`plans/`](../plans) next to the code
  they describe. `git blame` and `git log` explain *why*, not just *what*.
- **A shared contract.** Once a plan is approved, implementation (human or
  agent) has an agreed target to build against.

## How it works here

1. **Trigger.** Add the `plan` label to a GitHub issue, or run the
   *Planning as Code* workflow manually with a task description.
2. **Draft.** The
   [`planning-as-code.yml`](../.github/workflows/planning-as-code.yml) workflow
   runs Claude Code, which explores the repository and writes a structured plan
   file to [`plans/`](../plans) following the template in
   [`plans/README.md`](../plans/README.md).
3. **Review.** The plan is opened as a pull request. Reviewers comment on the
   plan itself.
4. **Approve → build → done.** Merging the plan marks it `approved`.
   Implementation references the plan; when it ships, the plan is marked
   `done`.

## Setup

The workflow needs an `ANTHROPIC_API_KEY` repository secret:

```
Settings → Secrets and variables → Actions → New repository secret
  Name:  ANTHROPIC_API_KEY
  Value: <your Anthropic API key>
```

It also needs a `plan` label to exist (create one under **Issues → Labels**)
if you want the issue-triggered path.

That's it — label an issue `plan` and a plan PR shows up.
