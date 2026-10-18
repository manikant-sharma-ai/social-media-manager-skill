# Finding and connecting social connectors

This file is how the skill gets "access" to social media. Never assume a platform
is connected - discover it.

## The method

1. **List what exists.**
   - `mcp_list_available` - every connector this workspace offers.
   - `mcp_list_for_target` - the ones already attached to this agent.
2. **Search for the exact action** with `tool_search`, e.g.
   `"LinkedIn create post"`, `"Reddit submit post"`, `"Instagram publish"`.
3. **Match** the user's platforms to what exists (tables below help).
4. **Connect what is missing** - `request_authorization(integration="<slug>")`
   returns a link; give it to the user and wait.
5. **Bind if needed** - `mcp_bind(mcp_id=...)` attaches an available connector to
   this agent; `mcp_unbind` removes it.
6. **Record** the outcome in `knowledge/platforms.md`.

There is no tool here to add a brand-new external MCP server by URL. If a tool
the user wants is not in `mcp_list_available`, it has to be added to the
workspace first (by the user or a workspace admin). Say this plainly rather than
pretending you connected it.

## Connectors native to this workspace (social-relevant)

These are already in the workspace catalogue and can be bound/authorised.

| Connector | Slug | What it is good for |
| --- | --- | --- |
| LinkedIn | `linkedin` | Posts, images, company pages, engagement |
| Reddit | `reddit` | Search, post and comment in communities |
| Discord | `discord` | Community posts, announcements |
| Canva | `canva` | Design images and graphics for posts |
| Bannerbear | `bannerbear` | Generate images/videos from templates |
| VEED | `veed` | AI talking-avatar videos |
| Runway | `runway` | Generate images and videos |
| Meta Ads | `metaads` | Meta ad campaign performance |
| Google Ads | `googleads` | Google ad campaign performance |
| Mailchimp | `mailchimp` | Email audiences and campaigns |
| Slack | `slack` | Team coordination, approvals |
| Notion | `notion` | Content calendar and briefs |
| Airtable | `airtable` | Content calendar as a base |
| Google Sheets / Drive / Docs | `googlesheets`, `googledrive`, `googledocs` | Calendars, drafts, brand assets |
| Web Search | `web-search` | Trends, hooks, competitor research |

Slugs are what `request_authorization(integration=...)` expects. Confirm exact
slugs with `mcp_list_available`.

## External social-media tools that publish their own MCP server

Many popular schedulers now ship an official MCP server. If the user already
uses one of these, it is often the fastest route to real publishing. Check the
vendor page before promising anything - plans and endpoints change.

| Tool | MCP endpoint (as documented) | Platforms | Notes |
| --- | --- | --- | --- |
| Metricool | `https://ai.metricool.com/mcp` | Instagram, TikTok, LinkedIn, Facebook, X, YouTube, Pinterest, Threads, Bluesky, Twitch (+ Meta/Google/TikTok Ads analytics) | Works on the free plan; OAuth. Schedule and edit posts, read analytics and competitors. |
| Buffer | `https://mcp.buffer.com/mcp` | 11 channels incl. Instagram, TikTok, YouTube, Pinterest, Bluesky, Mastodon, X | Free on every plan; posts land as drafts or scheduled. |
| Hootsuite | `https://mcp.hootsuite.com/perch` (+ Nest, Lumen, Parliament) | Its connected networks | Perch publishes and schedules; per-seat pricing. |
| Publora | `https://mcp.publora.com` | LinkedIn, X, Threads, Mastodon, Bluesky, Instagram, Facebook and more | Bearer API key; ~32 tools incl. media and first comments. |
| Postiz | `https://mcp.postiz.com/mcp` or `https://api.postiz.com/mcp` | 30+ (incl. Reddit, Discord, Telegram, Mastodon) | Open source, self-hostable. |
| Typefully | `https://mcp.typefully.com` | X, LinkedIn, Threads, Bluesky, Mastodon | Text-first; OAuth. |
| Planable | (vendor) | Its connected pages | Creates drafts that go through approval. |
| Sprout Social | (vendor) | TikTok data only | Read/analytics, not publishing, as documented. |
| Others with an official MCP | - | - | SocialPilot, Vista Social, Zoho Social, Agorapulse, Pallyy, SocialBu, ContentStudio, Nuelink, Zernio (formerly Late), Blotato, Ayrshare, Simplified, Upload-Post, Publer, Tailwind, FeedHive, Planoly, Social Champ, Oktopost, Ocoya, Predis.ai, Mixpost, RecurPost, Outstand, Socialync, PostFast, Schedchie, ZocialOne (India-focused, INR pricing). |

If the user names a tool, search for its MCP page, confirm the endpoint and the
platforms it covers, and use it through whatever connection this workspace
supports.

## Common confusions (avoid these)

- **Superhuman** is an email and calendar MCP, *not* a social-media tool. Do not
  treat it as a social connector.
- **Later, SocialBee, Loomly, Post Planner** do not publish their own MCP server
  as of the latest check. Do not claim they do.
- Some tools are **read/analytics only** over MCP (e.g. Sprout Social's TikTok
  data). Publishing may not be possible; check first.
- Instagram, TikTok and YouTube usually need **media attached** before a post can
  be published; create it as a draft, add media, then schedule.

## Sources

Vendor documentation, read while building this skill: Metricool help centre
(help.metricool.com), Publora docs (docs.publora.com), Superhuman help centre
(help.superhuman.com), plus comparison pages at dunsocial.com, schedchie.com,
contentdrifter.com and planpo.st. Re-check the vendor page before relying on a
detail, since plans, endpoints and platform support change often.
