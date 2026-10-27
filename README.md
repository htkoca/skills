# skills

Two skill packages for ChatGPT, Codex, and Claude Code, maintained in one
repository and also published through the `htkoca` marketplace:

- **[skills-software](plugins/skills-software/README.md):** coding, design, testing, git, estimation, delivery, writing,
  and agent conventions.
- **[skills-notes](plugins/skills-notes/README.md):** personal and work Notion context, plus job and rental listing
  capture.

Skills are plain Markdown with no hooks or per-surface glue. Each skill's
`description` says when to load it.

## Installing

**ChatGPT and Codex (preferred):**

Install either or both packages as private skills through chat or Plugin Creator.
This is the owner's preferred workflow; use marketplace installation only when
requested.

**Codex marketplace (optional):**

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

For marketplace installs, start a new Codex chat or restart Claude Code after
installing. Verify private skill imports in the destination app. Each app owns
its installation; updating one does not update the others.

Marketplace skills are namespaced by plugin, for example `/skills-software:nextjs` and
`/skills-notes:notes`. Agents also select skills when the request matches their
description. Shared writing and agent conventions live in skills-software.

## Updating

Pushing this repository does not update installed copies.

**ChatGPT and Codex (preferred):**

Import the updated skills through chat or Plugin Creator to update the private
copies. Verify the update in each app separately.

**Codex marketplace (optional):**

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

The two packages replace `skills@htkoca`. Import the private skills or install
the replacement marketplace plugins using the appropriate workflow above, then
remove the old plugin where installed to avoid duplicate skill discovery:

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
