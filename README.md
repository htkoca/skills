# skills

Reusable agent skills (`SKILL.md` per directory) for project standards, packaged as
one shared plugin for Claude Code and Codex.

Skills are plain markdown with no hooks or per-surface glue, so both agents read the
same files. Each skill's `description` says when to load it.

## Skills

Eighteen, in four groups.

### Code

- [nextjs](plugins/skills/skills/nextjs/SKILL.md): App Router conventions, runtime foundations, folder structure
- [components](plugins/skills/skills/components/SKILL.md): shadcn/CVA authoring shape, atomic-design organization
- [data](plugins/skills/skills/data/SKILL.md): content and state location (`constants/`, dates, media)
- [testing](plugins/skills/skills/testing/SKILL.md): testing strategy stance
- [performance](plugins/skills/skills/performance/SKILL.md): LCP, lazy-loading, motion and font budgets
- [accessibility](plugins/skills/skills/accessibility/SKILL.md): WCAG 2.0 AA baseline, motion, focus, contrast
- [seo](plugins/skills/skills/seo/SKILL.md): metadata, Open Graph, crawlable content

### Craft

- [writing](plugins/skills/skills/writing/SKILL.md): the prose standard, and the only skill that is not task-scoped
- [git](plugins/skills/skills/git/SKILL.md): Conventional Commits, branch naming, no AI attribution
- [process](plugins/skills/skills/process/SKILL.md): PRD pipeline, milestones, review tiers
- [estimation](plugins/skills/skills/estimation/SKILL.md): sizing work
- [figma](plugins/skills/skills/figma/SKILL.md): reading designs out of Figma, node structure over screenshots
- [notion](plugins/skills/skills/notion/SKILL.md): navigating and editing a Notion workspace over MCP
- [vscode](plugins/skills/skills/vscode/SKILL.md): editor-session hygiene after a move or rename
- [claude](plugins/skills/skills/claude/SKILL.md): Claude Code repo hygiene

### Agents

- [engineering](plugins/skills/skills/engineering/SKILL.md): harness engineering corpus and routing

### Scrapers

- [jd-scrape](plugins/skills/skills/jd-scrape/SKILL.md): a job posting into structured facts
- [listing-scrape](plugins/skills/skills/listing-scrape/SKILL.md): a rental or real-estate listing into structured facts

## Installing

The repo is both a plugin and its own marketplace, so it installs from GitHub. Add
the marketplace, then install the plugin from it.

**Codex** reads [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json):

```sh
codex plugin marketplace add https://github.com/htkoca/skills --ref main
codex plugin add skills@htkoca
```

Start a new thread afterward. Codex loads plugin skills at thread startup, so an open
thread will not see a new or updated install.

**Claude Code** reads [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json):

```sh
claude plugin marketplace add https://github.com/htkoca/skills.git
claude plugin install skills@htkoca
```

Start a new thread afterward. Claude loads plugin skills at thread startup, so an open
thread will not see a new or updated install.

Skills are namespaced by plugin: `/skills:nextjs`, `/skills:git`. Both agents
also load them on their own when a task matches a `description`.

Each surface installs its own copy. Installing or updating on one does nothing to the
rest.

## Updating

Installs pin to a commit SHA rather than tracking `main`. Claude Code copies the
plugin into `~/.claude/plugins/cache/<marketplace>/<plugin>/<sha>/` as a flat
snapshot, not a git checkout, so pushing here changes nothing on an installed machine.

Two steps, per machine.

**Codex:**

```sh
codex plugin marketplace upgrade htkoca   # refresh the catalog
codex plugin add skills@htkoca            # re-snapshot the plugin
```

**Claude Code:**

```sh
claude plugin marketplace update htkoca   # refresh the catalog
claude plugin update skills@htkoca        # re-snapshot the plugin
```

## Versioning

[`.claude-plugin/plugin.json`](plugins/skills/.claude-plugin/plugin.json) and
[`.codex-plugin/plugin.json`](plugins/skills/.codex-plugin/plugin.json) carry
matching `version` values, bumped by patch on every commit. Minor and major are the
owner's to set. See [AGENTS.md](AGENTS.md) for the rule agents follow.

The version is diagnostic, not a release channel: updates always move to the tip of
`main`, and no older version is installable. What it buys is a readable answer to "is
this install current?". Compare it against the `skills@htkoca` entry in
`~/.claude/plugins/installed_plugins.json`, which records the resolved version and the
`gitCommitSha` it came from.

## Layout

The repository root is the marketplace. The plugin package lives under
`plugins/skills/` so an install copies a self-contained directory.

```text
.claude-plugin/
  marketplace.json      Claude marketplace catalog
.agents/
  plugins/
    marketplace.json    Codex marketplace catalog
plugins/
  skills/
    .claude-plugin/
      plugin.json       Claude plugin manifest
    .codex-plugin/
      plugin.json       Codex plugin manifest
    skills/
      <name>/SKILL.md   one directory per skill
```

Both marketplaces point at `./plugins/skills`, which holds the only copy of the
skills.
