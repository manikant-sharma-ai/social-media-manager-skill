# Social Media Manager

A complete social media manager for one person or a whole brand. It researches,
plans, writes, humanises, schedules and analyses content across every major
platform, and it learns how the user posts so every draft sounds like them.

## When to use this skill

Trigger it whenever the user wants anything to do with running social media:

- "plan my content for next week / month"
- "write a LinkedIn / Instagram / X post about ..."
- "repurpose this blog / video / newsletter into posts"
- "schedule this", "post this", "queue it"
- "who engaged with my last post", "how did my posts do", "analytics"
- "find hooks / ideas / trends in my niche"
- "manage my social media end to end"

## First run - find the connectors (do this before anything else)

The very first time this skill is used - and any time the user says a platform is
missing - discover which social-media connectors are actually available instead
of assuming. Never guess that a platform is connected.

1. List what exists:
   - Available connectors in this workspace: `mcp_list_available`
   - Connectors already attached to this agent: `mcp_list_for_target`
   - Use `tool_search` with the platform name plus an action
     (e.g. "LinkedIn create post") to find the exact operations.
2. Match the user's platforms against what is available. The full method and a
   catalogue of social connectors live in `references/connectors.md`.
3. For each platform the user needs but that is not connected, call
   `request_authorization(integration="<slug>")` and give the user the link.
   Wait for them to connect. Never fake a connection.
4. Tell the user plainly which platforms are connected and which are still
   missing, and record the result in `knowledge/platforms.md`.

If no connector exists for a platform, do not pretend. Say it is missing, offer
the closest alternative (draft-only content the user can paste, or another
connector), and move on.

## The knowledge base - it makes the posts sound like the user

This skill keeps a small, editable knowledge base in `knowledge/`. Read it
before writing anything, and update it as you learn.

- `knowledge/brand-voice.md` - tone, do/don't words, emojis, hashtags, links.
- `knowledge/platforms.md` - which platforms are connected, handles, goals.
- `knowledge/content-pillars.md` - the themes the user posts about.
- `knowledge/past-posts.md` - their best-performing and recent posts.
- `knowledge/cadence.md` - how often, and when, they post.
- `knowledge/ingest-log.md` - what has been ingested and when.

### Ingesting what already exists

If the user already has content - a Drive folder, a doc, a sheet, past posts, a
website, a Notion page, a PDF - ingest it on request:

1. Read it with the right tool (Drive / Docs / Sheets / Notion / PDF / Word...).
2. Distil it into the knowledge base: voice patterns, pillars, formats, hooks,
   hashtags, what performed. Do not paste whole documents in.
3. Log the source and the date in `knowledge/ingest-log.md`.
4. Confirm to the user, in a few lines, what you learned.

## The workflow (research to report)

Full detail in `references/workflow.md`. In short:

1. **Understand the goal** - platform(s), audience, objective, deadline.
2. **Research** - trends, hooks, competitor and niche posts, keywords (use web
   search and any research connectors).
3. **Plan** - a calendar or a single-post brief: pillar, format, hook, CTA,
   time, target.
4. **Draft** - write in the user's voice, per platform
   (`references/platform-playbook.md`).
5. **Humanise** - strip AI tells so it reads like a person wrote it.
6. **Review with the user** - show the draft, get approval.
7. **Schedule / publish** - only after approval, via the connected connector.
8. **Engage** - draft replies to comments and DMs where the connector allows.
9. **Analyse and report** - pull the numbers, say what worked and what to change.

## Hard rules

- **Never publish without explicit approval.** Draft first, publish on a clear yes.
- **Never fabricate** metrics, reach, quotes or platform behaviour. If a number
  is not from a connector, label it an estimate.
- **Never hard-code credentials.** Use the connected connectors only.
- Respect each platform's rules and the user's own guidelines in
  `knowledge/brand-voice.md`.
- If a connector is missing or a platform is unsupported, say so and offer the
  closest alternative rather than pretending.

## Files

- `README.md` - a plain-language guide for the user.
- `references/connectors.md` - how to find and connect social connectors.
- `references/workflow.md` - the research-to-report workflow in detail.
- `references/platform-playbook.md` - per-platform formats and limits.
- `references/knowledge-base.md` - how the knowledge base works.
- `knowledge/` - the user's data (templates to fill in).
