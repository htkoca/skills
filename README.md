# standards

Reusable agent skills (`SKILL.md` per directory) for project standards, packaged as
one shared plugin for Claude Code and Codex.

Skills are plain markdown with no hooks or per-surface glue, so both agents read the
same files. Each skill's `description` says when to load it.

## Skills

Seventeen, in four groups.

### Code

- [nextjs](plugins/standards/skills/nextjs/SKILL.md): App Router conventions, runtime foundations, folder structure
- [components](plugins/standards/skills/components/SKILL.md): shadcn/CVA authoring shape, atomic-design organization
- [data](plugins/standards/skills/data/SKILL.md): content and state location (`constants/`, dates, media)
- [testing](plugins/standards/skills/testing/SKILL.md): testing strategy stance
- [performance](plugins/standards/skills/performance/SKILL.md): LCP, lazy-loading, motion and font budgets
- [accessibility](plugins/standards/skills/accessibility/SKILL.md): WCAG 2.0 AA baseline, motion, focus, contrast
- [seo](plugins/standards/skills/seo/SKILL.md): metadata, Open Graph, crawlable content

### Craft

- [writing](plugins/standards/skills/writing/SKILL.md): the prose standard, and the only skill that is not task-scoped
- [git](plugins/standards/skills/git/SKILL.md): Conventional Commits, branch naming, no AI attribution
- [process](plugins/standards/skills/process/SKILL.md): PRD pipeline, milestones, review tiers
- [estimation](plugins/standards/skills/estimation/SKILL.md): sizing work
- [figma](plugins/standards/skills/figma/SKILL.md): reading designs out of Figma, node structure over screenshots
- [vscode](plugins/standards/skills/vscode/SKILL.md): editor-session hygiene after a move or rename
- [claude](plugins/standards/skills/claude/SKILL.md): Claude Code repo hygiene

### Agents

- [engineering](plugins/standards/skills/engineering/SKILL.md): harness engineering corpus and routing

### Scrapers

- [jd-scrape](plugins/standards/skills/jd-scrape/SKILL.md): a job posting into structured facts
- [listing-scrape](plugins/standards/skills/listing-scrape/SKILL.md): a rental or real-estate listing into structured facts

## Installing

The repo is both a plugin and its own marketplace, so it installs from GitHub. Add
the marketplace, then install the plugin from it.

**Codex** reads [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json):

```sh
codex plugin marketplace add https://github.com/htkoca/standards --ref main
codex plugin add standards@htkoca
```

Start a new thread afterward. Codex loads plugin skills at thread startup, so an open
thread will not see a new or updated install.

**Claude Code CLI**, in chat:

```sh
/plugin marketplace add htkoca/standards
/plugin install standards@htkoca
```

In VS Code and the desktop app, run `/plugin` (or click customize), then: marketplaces
→ add the standards git repo → install the standards plugin from it.

Skills are namespaced by plugin: `/standards:nextjs`, `/standards:git`. Both agents
also load them on their own when a task matches a `description`.

Each surface installs its own copy. Installing or updating on one does nothing to the
rest.

## Updating

Installs pin to a commit SHA rather than tracking `main`. Claude Code copies the
plugin into `~/.claude/plugins/cache/<marketplace>/<plugin>/<sha>/` as a flat
snapshot, not a git checkout, so pushing here changes nothing on an installed machine.

Two steps, per machine:

```sh
/plugin marketplace update htkoca   # refresh the catalog
/plugin update standards@htkoca     # re-snapshot the plugin
```

The first alone is not enough: it refreshes the catalog, not the installed skills.
The Codex equivalent is `codex plugin marketplace upgrade htkoca` then
`codex plugin add standards@htkoca`.

## Versioning

[`.claude-plugin/plugin.json`](plugins/standards/.claude-plugin/plugin.json) and
[`.codex-plugin/plugin.json`](plugins/standards/.codex-plugin/plugin.json) carry
matching `version` values, bumped by patch on every commit. Minor and major are the
owner's to set. See [AGENTS.md](AGENTS.md) for the rule agents follow.

The version is diagnostic, not a release channel: updates always move to the tip of
`main`, and no older version is installable. What it buys is a readable answer to "is
this install current?". Compare it against the `standards@htkoca` entry in
`~/.claude/plugins/installed_plugins.json`, which records the resolved version and the
`gitCommitSha` it came from.

## Layout

The repository root is the marketplace. The plugin package lives under
`plugins/standards/` so an install copies a self-contained directory.

```text
.claude-plugin/
  marketplace.json      Claude marketplace catalog
.agents/
  plugins/
    marketplace.json    Codex marketplace catalog
plugins/
  standards/
    .claude-plugin/
      plugin.json       Claude plugin manifest
    .codex-plugin/
      plugin.json       Codex plugin manifest
    skills/
      <name>/SKILL.md   one directory per skill
```

Both marketplaces point at `./plugins/standards`, which holds the only copy of the
skills.
