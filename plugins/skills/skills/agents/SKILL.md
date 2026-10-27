---
name: agents
description: Shared instructions and repo hygiene for Claude, Claude Code, ChatGPT, and Codex. Use when writing or restructuring AGENTS.md, migrating CLAUDE.md, configuring agent instructions, or deciding which agent state belongs in git.
---

# Agents

Shared instruction and repo conventions for Claude, Claude Code, ChatGPT, and Codex.

1. **`AGENTS.md` is the shared repo instruction file** for Claude, Claude Code,
   ChatGPT, and Codex.
   Keep it as a real tracked file. Remove redundant `CLAUDE.md` symlinks or copies.
   If `CLAUDE.md` contains unique instructions, move them into `AGENTS.md` before
   removing it; if it is the only instruction file, rename it to `AGENTS.md`.
   Update repo docs to point to `AGENTS.md`. If neither file exists, don't invent one.
2. **Gitignore Claude Code's local-only state**: add `/.claude/`
   (personal permission overrides, machine-specific) to `.gitignore`. 
3. **Don't use the persistent memory system for project facts.** Status, decisions,
   and other facts that matter beyond the current conversation belong in the
   repo — the owning doc (PRD, plan, standards) or the code itself — not in
   cross-session memory. Memory drifts silently out of sync with the repo it
   describes; the repo can't. If a fact is worth remembering past this session,
   write it back to the doc that owns it (see the process skill's §Division of
   truth) instead of saving it to memory.
