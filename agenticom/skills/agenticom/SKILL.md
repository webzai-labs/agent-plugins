---
name: agenticom
description: Use when the user mentions agenticom, an agenticom link or spec, or asks to publish, revise, read or share a planning spec on agenticom.
---

# agenticom

agenticom hosts the specs a planning session produces — pages composed of the planning kit's
components — as versioned artifacts with reviews. The agenticom MCP server is how an agent publishes,
reads and shares them, as the person who signed in.

## When the agenticom tools are missing

The server is `https://agenticom.app/mcp` (Streamable HTTP, OAuth sign-in in the person's own
browser). Read `https://agenticom.app/docs/connecting-to-agenticom` — the server's own guide — and
follow it. Never ask for a token or a password: the sign-in completes between the browser and the
client.

## Where to start

- `get_docs` with topic `publishing-on-agenticom` before publishing or revising a spec — it is the
  whole flow. The topic `README` indexes the rest: how a session is run, how a spec is written and a
  mock drawn, and the kit's own contract documentation.
- `upload_draft` sends a spec's source and answers with the build: the checks that failed, or a draft
  only the person sees. `promote_draft` publishes it as the next version.
- A revision names the artifact and the version it was built on; if a newer version was published
  since, the upload is refused and nothing is lost.

## Before a write

Every tool is annotated with its kind: a read changes nothing; an additive write only adds; a
destructive one deletes or overwrites; an outward one reaches people (adding a member, inviting).
Confirm with the person before every destructive or outward call. No tool widens who may read an
artifact — that is its owner's, in the app.
