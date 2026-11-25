---
name: kosher-compass
description: Use when planning kosher travel or looking up kosher restaurants, groceries, synagogues or city guides with the Kosher Compass tools, or when saving and sharing a Kosher Compass trip.
---

# Kosher Compass

The Kosher Compass MCP server answers from the pages published on https://kosher-compass.com/en/. Its own tool descriptions and server instructions are current for the server you are connected to, so this file does not repeat them.

## Where to start

- Call `start_here` on the first turn. It returns the opening to give the person: what Kosher Compass offers and the next steps.
- `search` finds published places, city guides and vacations. `fetch` reads one in full by the id `search` returned.
- `read_published_vacation` reads a published vacation day by day; `list_destination_days` ranks a destination's published days for a party (kids, adults, family, couple).

## What to say and not say

Every certifier, verification status, address or time you state must come from a tool result. If the site does not have it, say so. Do not add places from memory.

## Before a write

`create_trip`, `update_trip`, `ask_group` and `share_trip` need the person signed in. `set_route` replaces a trip's days and `delete_trip` removes the trip for everyone with the link: ask the person and wait for a clear yes before either. Nothing here books, pays, or changes a published listing.
