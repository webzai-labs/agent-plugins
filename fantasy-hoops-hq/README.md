# Fantasy Hoops HQ plugin

Connects your agent to [Fantasy Hoops HQ](https://fantasyhoopshq.com/), a fantasy basketball site. With it, the agent can search and read the site's guides, look up NBA players in the site's player list and count each team's games over a date range, and, after you sign in, read the leagues and roster saved on your account, see who plays tonight, follow your matchup in the planner, check trades, and edit the saved roster and lineup.

## What it contains

- **The Fantasy Hoops HQ MCP server**, `https://fantasyhoopshq.com/chatgpt/mcp`: remote, Streamable HTTP. Nothing runs on your machine.
- **A `fantasy-hoops-hq` skill** that tells the agent where to start and what to confirm with you first.

## Signing in

`search_guides`, `get_guide`, `get_players` and `get_schedule` need no account. The league, roster, matchup and trade tools act on your Fantasy Hoops HQ account, so the first one opens Fantasy Hoops HQ's sign-in in your browser (OAuth 2.1 with PKCE). They change only what is saved on Fantasy Hoops HQ, never your ESPN, Yahoo, Sleeper, Fantrax or CBS league. You sign in on the site and approve the client; the token goes straight back to the client. Nobody asks you to paste a token or a password.

## Installing

| Client | How |
|---|---|
| Claude Code | `/plugin marketplace add webzai-labs/agent-plugins` then `/plugin install fantasy-hoops-hq@webzai-labs` |
| Claude (web, desktop) | Settings, Connectors, Add custom connector, `https://fantasyhoopshq.com/chatgpt/mcp` |
| Cursor | Install from the Cursor marketplace, or add `{"mcpServers": {"fantasy-hoops-hq": {"url": "https://fantasyhoopshq.com/chatgpt/mcp"}}}` to `mcp.json` |
| ChatGPT | Search for Fantasy Hoops HQ in ChatGPT's Apps |

## Support and privacy

- Website: <https://fantasyhoopshq.com/>
- Support: <https://fantasyhoopshq.com/support/>, support@fantasyhoopshq.com
- Privacy policy: <https://fantasyhoopshq.com/privacy/>
- Terms: <https://fantasyhoopshq.com/terms/>
