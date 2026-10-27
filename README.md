# skills

Two plugins for Claude Code and Codex, published from one repository and the
`htkoca` marketplace:

- **skills-software:** coding, design, testing, git, estimation, delivery, writing,
  and agent conventions.
- **skills-notes:** personal and work Notion context, plus job and rental listing
  capture.

Skills are plain Markdown with no hooks or per-surface glue. Each skill's
`description` says when to load it.

## Skills Software

Fifteen skills in `plugins/skills-software/`.

- [nextjs](plugins/skills-software/skills/nextjs/SKILL.md): App Router conventions, runtime foundations, folder structure
  <!-- Next.js, App Router, page.tsx, layout.tsx, route.ts, route handler, "use client", server component, RSC, generateStaticParams, generateMetadata, dynamic route, SSG/ISR, app/ folder structure, TypeScript. Use when scaffolding a Next.js app, adding a route or page, or deciding how code is organized in a Next.js + TypeScript codebase. -->
- [components](plugins/skills-software/skills/components/SKILL.md): shadcn/CVA authoring shape, atomic-design organization
  <!-- React component, shadcn, Radix, Tailwind v4, CVA, class-variance-authority, cn(), variants, props interface, .tsx, atoms/molecules/organisms, atomic design, layout shell, design tokens, component file skeleton. Use when adding, extracting, refactoring, restyling, or reviewing a component in any shadcn + Tailwind project. -->
- [data](plugins/skills-software/skills/data/SKILL.md): content and state location (`constants/`, dates, media)
  <!-- constants/, types/, site copy, content, hardcoded strings, useState, URL params, global state, context, store, dates, timezones, date formatting, media entries, images metadata. Use when adding or moving site content, deciding where data or state should live, typing a content entry, or handling dates and media. -->
- [testing](plugins/skills-software/skills/testing/SKILL.md): testing strategy stance
  <!-- Tests, testing strategy, unit test, integration test, e2e, testing pyramid, test runner, vitest, jest, Playwright, coverage, flaky test, failing test, keeping CI green. Use when deciding what kind of test to add, setting up a runner, or reviewing a PR that adds or changes test coverage. -->
- [performance](plugins/skills-software/skills/performance/SKILL.md): LCP, lazy-loading, motion and font budgets
  <!-- Performance, LCP, CLS, INP, Core Web Vitals, Lighthouse, page speed, slow load, lazy-loading, above/below the fold, image optimization, SVG vs raster, bundle size, font loading, FOUT, motion budget. Use when adding images, media, animation, or custom fonts, or when reviewing a page for load or interactivity regressions. -->
- [accessibility](plugins/skills-software/skills/accessibility/SKILL.md): WCAG 2.0 AA baseline, motion, focus, contrast
  <!-- Accessibility, a11y, WCAG 2.0 AA, AODA, ARIA, screen reader, keyboard navigation, tab order, focus ring, focus trap, skip link, alt text, color contrast, semantic landmarks, header/main/nav/footer, h1, prefers-reduced-motion. Use when building or reviewing any UI component, page, navigation, menu, dialog, modal, overlay, carousel, or self-starting animation in a web frontend. -->
- [seo](plugins/skills-software/skills/seo/SKILL.md): metadata, Open Graph, crawlable content
  <!-- SEO, metadata, meta description, page title, Open Graph, og:image, Twitter card, canonical URL, favicon, theme-color, sitemap, robots.txt, crawlable, indexing, link preview, server-rendered content. Use when adding metadata to a page or route, making a link preview well, or reviewing whether content is crawlable. -->
- [writing](plugins/skills-software/skills/writing/SKILL.md): the prose standard, and the only skill that is not task-scoped
  <!-- Keep all prose simple, concise, readable, and short. Applies to every response and anything written into a file. Load before the first response and after context compaction. -->
- [git](plugins/skills-software/skills/git/SKILL.md): Conventional Commits, branch naming, no AI attribution
  <!-- git, worktree, commit message, Conventional Commits, feat/fix/chore/docs, branch name, branching, PR, pull request, opening a PR, PR review, code review of a diff, merge, rebase, push, AI attribution, Co-Authored-By. Use when starting work on a ticket or feature, creating a worktree or branch, writing a commit or PR body, reviewing a PR, or deciding how a change gets recorded in git. -->
- [process](plugins/skills-software/skills/process/SKILL.md): PRD pipeline, milestones, review tiers
  <!-- PRD, product requirements, project plan, planning, roadmap, milestone, scope, kickoff, delivery methodology, GitHub issues, where a decision gets documented, source of truth between repo/design tool/GitHub. Use when planning work, cutting milestones, deciding which doc owns what, or setting up delivery process for a new project. -->
- [estimation](plugins/skills-software/skills/estimation/SKILL.md): sizing work
  <!-- Dev-hour estimate, effort estimate, LOE, quote, scoping, base hours, multiplier, overhead, buffer, rounding, itemized change list, client-facing summary, internal working doc, PM request, SOW. Use when a client or PM asks how long something takes, when turning a change set or ticket list into hours, or when preparing an estimate to send out. -->
- [figma](plugins/skills-software/skills/figma/SKILL.md): reading designs out of Figma, node structure over screenshots
  <!-- "Figma, figma.com URL, node-id, frame, design context, design tokens, Figma MCP, get_design_context, get_metadata, screenshot, design-to-code, transcribing a design, matching a component to the design. Use for any design-to-code work backed by Figma: implementing a node, reading values out of a file, or checking built UI against the design." -->
- [vscode](plugins/skills-software/skills/vscode/SKILL.md): editor-session hygiene after a move or rename
  <!-- Editor session, VS Code window, stale path, repo moved, directory renamed, `mv` the repo, reopen at new path, `code` command, stale file tree. Use right after this repo's directory is moved or renamed, so the open editor is not pointed at the old path. -->
- [agents](plugins/skills-software/skills/agents/SKILL.md): shared instructions and repo hygiene for Claude, Claude Code, ChatGPT, and Codex
  <!-- Shared instructions and repo hygiene for Claude, Claude Code, ChatGPT, and Codex. Use when writing or restructuring AGENTS.md, migrating CLAUDE.md, configuring agent instructions, or deciding which agent state belongs in git. -->
- [engineering](plugins/skills-software/skills/engineering/SKILL.md): harness engineering corpus and routing
  <!-- "Harness engineering, context engineering, agent design, SKILL.md, AGENTS.md, system prompt, subagent, tool definition, MCP server design, progressive disclosure, runbook, sidecar, agent permissions and authority, bad agent trajectory, agent keeps doing X. Use on an unresolved agent-design decision: authoring or debugging a skill, deciding what belongs in context vs. tools vs. code, or diagnosing why an agent behaves wrongly." -->

## Skills Notes

Three skills in `plugins/skills-notes/`.

- [notes](plugins/skills-notes/skills/notes/SKILL.md): when and where to read personal and career instructions in Notion
  <!-- Read before advising or acting on Tony's personal background, life, relationships, dating, social life, chats, events, goals, planning, housing, finances, travel, home, hobbies, professional background, career, job search, applications, resumes, interviews, recruiter chats, project/client work, compensation, corporate administration, ideation, business ideas, venture planning, or resale listings. Routes to the htkoca (personal) and tkodev (career and work) Notion guides, even when Notion is not mentioned. -->
- [jd-scrape](plugins/skills-notes/skills/jd-scrape/SKILL.md): a job posting into structured facts
  <!-- Job description, JD, job posting, careers page, job listing URL, LinkedIn/Greenhouse/Lever/Workday/Ashby posting, recruiter link, lightpanda scrape. Use when given a JD or careers URL, when pasting job posting text to capture, or when asked to save, pull, or file a job posting. Recording facts only; judging the role is a separate step. -->
- [listing-scrape](plugins/skills-notes/skills/listing-scrape/SKILL.md): a rental or real-estate listing into structured facts
  <!-- Rental listing, apartment, condo, real estate listing, listing URL, rentals.ca, Zumper, PadMapper, Condos.ca, Realtor.ca, MLS, building site, lease, rent, viewing, prospect file, lightpanda scrape. Use when given a listing URL, when pasting listing text or a screenshot to capture, or when asked whether a place is worth viewing. Recording facts only; judging the listing is a separate step. -->

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
    .claude-plugin/plugin.json
    .codex-plugin/plugin.json
    skills/<name>/SKILL.md
  skills-notes/
    .claude-plugin/plugin.json
    .codex-plugin/plugin.json
    skills/<name>/SKILL.md
```
