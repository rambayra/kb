# Knowledge base instructions

This repo is my personal knowledge base: plain markdown notes (viewed in
Obsidian, stored in git) about platform engineering, cloud best practices,
coding, code review, testing, AI agents, system design and software
engineering. You are my assistant for capturing, searching and synthesizing it.

## Structure
- One folder per topic: platform-engineering, cloud-best-practices, coding,
  code-review, testing, ai-agents, system-design, software-engineering.
- `playbooks/` holds distilled checklists synthesized from many notes.
- `inbox/` holds raw links and clipped pages waiting to be processed.
- `_templates/` holds note and playbook templates. Follow them.

## File conventions
- Filenames: kebab-case, descriptive, no dates (e.g. `flaky-test-strategies.md`).
- Every note has YAML frontmatter: title, source, type, topics, added, status.
- A note lives in the folder of its PRIMARY topic; list all topics in frontmatter.
- Link related notes with [[wikilinks]]. Only link to notes that exist.

## Workflow: ingest
When I give you a URL, pasted text, or ask you to process `inbox/`:
1. Fetch/read the source. If it can't be read, say so; never invent content.
2. Write a note from `_templates/note.md`: summary and takeaways in my own
   words, source URL preserved, at most one or two short quotes.
3. Choose topic folder and topics. Check existing notes first and link related
   ones. If it duplicates an existing note, tell me and offer to merge instead.
4. Leave "My take" as a placeholder for me unless I give you my opinion.
5. Move processed inbox items out of `inbox/` (do not delete the original
   without asking). One git commit per ingested source.

## Workflow: search / answer
- Answer from the notes in this repo and cite them as [[note-name]].
- If the notes don't cover the question, say so clearly. Only add general
  knowledge if I ask, and label it as NOT from my notes.
- When sources disagree, show both and name the notes.

## Workflow: synthesize
- When I ask (or when 5+ notes on a theme exist), propose or update a file in
  `playbooks/` using `_templates/playbook.md`.
- Every playbook item should be traceable to source notes under "Sources".
- Mark new playbooks `status: draft` until I review them.

## Maintenance (on request)
- Find duplicates, stale notes, broken links, topics with few notes.
- Weekly digest: what was added, and any themes worth turning into a playbook.

## Rules
- Never delete or overwrite my "My take" sections.
- Don't reproduce long passages from sources; paraphrase and link.
- Show me a summary of changes before committing anything large.
