# skills

Two plugins for Claude Code and Codex, published from one repository and the
`htkoca` marketplace:

- **[skills-software](plugins/skills-software/README.md):** coding, design, testing, git, estimation, delivery, writing,
  and agent conventions.
- **[skills-notes](plugins/skills-notes/README.md):** personal and work Notion context, plus job and rental listing
  capture.

Skills are plain Markdown with no hooks or per-surface glue. Each skill's
`description` says when to load it.

## Installing

Add the marketplace once, then install either or both plugins.

**Codex:**

```sh
codex plugin marketplace add https://github.com/htkoca/skills --ref main
codex plugin add skills-software@htkoca
codex plugin add skills-notes@htkoca
```

**Claude Code:**

```sh
claude plugin marketplace add https://github.com/htkoca/skills.git
claude plugin install skills-software@htkoca
claude plugin install skills-notes@htkoca
```

Start a new Codex chat and restart Claude Code after installing. Each surface owns
its installation; updating one does not update the others. Verify installation in
regular ChatGPT separately.

Skills are namespaced by plugin, for example `/skills-software:nextjs` and
`/skills-notes:notes`. Agents also select skills when the request matches their
description. Shared writing and agent conventions live in skills-software.

## Updating

Installs are snapshots pinned to a commit SHA. Pushing this repository does not
update installed copies.

**Codex:**

```sh
codex plugin marketplace upgrade htkoca
codex plugin add skills-software@htkoca
codex plugin add skills-notes@htkoca
```

**Claude Code:**

```sh
claude plugin marketplace update htkoca
claude plugin update skills-software@htkoca
claude plugin update skills-notes@htkoca
```

## Migrating from the old plugin

The two plugins replace `skills@htkoca`. Install the replacements using the commands
above, then remove the old plugin to avoid duplicate skill discovery:

```sh
codex plugin remove skills@htkoca
claude plugin uninstall skills@htkoca
```

Update personal instructions and explicit skill references from `skills` to
`skills-software` or `skills-notes`, as appropriate.

## Versioning

Both plugins carry matching versions in their `.claude-plugin/plugin.json` and
`.codex-plugin/plugin.json` manifests. Bump the patch version in all four manifests
on every commit. Minor and major are the owner's to set. See [AGENTS.md](AGENTS.md).

Compare installed versions with these manifests to identify stale snapshots.
Claude Code records installed versions and commit SHAs in
`~/.claude/plugins/installed_plugins.json`.

## Layout

The root catalogs list both self-contained plugin packages:

```text
.agents/plugins/marketplace.json   Codex marketplace catalog
.claude-plugin/marketplace.json    Claude Code marketplace catalog
plugins/
  skills-software/
    README.md
    .claude-plugin/plugin.json
    .codex-plugin/plugin.json
    skills/<name>/SKILL.md
  skills-notes/
    README.md
    .claude-plugin/plugin.json
    .codex-plugin/plugin.json
    skills/<name>/SKILL.md
```
