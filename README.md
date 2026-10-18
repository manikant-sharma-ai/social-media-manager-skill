# Social Media Manager — an agent skill

An AI-agent skill that runs social media end to end. It finds which social
connectors are available, keeps a knowledge base of your brand, and then plans,
writes, humanises, schedules and reports across every major platform.

## What it does

- Discovers which social connectors the agent actually has, and tests access.
- Tells you plainly what is connected, what is blocked, and what is missing.
- Keeps a knowledge base of your brand voice, platforms, pillars, past posts and
  cadence — so every post sounds like you.
- Studies your existing posts, finds the ones that worked, and compounds them.
- Plans a calendar or a single post; writes it per platform; strips the AI tells;
  gets your approval; schedules or publishes through the connector; then reports
  what worked.

## Platforms it covers

LinkedIn, Instagram, Facebook, X (Twitter), YouTube, TikTok, Pinterest, Threads,
Bluesky, Mastodon, Reddit, Discord, Telegram, Twitch and Google Business Profile.
If a platform is not available as a connector, the skill says so and points to a
scheduler connector that can cover it.

## How it works

On first use — whatever you type — the skill does the same first step: it lists
the connectors available, tests real access, and tells you which platforms are
ready and which need connecting. Then it asks about your topic, audience,
platforms and cadence, studies your existing content, and starts planning.

It is connector-agnostic: it works with whatever social connectors your agent
has — native ones such as LinkedIn and Reddit, or a scheduler connector such as
Metricool, Buffer, Publora, Hootsuite, Postiz or Typefully.

## What's in this repo

- `SKILL.md` — the skill definition. Read this first.
- `references/` — connector discovery, the research-to-report workflow, the
  per-platform playbook, and how the knowledge base works.
- `knowledge/` — the templates you fill in: brand voice, platforms, content
  pillars, past posts, cadence, ingest log.
- `README.md` — this file.

## Install

Add the folder as a skill to your agent (drop it into the agent's skills
directory, or install it through your platform's skill mechanism), then ask the
agent to manage your social media. It will do the connector discovery first.

## Design rules

- Never publishes without explicit approval.
- Never fabricates metrics, reach or results.
- Never stores credentials; it uses the connectors you authorise.

## Licence

MIT — see `LICENSE`.
