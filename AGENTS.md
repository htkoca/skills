# Agent Instructions

See [README.md](README.md) for what this repo is and how other repos use it.

## On every commit: bump the patch version

Each plugin has matching versions in its Claude Code and Codex manifests:

- `plugins/skills-software/.claude-plugin/plugin.json`
- `plugins/skills-software/.codex-plugin/plugin.json`
- `plugins/skills-notes/.claude-plugin/plugin.json`
- `plugins/skills-notes/.codex-plugin/plugin.json`

Bump the patch number in all four manifests in every commit, always and without
being asked. Keep all four versions matching.

Minor and major are the owner's to set. Never bump them or propose changing them.
If a change seems to warrant more than a patch, let the owner decide.

Installs are snapshots pinned to a commit SHA. The version identifies which
snapshot is installed; different contents must not share a version.

## Keep the plugin portable

Skills are plain markdown, read by both Claude Code and Codex. No hooks, no
settings, no per-surface glue: anything that only one agent can execute does not
belong here. A skill that must run at a particular moment says so in its
`description`.

Skills ship to agents in other repos. Treat a change here as shipping.
