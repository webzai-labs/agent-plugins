# Kosher Compass plugin

Connects your agent to [Kosher Compass](https://kosher-compass.com/en/), a site of verified kosher listings and trip plans. With it, the agent can search the kosher places (restaurants, groceries, bakeries, synagogues, Chabad houses, hotels), city guides, neighbourhoods and published vacations on the site, each place with its certifier and verification status, read a published vacation day by day, and, after you sign in, save a shared trip, put a question to your group on its decisions page, and share the link.

## What it contains

- **The Kosher Compass MCP server**, `https://kosher-compass.com/chatgpt/mcp`: remote, Streamable HTTP. Nothing runs on your machine.
- **A `kosher-compass` skill** that tells the agent where to start and what to confirm with you first.

## Signing in

`start_here`, `search`, `fetch`, `read_published_vacation` and `list_destination_days` need no account. `list_trips`, `get_trip`, `create_trip`, `update_trip`, `set_route`, `ask_group`, `share_trip` and `delete_trip` act on your Kosher Compass account, so the first one opens Kosher Compass's sign-in in your browser (OAuth 2.1 with PKCE). You sign in on the site and approve the client; the token goes straight back to the client. Nobody asks you to paste a token or a password.

## Installing

| Client | How |
|---|---|
| Claude Code | `/plugin marketplace add webzai-labs/agent-plugins` then `/plugin install kosher-compass@webzai-labs` |
| Claude (web, desktop) | Settings, Connectors, Add custom connector, `https://kosher-compass.com/chatgpt/mcp` |
| Cursor | Install from the Cursor marketplace, or add `{"mcpServers": {"kosher-compass": {"url": "https://kosher-compass.com/chatgpt/mcp"}}}` to `mcp.json` |
| ChatGPT | Search for Kosher Compass in ChatGPT's Apps |

## Support and privacy

- Website: <https://kosher-compass.com/en/>
- Support: <https://kosher-compass.com/en/support/>, support@kosher-compass.com
- Privacy policy: <https://kosher-compass.com/en/privacy/>
- Terms: <https://kosher-compass.com/en/terms/>
