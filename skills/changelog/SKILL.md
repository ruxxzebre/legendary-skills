---
name: changelog
description: Write a structured changelog entry and append it to CHANGELOG.md. Use this skill when the user asks to write a changelog, update the changelog, document recent changes, or after completing a feature/fix/task and wanting to record what was done. Triggers on commands like /changelog, "write changelog", "update changelog", "add to changelog", or "document what we did".
---

# Changelog

Write a structured changelog entry based on recent work and append it to `CHANGELOG.md`.

## Mode Detection

Pick the source before starting:

| Signal | Mode |
|--------|------|
| User says "based on our conversation / this session / what we did in this chat" | **Chat** |
| No git repo, or repo has no new commits | **Chat** |
| User says "from git / from commits" | **Git** |
| Both git activity and conversation context available | **Hybrid** |
| No explicit signal | **Git** (default) |

---

## Workflow — Chat Mode

Use this when the source is the current conversation.

1. **Scan the conversation** — read the full message history. Identify:
   - Features or capabilities added
   - Bugs or regressions fixed
   - APIs, configs, or interfaces changed
   - Things removed or deprecated
   - Decisions made that affect future behavior
2. **Ignore implementation noise** — skip "I read file X", "I edited line Y". Focus on observable outcomes: what a user or caller of this system would notice.
3. **Categorize** — sort findings into Added / Changed / Fixed / Removed / etc. (see `references/format.md`).
4. **Draft the entry** — write bullets in imperative mood following the format in `references/format.md`. Use today's date.
5. **Append to CHANGELOG.md** — insert under `## [Unreleased]` (create the file and header if missing).
6. **Show the entry** — display what was written.

---

## Workflow — Git Mode

Use this when the source is git history.

1. **Run** `git log --oneline -20` and inspect staged/unstaged diff.
2. **Categorize** commits and diff hunks into Added / Changed / Fixed / Removed / etc.
3. **Draft the entry** — write bullets in imperative mood. Group related small commits into one bullet.
4. **Append to CHANGELOG.md** — insert under `## [Unreleased]` (create the file and header if missing).
5. **Show the entry** — display what was written.

---

## Workflow — Hybrid Mode

1. Run both the **Chat** and **Git** steps above in parallel.
2. Merge results — use git for precise code changes, use conversation for intent and context not obvious from commit messages.
3. Deduplicate, then write and append a single unified entry.

---

## Key Rules

- Use imperative mood: "Add", "Fix", "Remove" — not "Added", "Fixed".
- Each bullet is one self-contained change; keep it under ~120 chars.
- Do not duplicate entries already in CHANGELOG.md.
- Use today's date (ISO 8601: YYYY-MM-DD) for versioned entries.
- Group related small changes into one bullet rather than listing each file changed.

## Resources

- **Entry format & examples**: See `references/format.md`
