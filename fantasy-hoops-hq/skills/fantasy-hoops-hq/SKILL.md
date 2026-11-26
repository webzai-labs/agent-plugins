---
name: fantasy-hoops-hq
description: Use for fantasy basketball questions with the Fantasy Hoops HQ tools: guides, NBA player lines and schedule counts, and the signed-in manager's saved leagues, roster, matchups and trades.
---

# Fantasy Hoops HQ

The Fantasy Hoops HQ MCP server answers from the pages published on https://fantasyhoopshq.com/. Its own tool descriptions and server instructions are current for the server you are connected to, so this file does not repeat them.

## Where to start

- A rule or a how-to: `search_guides`, then `get_guide`. Quote only what the guide says.
- Players and games: `get_players` (up to 25 names) and `get_schedule` (game counts only).
- Signed in: `list_leagues`, then `get_roster`, `get_tonight`, `get_matchup` and the trade tools for that league.

## What to say and not say

Never invent a stat, a tip-off, an opponent or a games limit. If the tools do not have it, say so.

## Before a write

The tools change only what is saved on Fantasy Hoops HQ, never ESPN, Yahoo, Sleeper, Fantrax or CBS. `drop_players`, `set_lineup`, `remove_opponent` and the other tools marked destructive need the person's clear yes, then `confirm: true`.
