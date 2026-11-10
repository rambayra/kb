---
title: "Prompt library"
source: "https://code.claude.com/docs/en/prompt-library"
author:
published:
created: 2026-11-10
description: "Copy-paste prompts for Claude Code, tagged by task and role."
tags:
  - "clippings"
---
This is a library of prompts to copy into Claude Code. Use it to explore ways of working you haven’t tried, or when you’re not sure where to start.

The prompts are collected from various Anthropic guides, including [Common workflows](https://code.claude.com/docs/en/common-workflows), [Best practices](https://code.claude.com/docs/en/best-practices), and [How Anthropic teams use Claude Code](https://claude.com/blog/how-anthropic-teams-use-claude-code). They’re starting points rather than scripts. Open **Why this works** under any prompt to see the pattern behind it so you can write your own.

7 prompts

Discover · Onboard

`give me an overview of this codebase: architecture, key directories, and how the pieces connect`

Discover · Understand

`explain what src/scheduler/queue.ts does and how data flows through it. write it up as an HTML page with a diagram, then open it in my browser`

`where do we validate uploaded file types?`

`what would break if I deleted the retryWithBackoff helper?`

`look through the commit history of internal/auth/session.go and summarize how it evolved and why`

`I am a PM. walk me through what happens when a user clicks Export to PDF, from the UI down to the result`

`which files would I need to touch to add a dark mode toggle to settings?`

## What makes these prompts work

The prompts above share a few patterns. Recognizing them helps you adapt any prompt here to your own task.

**Describe the outcome, not the steps.** Say what you want and let Claude find the files. The prompt below works without naming a single file path.

```text
add rate limiting to the public API and make sure existing tests still pass
```

**Give it a way to check its own work.** Ask for run, test, compare, or verify in the same prompt so Claude iterates instead of stopping after one attempt. To check the finished change against the running app, run [`/verify`](https://code.claude.com/docs/en/skills#run-and-verify-your-app).

```text
write the migration, run it against the dev database, and confirm the schema matches
```

**Point at a reference.** Name an existing file, test, or pattern to match so the new code is consistent with what you already have.

```text
add a settings page that follows the same layout as the profile page
```

**State the measurable target.** When the goal is performance or coverage, give the metric and threshold so completion is unambiguous.

```text
get the bundle size under 200KB and show me what you removed
```

**Give it the artifact.** Paste errors, logs, screenshots, and plan output directly in the prompt, or type `@` to reference a file. Claude reads the source instead of your description of it.

```text
why is the build failing? @build.log
```

**Say how you want the answer.** Name the format, length, or audience so the explanation fits how you’ll use it. To make a format the default for every response, set an [output style](https://code.claude.com/docs/en/output-styles).

```text
explain how the payment retry logic works as an HTML page with a diagram, then open it in my browser
```

For more on each pattern, see [best practices](https://code.claude.com/docs/en/best-practices).

## Where these come from

These prompts are based on patterns from published Anthropic resources. Each card links to its source:

- [Common workflows](https://code.claude.com/docs/en/common-workflows): step-by-step guides for the core tasks
- [Best practices](https://code.claude.com/docs/en/best-practices): prompting patterns and project setup
- [How Anthropic teams use Claude Code](https://claude.com/blog/how-anthropic-teams-use-claude-code): real workflows from engineering, product, design, and data teams, with deep dives on [legal](https://claude.com/blog/how-anthropic-uses-claude-legal), [marketing](https://claude.com/blog/how-anthropic-uses-claude-marketing), and [cybersecurity](https://claude.com/blog/how-anthropic-uses-claude-cybersecurity)
- [Scaling agentic coding guide](https://resources.anthropic.com/hubfs/Scaling%20agentic%20coding%20across%20your%20organization.pdf): the enterprise adoption guide

For video walkthroughs of these patterns, see the free [Claude Code in Action](https://academy.claude.com/courses/claude-code-in-action) course on [Claude Academy](https://academy.claude.com/).

## Related resources

The prompts on this page are starting points. Once one works for your project, the next step is making it repeatable: save it as a [skill](https://code.claude.com/docs/en/skills) so anyone on your team can run it as a `/command`, and record the conventions Claude learned in [CLAUDE.md](https://code.claude.com/docs/en/memory) so every session starts with that context instead of Claude relearning it. For larger or riskier changes, [plan mode](https://code.claude.com/docs/en/permission-modes#analyze-before-you-edit-with-plan-mode) shows you the file list before any edits happen.

If you’re introducing Claude Code across a team, see [administration](https://code.claude.com/docs/en/admin-setup) for managed settings and policy, and [costs and usage](https://code.claude.com/docs/en/costs) for how this work is billed on your plan.