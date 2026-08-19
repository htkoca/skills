# Agent Instructions

See [README.md](README.md) for what this repo is and how other repos use it.

## On every commit: bump the patch version

[`plugins/skills/.claude-plugin/plugin.json`](plugins/skills/.claude-plugin/plugin.json)
and [`plugins/skills/.codex-plugin/plugin.json`](plugins/skills/.codex-plugin/plugin.json)
carry matching `version` values. Bump the **patch** number in both, in the same commit
as the change, always and without being asked:

```json
"version": "0.1.0"   →   "version": "0.1.1"
```

**Minor and major are the owner's to set.** Never bump them and never propose a
version that changes them. If a change seems to warrant more than a patch, say so and
let them decide.

Why: installs are snapshots pinned to a commit SHA, not live clones of `main`. The
version is the only readable way to tell a stale install from a current one (compare
`plugin.json` against the entry in `~/.claude/plugins/installed_plugins.json`).
Skipping the bump makes two different plugin contents share a version, which is worse
than no version at all.

## Keep the plugin portable

Skills are plain markdown, read by both Claude Code and Codex. No hooks, no
settings, no per-surface glue: anything that only one agent can execute does not
belong here. A skill that must run at a particular moment says so in its
`description`.

Skills ship to agents in other repos. Treat a change here as shipping.
