# skills-software

Tony Ko's software standards for frontend architecture, Next.js, components, data, testing, performance, accessibility, SEO, Figma, git, estimation, delivery, writing, and agent engineering. Use when planning, building, reviewing, or maintaining software.

## Skills

### [nextjs](skills/nextjs/SKILL.md)

Next.js, App Router, page.tsx, layout.tsx, route.ts, route handler, "use client", server component, RSC, generateStaticParams, generateMetadata, dynamic route, SSG/ISR, app/ folder structure, TypeScript. Use when scaffolding a Next.js app, adding a route or page, or deciding how code is organized in a Next.js + TypeScript codebase.

### [components](skills/components/SKILL.md)

React component, shadcn, Radix, Tailwind v4, CVA, class-variance-authority, cn(), variants, props interface, .tsx, atoms/molecules/organisms, atomic design, layout shell, design tokens, component file skeleton. Use when adding, extracting, refactoring, restyling, or reviewing a component in any shadcn + Tailwind project.

### [data](skills/data/SKILL.md)

constants/, types/, site copy, content, hardcoded strings, useState, URL params, global state, context, store, dates, timezones, date formatting, media entries, images metadata. Use when adding or moving site content, deciding where data or state should live, typing a content entry, or handling dates and media.

### [testing](skills/testing/SKILL.md)

Tests, testing strategy, unit test, integration test, e2e, testing pyramid, test runner, vitest, jest, Playwright, coverage, flaky test, failing test, keeping CI green. Use when deciding what kind of test to add, setting up a runner, or reviewing a PR that adds or changes test coverage.

### [performance](skills/performance/SKILL.md)

Performance, LCP, CLS, INP, Core Web Vitals, Lighthouse, page speed, slow load, lazy-loading, above/below the fold, image optimization, SVG vs raster, bundle size, font loading, FOUT, motion budget. Use when adding images, media, animation, or custom fonts, or when reviewing a page for load or interactivity regressions.

### [accessibility](skills/accessibility/SKILL.md)

Accessibility, a11y, WCAG 2.0 AA, AODA, ARIA, screen reader, keyboard navigation, tab order, focus ring, focus trap, skip link, alt text, color contrast, semantic landmarks, header/main/nav/footer, h1, prefers-reduced-motion. Use when building or reviewing any UI component, page, navigation, menu, dialog, modal, overlay, carousel, or self-starting animation in a web frontend.

### [seo](skills/seo/SKILL.md)

SEO, metadata, meta description, page title, Open Graph, og:image, Twitter card, canonical URL, favicon, theme-color, sitemap, robots.txt, crawlable, indexing, link preview, server-rendered content. Use when adding metadata to a page or route, making a link preview well, or reviewing whether content is crawlable.

### [writing](skills/writing/SKILL.md)

Keep all prose simple, concise, readable, and short. Applies to every response and anything written into a file. Load before the first response and after context compaction.

### [git](skills/git/SKILL.md)

git, worktree, commit message, Conventional Commits, feat/fix/chore/docs, branch name, branching, PR, pull request, opening a PR, PR review, code review of a diff, merge, rebase, push, AI attribution, Co-Authored-By. Use when starting work on a ticket or feature, creating a worktree or branch, writing a commit or PR body, reviewing a PR, or deciding how a change gets recorded in git.

### [process](skills/process/SKILL.md)

PRD, product requirements, project plan, planning, roadmap, milestone, scope, kickoff, delivery methodology, GitHub issues, where a decision gets documented, source of truth between repo/design tool/GitHub. Use when planning work, cutting milestones, deciding which doc owns what, or setting up delivery process for a new project.

### [estimation](skills/estimation/SKILL.md)

Dev-hour estimate, effort estimate, LOE, quote, scoping, base hours, multiplier, overhead, buffer, rounding, itemized change list, client-facing summary, internal working doc, PM request, SOW. Use when a client or PM asks how long something takes, when turning a change set or ticket list into hours, or when preparing an estimate to send out.

### [figma](skills/figma/SKILL.md)

Figma, figma.com URL, node-id, frame, design context, design tokens, Figma MCP, get_design_context, get_metadata, screenshot, design-to-code, transcribing a design, matching a component to the design. Use for any design-to-code work backed by Figma: implementing a node, reading values out of a file, or checking built UI against the design.

### [vscode](skills/vscode/SKILL.md)

Editor session, VS Code window, stale path, repo moved, directory renamed, `mv` the repo, reopen at new path, `code` command, stale file tree. Use right after this repo's directory is moved or renamed, so the open editor is not pointed at the old path.

### [agents](skills/agents/SKILL.md)

Shared instructions and repo hygiene for Claude, Claude Code, ChatGPT, and Codex. Use when writing or restructuring AGENTS.md, migrating CLAUDE.md, configuring agent instructions, or deciding which agent state belongs in git.

### [engineering](skills/engineering/SKILL.md)

Harness engineering, context engineering, agent design, SKILL.md, AGENTS.md, system prompt, subagent, tool definition, MCP server design, progressive disclosure, runbook, sidecar, agent permissions and authority, bad agent trajectory, agent keeps doing X. Use on an unresolved agent-design decision: authoring or debugging a skill, deciding what belongs in context vs. tools vs. code, or diagnosing why an agent behaves wrongly.
