---
name: waymark
description: Use when planning a long-distance walk or looking up a walking route with the Waymark tools, or when saving and editing a Waymark trip.
---

# Waymark

The Waymark MCP server answers from the pages published on https://waymarkroutes.com/. Its own tool descriptions and server instructions are current for the server you are connected to, so this file does not repeat them.

## Where to start

- `search` finds published routes and days. `fetch` reads one page in full by the id `search` returned.
- `read_published_route` reads one route day by day when you have its exact name or slug.

## What to say and not say

Every stage, distance, overnight stop, hut or season you state must appear in a tool result. If it does not, say Waymark does not have it. Do not fill a gap from memory.

## Before a write

`create_trip` and `update_trip` need the person signed in. `set_route` replaces a trip's days and `delete_trip` removes the trip for everyone with the link: ask the person and wait for a clear yes before either.
