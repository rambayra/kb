---
title: Claude prompting best practices
source: https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices
type: docs
topics: [ai-agents, coding, software-engineering]
added: 2026-11-10
status: processed
---

## Summary
Anthropic's main reference for prompting current Claude models through the API.
It covers three things: general techniques (be explicit, give context, use
examples and XML structure), how to steer output, tools, thinking, and agent
behaviour, and how to migrate prompts written for older models. A recurring
theme is that newer models follow instructions more literally and act more
proactively, so prompts built to push older models harder now cause
over-triggering and should be toned down. Behaviour varies by model, and the
page links to a separate guide for each model; treat model-specific tips as
things to re-check with your own evals.

## Key takeaways
**General**
- Write prompts as if briefing a smart new hire who doesn't know your norms.
  Test: would a colleague with no context understand it?
- Explain *why* an instruction matters. The model generalizes from the reason.
- Few-shot examples are the most reliable way to steer format and tone. Make
  them relevant and varied, and wrap them in `<example>` tags.
- Use consistent XML tags to separate instructions, context, examples, and
  inputs.
- For long inputs (20k+ tokens), put documents first and the question last.
  Ask the model to pull out relevant quotes before answering.

**Output and formatting**
- Say what to do, not what to avoid ("write flowing prose", not "no markdown").
- The style of your prompt influences the style of the output. Less markdown in
  the prompt means less in the reply.
- Newer models give fewer summaries after tool calls. Ask for them if you want
  them.
- Prefilling the last assistant turn is no longer supported (400 error) from
  the 4.6 models onward.

**Tools and actions**
- "Can you suggest changes" may only produce suggestions. Be explicit if you
  want action, or set a default-to-action or don't-act-before-asked policy in
  the system prompt.
- Drop shouty language ("CRITICAL: you MUST…"). Newer models over-trigger on it.
- Parallel tool calls are on by default and can be tuned up or down by prompt.

**Thinking**
- Adaptive thinking plus the `effort` parameter replaces `budget_tokens`, which
  returns an error on 4.7+ models. On several newer models thinking is always
  on.
- General guidance ("think thoroughly") often works better than a hand-written
  plan of steps.
- Self-check instructions ("verify against X before finishing") help on most
  models, but cause over-verification on Opus 5, so remove them there.
- If the model thinks or explores too much: tell it to pick an approach and
  commit, or lower `effort`.

**Agentic / long-horizon work**
- Over multiple context windows: use the first window to set up tests and init
  scripts, then iterate. Track state in JSON for structured data, free text for
  progress notes, and git for checkpoints.
- A fresh context that rediscovers state from the filesystem can work better
  than compaction.
- Add a reversibility rule: local, reversible actions are fine; ask before
  destructive or shared-system actions (force push, deleting branches, posting
  messages).
- Watch for too many subagents. Say when delegation is and isn't worth it.
- Common failure modes and their fixes: over-engineering (keep scope minimal),
  gaming tests or hardcoding (ask for general solutions and to flag bad tests),
  hallucinating about code (never make claims about files you haven't opened),
  leftover temp files (ask for cleanup).
- Prompt chaining is still useful when you need to inspect intermediate output.
  The main pattern is draft → review → refine.

**Migration checklist (from older models)**
- Be explicit about the behaviour and features you want, move from
  `budget_tokens` to adaptive thinking plus `effort`, remove prefills, tone
  down anti-laziness prompts, and keep conversation history append-only so
  thinking blocks stay valid.

**Not captured**
- The clipping is missing the prefill migration examples. It also contains
  other material that I left out of this note: medication-dosing system
  prompt blocks, frontend design prompt snippets, and parts of the general
  prompt engineering overview.

## My take / how I'd apply it
- 

## Short quotes (optional, keep brief)
> Think of Claude as a brilliant but new employee who lacks context on your norms and workflows.

## Related
- [[claude-code-prompt-patterns]]
