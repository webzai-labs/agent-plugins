# Waymark plugin

Connects your agent to [Waymark](https://waymarkroutes.com/), a site of published long-distance walking routes. With it, the agent can search the routes and days on the site, read one in full, read a route day by day with only the stages, distances and stops its page states, and, after you sign in, save the plan as a shared trip and edit it.

## What it contains

- **The Waymark MCP server**, `https://waymarkroutes.com/chatgpt/mcp`: remote, Streamable HTTP. Nothing runs on your machine.
- **A `waymark` skill** that tells the agent where to start and what to confirm with you first.

## Signing in

`search`, `fetch` and `read_published_route` need no account. `list_trips`, `get_trip`, `create_trip`, `update_trip`, `set_route` and `delete_trip` act on your Waymark account, so the first one opens Waymark's sign-in in your browser (OAuth 2.1 with PKCE). You sign in on the site and approve the client; the token goes straight back to the client. Nobody asks you to paste a token or a password.

## Installing

| Client | How |
|---|---|
| Claude Code | `/plugin marketplace add webzai-labs/agent-plugins` then `/plugin install waymark@webzai-labs` |
| Claude (web, desktop) | Settings, Connectors, Add custom connector, `https://waymarkroutes.com/chatgpt/mcp` |
| Cursor | Install from the Cursor marketplace, or add `{"mcpServers": {"waymark": {"url": "https://waymarkroutes.com/chatgpt/mcp"}}}` to `mcp.json` |
| ChatGPT | Search for Waymark in ChatGPT's Apps |

## Support and privacy

- Website: <https://waymarkroutes.com/>
- Support: <https://waymarkroutes.com/support>, hello@waymarkroutes.com
- Privacy policy: <https://waymarkroutes.com/privacy>
- Terms: <https://waymarkroutes.com/terms>
