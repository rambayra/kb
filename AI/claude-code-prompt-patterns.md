---
title: Claude Code prompt library and patterns
source: https://code.claude.com/docs/en/prompt-library
type: docs
topics: [ai-agents, coding, software-engineering]
added: 2026-11-10
status: processed
---

## Summary
A set of copy-paste prompts for Claude Code. The more useful part is the list
of six patterns that explain why they work. The example prompts are mostly
about discovery and onboarding: getting an architecture overview, tracing a
data flow, finding where something happens, judging the impact of deleting
code, and summarizing a file's history. The page also suggests turning prompts
that work into skills, and recording learned conventions in CLAUDE.md.

## Key takeaways
Six patterns for task prompts:
- **Describe the outcome, not the steps.** Let the agent find the files.
- **Give it a way to check its own work.** Include run, test, or compare in the
  prompt so it iterates instead of stopping after one try.
- **Point at a reference.** Name an existing file or pattern to match so the
  result is consistent.
- **State a measurable target.** For performance or coverage work, give the
  metric and threshold so "done" is clear.
- **Give it the artifact.** Paste the error, log, screenshot, or plan output
  (or `@`-reference a file) rather than describing it.
- **Say how you want the answer.** Specify format, length, and audience (e.g.
  "as an HTML page with a diagram", "I am a PM").

Useful discovery prompts:
- Codebase overview: architecture, key directories, and how the parts connect.
- "What would break if I deleted X?" for impact analysis before refactoring.
- "Which files would I need to touch to add Y?" for scoping.
- Summarizing a file's commit history to see how and why it changed.
- Walking through a user action end-to-end, written for a non-engineer.

Making it repeatable:
- Save a prompt that works as a skill (`/command`), and put conventions in
  CLAUDE.md. Use plan mode for larger or riskier changes so you see the file
  list before any edits happen.

## My take / how I'd apply it
- 

## Short quotes (optional, keep brief)
> They're starting points rather than scripts.

## Related
- [[claude-prompting-best-practices]]
