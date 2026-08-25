---
name: notion
description: Notion, Notion MCP, notion.so URL, teamspace, Agents section, page tree, fetch, search, move-pages, update-page, update_content, replace_content, filing a note in Notion, archiving a page, duplicate page titles. Use for any read or write against Notion through the MCP connector: mapping the workspace, finding where a page lives, editing page content, or moving something.
---

# Notion

How the workspace is navigated and edited through the MCP tools. Tool names below are
written unprefixed (`fetch`, `search`, `update-page`); clients namespace them, usually
as `notion-fetch` and so on.

## How the workspace is laid out

1. **Each teamspace holds three things at its root:** one container page, `Archive`,
   and `Unsorted`. Everything else lives under the container.
2. **Inside the container are the domain pages,** and each domain page holds its
   pillar children.
3. **A domain page carries its own instructions inline.** There is no separate README
   or instructions child page: the prose sits on the domain page above its child list,
   and Notion renders the child list itself. Never write an inventory of child pages
   into a page's text. It drifts, and the rendered list does not.
4. **Agent-facing rules live under an `Agents` heading** at the end of that prose.
   Everything above it describes the domain and is written for a person. Everything
   under it is working rules: what to load, what the guardrails are, what format a new
   page takes.
5. **Teamspaces mirror each other's names on purpose.** The same domain and pillar
   names appear in more than one teamspace, so a bare title never identifies a page.
   See "Duplicate titles" below.
6. **The workspace is the authority, not this description.** When what you fetch does
   not match the shape above, follow what is there and say so.

## Load skills before pages

1. **Pull every skill the session will plausibly need up front,** before the first
   page fetch. Deciding at the point of need is too late: a leaf page fetch is large,
   and a skill loaded after it competes with the page content for the room to use it.
2. **The writing skill applies to every word written into a page,** so it is always
   one of them.
3. **Read the domain page first, then load in one pass** what its `Agents` section
   names and the skills that match the task: `listing-scrape` for a rental listing,
   `jd-scrape` for a job posting, `git` when repo work follows from the note.
4. **Err toward loading one skill too many.** A skill is small next to a page of
   content, and the cost of not having it is work redone.

## Mapping the tree

1. **No tool lists a teamspace's root children.** `get-teams` returns teamspace ids,
   fetching a teamspace id returns 404, and `search` returns a flat ranked list with
   no parent information. Do not go looking for the tool that does this.
2. **Start from a known page URL and fetch downward.** This is the cheap path, and the
   reason the container page exists.
3. **Without a known URL, reconstruct roots from `list-recent-pages`,** then `fetch`
   the candidates. A page sitting at teamspace root is the one whose ancestor path
   comes back empty. That empty path is the only available signal.
4. **Scope every search.** `search` takes `teamspace_id` and `page_url`, and a scoped
   query beats a bare one by enough to be worth the extra fetch that finds the id.
   Set `page_size` low and `max_highlight_length` to 0 when you only need ids.

## Fetch cost

1. **Fetch cost is bimodal.** A container page returns little more than its child
   list. A leaf page returns its full content.
2. **Map containers first, open leaves last.** Walk the structure with container
   fetches until you know which leaf you actually need, then open that one. Opening
   leaves early is the main way a Notion session runs out of context.

## Duplicate titles

1. **Disambiguate by ancestor path.** Titles repeat across teamspaces by design, and
   `search` returns the duplicates undifferentiated.
2. **Icons do not disambiguate.** They do not appear in search results.
3. **Two candidates with the same title means stop and ask,** rather than picking the
   higher-ranked one. Filing a note under the wrong person or the wrong domain is
   silent and hard to notice later.

## Editing

1. **Read `notion://docs/enhanced-markdown-spec` before writing page content** the
   first time in a session. Pass the URI as the `id` to `fetch`. Notion-flavored
   markdown is not standard markdown, and guessing its syntax corrupts the page.
2. **`update_content` matches `old_str` exactly, against Notion's escaped form.**
   A dollar amount is stored as `\$3,600`, not `$3,600`. Fetch the page immediately
   before the edit and copy `old_str` out of that output rather than retyping it.
3. **Send the smallest edit region that is still unique.** Leave
   `replace_all_matches` at its default: failing on an ambiguous match is the
   behavior you want.
4. **Never pass `allow_deleting_content: true` on a page with child pages.** Without
   it, an `update_content` or `replace_content` that would orphan children fails and
   lists them, which is the guard working. Pass it only when the user has asked for
   those specific children to go.
5. **Prefer `update_content` over `replace_content`.** Replacing whole page content is
   how children get orphaned in the first place.

## There is no delete

1. **No tool trashes or deletes a page.** `move-pages` is the only relocation
   available.
2. **Never offer deletion.** Move the page under `Archive` instead, then tell the user
   to trash it themselves if that is what they want.
3. **Moving to the workspace parent makes a page private.** Use a `page_id` parent.

## Stale reads

1. **Re-fetch anything read more than a few turns ago, before acting on it.** The user
   edits the workspace while you work.
2. **A write against a stale id fails,** and a page the user trashed mid-task fails a
   `move-pages` call with an error that does not obviously say "trashed". Re-fetch
   first and the error never happens.
