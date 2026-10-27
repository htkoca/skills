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

## Keep plugin READMEs in sync

Each plugin owns its skill list in `plugins/<plugin>/README.md`. When adding,
removing, renaming, or changing a skill description, update that README in the
same change. List every skill with a working relative link and its full
`SKILL.md` frontmatter description as visible text, including trigger words.
Keep the plugin summary in sync with its manifests. The root README links to
plugin READMEs; do not duplicate skill lists there or hide descriptions in HTML
comments.

## ChatGPT and Codex installation preference

For ChatGPT and Codex, the owner prefers installing and updating these as
private skills through chat or Plugin Creator instead of marketplace plugins.
Use that workflow by default unless the owner requests a marketplace install.
Pushing this repo does not update imported copies; import the updated skills
through chat or Plugin Creator when an update is requested.
