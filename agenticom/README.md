# agenticom plugin

Connects your agent to [agenticom](https://agenticom.app), where the specs a planning session
produces are published as versioned artifacts with reviews. With it, the agent can read the publishing
flow and the planning kit's documentation, upload a draft and see what the build checked, publish it
as the next version, and read and manage the projects, workspaces and specs you can reach — always as
you.

## What it contains

- **The agenticom MCP server**, `https://agenticom.app/mcp` — remote, Streamable HTTP. Nothing runs
  on your machine.
- **An `agenticom` skill** that tells the agent where to start and what to confirm with you first.

## Signing in

The first call opens agenticom's sign-in in your browser (OAuth 2.1 with PKCE). You sign in and
approve the client; the token goes straight back to the client. Nobody asks you to paste a token or a
password.

## Installing

| Client | How |
|---|---|
| Claude Code | `/plugin marketplace add <this repository>` then `/plugin install agenticom@webzai-labs` |
| Claude (web, desktop) | Settings → Connectors → Add custom connector → `https://agenticom.app/mcp` |
| Cursor | Install from the Cursor marketplace, or add `{"mcpServers": {"agenticom": {"url": "https://agenticom.app/mcp"}}}` to `mcp.json` |
| ChatGPT | Install the agenticom plugin from the ChatGPT directory |

Full guide, served by the server itself: <https://agenticom.app/docs/connecting-to-agenticom>.

## Support and privacy

- Support: <https://agenticom.app/contact> · support@agenticom.app
- Privacy policy: <https://agenticom.app/privacy>
- Terms: <https://agenticom.app/terms>
