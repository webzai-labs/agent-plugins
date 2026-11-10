---
name: traileo
description: Use when the user mentions traileo, a traileo feedback or link, or asks to read, triage, comment on or file feedback about a web page that was recorded with traileo.
---

# traileo

traileo records observations about web pages — a defect, a UX or design suggestion, a copy or
accessibility note — with the evidence somebody captured attached: the page, a video, the steps, the
network and console activity, screenshots. The traileo MCP server is how an agent reads them and acts
on them, as the user who signed in.

## When the traileo tools are missing

The server is `https://traileo.app/mcp` (Streamable HTTP, OAuth sign-in in the user's own browser).
Read `https://traileo.app/docs/connect` — the server's own guide — and follow it. Never ask the user
for a token or a password: the sign-in completes between their browser and the client.

## Where to start

- `list_projects` when you do not already have a project id.
- `get_format_docs` for the structures the reads return — the server documents itself, so this file
  does not repeat it, and what it says is current for the server you are connected to.
- A traileo link names a feedback; `get_feedback` reads it with its evidence.

## Before a write

Every tool is annotated with what it does to the data. A read changes nothing; an additive write only
adds; a destructive one deletes or overwrites; `invite_workspace_collaborator` emails a real person and
uses a billable seat. Confirm with the user before a destructive or open-world call — each tool's own
description says what it takes with it, and several are reversible.
