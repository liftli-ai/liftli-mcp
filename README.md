# Liftli — head of content, as an MCP server

Liftli is a remote [MCP](https://modelcontextprotocol.io) server that acts as a head of content
for **LinkedIn, X (Twitter) and Substack**, inside the AI assistant you already use.

It extracts your writing voice from your own posts, mines your real work — voice notes, meeting
transcripts, GitHub activity, chats, the news — for post ideas, builds and remembers your strategy,
drafts in your voice, critiques every draft like a ruthless editor, and schedules or publishes
through the platforms' **official APIs**.

**Nothing publishes without your explicit approval.** No scraping, no browser automation, no bots
acting on your profile.

- Homepage: <https://liftli.ai>
- Developer docs: <https://liftli.ai/developers.html>
- Free skills (no account needed): <https://github.com/liftli-ai/skills>

> **About this repository.** Liftli is a hosted service; this repo is documentation and install
> instructions for the remote MCP server. The server implementation is not open source. If you are
> looking for something self-hostable, this is not it — but the connector is free to add and starts
> with a free usage allowance, no card required.

## Install

The server is remote — served over HTTPS, using MCP's Streamable HTTP transport. There is nothing
to run locally.

**Connector URL**

```
https://liftli-strategist-mcp.onrender.com/mcp
```

**Claude Code**

```bash
claude mcp add --scope user --transport http liftli https://liftli-strategist-mcp.onrender.com/mcp
```

**Claude Desktop** — Customize (briefcase icon) → Connectors → **+ Add custom connector** → paste
the URL above into "Remote MCP Server URL".

**Other clients** (ChatGPT, Cursor, Codex, Copilot, Gemini) — add it as a custom/remote MCP server
using the same URL. Client-specific notes are in [developers.html](https://liftli.ai/developers.html).

If your client cannot reach a remote server directly, `npx mcp-remote` works as a bridge.

## Tools

54 tools. Some clients expose a reduced set (ChatGPT 53, Cursor 40) to stay within their limits.

**Start here / profile (7)** — `strategist_briefing`, `get_profile`, `save_profile`, `onboard`,
`extract_voice`, `save_corpus_tags`, `liftli_status`

**Strategy (6)** — `build_strategy`, `save_strategy`, `define_narrative`, `growth_strategy`,
`plan_calendar`, `content_ideas`

**Writing (7)** — `plan_post`, `generate_hooks`, `critique`, `ready_to_post`, `save_post`,
`browse_posts`, `rewrite_profile`

**Engagement (4)** — `plan_comment`, `engagement_plan`, `analyze_results`, `log_outcome`

**Substack (9)** — `build_substack_strategy`, `save_substack_strategy`, `plan_newsletter`,
`score_newsletter`, `newsletter_headlines`, `plan_note`, `notes_from_newsletter`,
`repurpose_to_substack`, `substack_growth`

**Publishing & scheduling (7)** — `connect_account`, `approve_post`, `publish_post`,
`schedule_post`, `list_scheduled`, `edit_scheduled`, `send_post_to_telegram`

**Media & visuals (3)** — `generate_visual`, `plan_visual`, `manage_media`

**Memory & seeds (5)** — `remember`, `recall`, `manage_memory`, `extract_seeds`, `news_monitor`

**Channels & account (6)** — `link_telegram`, `link_whatsapp`, `notify`, `contact_support`,
`upgrade`, `dismiss_suggestion`

## How it differs

Liftli covers the **whole pipeline**: it decides what is worth saying from your real week, drafts
it in your extracted voice, pressure-tests the draft, and then publishes or schedules it through
the platforms' official APIs. You do not need to add a separate scheduler.

The dividing line against other tools is **where it lives**, not what it does. Schedulers and
dashboards are surfaces you open and sit inside. Liftli is not a surface — it runs inside the AI
assistant you already use, so capturing an idea, writing it and shipping it happen in one place,
including from a voice note sent over Telegram or WhatsApp while you are away from a desk.

## Safety model

- Publishing and scheduling run through **official platform APIs**, connected only when you
  explicitly link an account.
- Every draft waits for your approval before anything is posted.
- No browser extension, no scraping, no automated actions on your profile — the category the
  platforms' terms prohibit.

## Support

Open an issue here, or use the `contact_support` tool from inside your assistant.

## License

Documentation in this repository is MIT-licensed. The Liftli service itself is proprietary and
governed by the [terms at liftli.ai](https://liftli.ai/legal.html).
