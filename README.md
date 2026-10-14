<h1 align="center">Liftli MCP</h1>

<p align="center">
  The remote MCP server behind <a href="https://liftli.ai">Liftli</a>: a head of content for LinkedIn and X, inside the AI you already use.<br>
  Built by <a href="https://www.linkedin.com/in/odedtsamir/">Oded Tsamir</a>.<br><br>
  <a href="https://liftli.ai">Website</a> ·
  <a href="#install">Install</a> ·
  <a href="#tools">Tools</a> ·
  <a href="https://github.com/liftli-ai/linkedin-agent-skills">Free open-source skills</a> ·
  <a href="https://liftli.ai/developers">Developer docs</a>
</p>

<p align="center">
  <img alt="LinkedIn" src="https://cdn.worldvectorlogo.com/logos/linkedin-icon-2.svg" width="32">
  &nbsp;&nbsp;
  <img alt="X (Twitter)" src="https://cdn.simpleicons.org/x/000000" width="32">
  &nbsp;&nbsp;
  <img alt="Substack" src="https://cdn.simpleicons.org/substack/FF6719" width="32">
</p>

> **What this repository is.** Liftli is a hosted service. This repo holds its public documentation and the
> `server.json` that lists it in the [Official MCP Registry](https://registry.modelcontextprotocol.io) as
> `io.github.liftli-ai/liftli`. The server code is not open source, and there is nothing to self-host.
> The open-source part of Liftli is [liftli-ai/linkedin-agent-skills](https://github.com/liftli-ai/linkedin-agent-skills):
> 31 free, MIT-licensed LinkedIn skills that run on your own agent's model.

## What it does

Liftli learns your writing voice from your own posts, finds post ideas in your real work (voice notes,
meeting transcripts, GitHub activity, chats and the news), builds and remembers your strategy, drafts in
your voice and critiques every draft before you see it. Approved posts are published or scheduled to
LinkedIn (and X on the Business plan) through their official APIs. For Substack it plans and drafts newsletter issues and Notes;
you publish those on Substack yourself.

**Nothing publishes without your approval.** No browser extension and no bots acting on your profile.

## Install

The server is remote, served over HTTPS with MCP's Streamable HTTP transport. Nothing runs locally.

Connector URL:

```
https://mcp.liftli.ai/mcp
```

**Claude Code**

```bash
claude mcp add --scope user --transport http liftli https://mcp.liftli.ai/mcp
claude mcp login liftli
```

**Claude (web and desktop):** Customize (briefcase icon), then Connectors, then **Add custom connector**,
and paste the URL above into "Remote MCP Server URL".

**ChatGPT, Codex, Cursor, Grok and other clients:** add a custom or remote MCP server with the same URL.
Client-specific steps: [liftli.ai/developers](https://liftli.ai/developers).

You sign in once (secure WorkOS login). The free plan needs no card.

## Tools

24 tools, grouped by job. Ask your assistant in plain language; it picks the tool.

| Job | Tools |
|---|---|
| Start and profile | `strategist_briefing`, `onboard`, `save_profile`, `rewrite_profile` |
| Strategy and craft | `save_strategy`, `playbook` (13 briefs: hooks, ideas, calendar, growth, narrative, engagement, repurposing, Substack growth and more) |
| Writing | `plan_post`, `plan_comment`, `critique`, `ready_to_post`, `save_post` |
| Publishing | `connect_account` (LinkedIn, X, Google Calendar), `approve_post`, `distribute` (publish now, schedule, manage the queue) |
| Memory and ideas | `remember`, `recall`, `news_monitor` |
| Results | `log_outcome`, `analyze_results` |
| Media | `media` (generate, upload, attach, list) |
| Channels and account | `channel` (Telegram; WhatsApp coming soon), `contact_support`, `upgrade`, `dismiss_suggestion` |

The list above matches the live server's `tools/list`. You can check it without an account:

```bash
curl -s -X POST https://mcp.liftli.ai/mcp \
  -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

## How it differs

Most tools cover one end of the job: a scheduler, or a writer. Liftli covers the whole pipeline: it decides
what is worth saying from your real week, drafts it in your voice, pressure-tests the draft, and publishes
or schedules it after you approve. It lives inside the AI assistant you already use, so capturing an idea,
writing it and shipping it happen in one place, including from a voice note sent over Telegram.

## Safety model

- Publishing and scheduling use the platforms' official APIs, connected only when you link an account.
- Every draft waits for your approval.
- No browser extension and no automated actions on your profile.

## Support

Open an issue here, or use the `contact_support` tool from inside your assistant.

## License

The documentation in this repository is MIT-licensed. The Liftli service is proprietary and governed by the
[terms at liftli.ai](https://liftli.ai/terms).
