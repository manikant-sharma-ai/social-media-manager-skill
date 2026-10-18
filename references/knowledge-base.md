# How the knowledge base works

The `knowledge/` folder is what makes this skill sound like the user instead of
like a generic AI. It is plain text, the user can read and edit every file, and
the skill should keep it up to date.

## The files

| File | Holds | Update when |
| --- | --- | --- |
| `brand-voice.md` | Tone, do/don't words, emoji policy, hashtag policy, link policy | You learn a new voice rule |
| `platforms.md` | Which platforms are connected, handles, goals, audience per platform | A connector is connected or removed |
| `content-pillars.md` | The 3-6 themes the user posts about, with example angles | The strategy changes |
| `past-posts.md` | Best-performing and recent posts, with the numbers | After every reporting round |
| `cadence.md` | How often and when the user posts, per platform | The schedule changes |
| `ingest-log.md` | What source was ingested and when | After every ingestion |

## Filling it in

Two ways, both fine:

1. **The user fills it in.** Give them the templates and a couple of examples;
   they edit the files directly.
2. **The assistant fills it in.** The user points at their existing content and
   the assistant reads it and writes the distilled version into the files.

Never overwrite something the user wrote with an assumption. If you are unsure,
add a new line and mark it `(draft - confirm)`.

## Ingesting existing content

When the user says "learn from my content", "here is my old content", or points
at a folder, document, sheet, website or past posts:

1. Read the source with the right tool.
2. Extract, do not copy:
   - Voice: recurring phrases, tone, emoji use, sentence length.
   - Pillars: what topics repeat.
   - Formats and hooks: what shapes the posts take.
   - Performance: what got the most engagement, if the numbers exist.
3. Write the distilled notes into the right `knowledge/` file.
4. Add a line to `ingest-log.md`: source, what was learned, date.
5. Tell the user, in a few lines, what changed.

## Privacy and safety

- Keep only what is useful for writing and scheduling. Do not paste whole
  private documents in.
- Never store passwords, tokens or keys in the knowledge base.
- If the content contains anything sensitive (client names, personal data), keep
  only what the posts genuinely need.
