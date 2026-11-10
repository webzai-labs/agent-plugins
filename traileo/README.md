# traileo plugin

Connects your agent to [traileo](https://traileo.app) — recorded observations about web pages (a
defect, a UX or copy note) with the evidence captured alongside them: the page, a video, the steps,
the network and console activity, and screenshots. With it, the agent can read a feedback and its
evidence, comment on it, triage and assign it, file a new one, and manage the projects and workspaces
that hold them — always as you, and refused exactly where the traileo web app would refuse you.

## What it contains

- **The traileo MCP server**, `https://traileo.app/mcp` — remote, Streamable HTTP. Nothing runs on
  your machine.
- **A `traileo` skill** that tells the agent where to start and what to confirm with you first.

## Signing in

The first call opens traileo's sign-in in your browser (OAuth 2.1 with PKCE). You sign in with your
traileo account and approve the client; the token goes straight back to the client. Nobody asks you
to paste a token or a password.

## Installing

| Client | How |
|---|---|
| Claude Code | `/plugin marketplace add <this repository>` then `/plugin install traileo@webzai-labs` |
| Claude (web, desktop) | Settings → Connectors → Add custom connector → `https://traileo.app/mcp` |
| Cursor | Install from the Cursor marketplace, or add `{"mcpServers": {"traileo": {"url": "https://traileo.app/mcp"}}}` to `mcp.json` |
| ChatGPT | Install the traileo plugin from the ChatGPT directory |

Full guide, served by the server itself: <https://traileo.app/docs/connect>.

## Support and privacy

- Support: <https://traileo.app/contact> · support@traileo.app
- Privacy policy: <https://traileo.app/privacy>
- Terms: <https://traileo.app/terms>
