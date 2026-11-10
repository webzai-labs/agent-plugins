# Plugins: traileo and agenticom for Claude, Cursor and ChatGPT

One folder per product. Each folder is ONE plugin that three hosts read, each from its own manifest:

| File | Read by | What it is |
|---|---|---|
| `<product>/.claude-plugin/plugin.json` | Claude Code, Claude's plugin directory | the Claude manifest |
| `<product>/.mcp.json` | Claude Code | the remote MCP server (`type: http`) |
| `<product>/.cursor-plugin/plugin.json` | Cursor | the Cursor manifest; the MCP server is declared inline |
| `<product>/plugin.json` | ChatGPT (and any Agent Plugins host) | the portable manifest; ChatGPT's listing, review test cases and links are under `extensions["com.openai"]` |
| `<product>/mcp.json` | ChatGPT | the remote MCP server (`type: streamable-http`), OAuth with dynamic client registration |
| `<product>/skills/<product>/SKILL.md` | all three | a short onboarding skill: where to start, what to confirm first. It points at the server's own docs rather than copying them |
| `<product>/assets/logo.png` | Cursor, ChatGPT; the Claude portal asks for it as an upload | square logo (copied from the product's app icons) |
| `.claude-plugin/marketplace.json`, `.cursor-plugin/marketplace.json` | Claude Code, Cursor | this folder as a marketplace listing both plugins |

Nothing here runs: both servers are remote (`https://traileo.app/mcp`, `https://agenticom.app/mcp`), signed in
with OAuth 2.1 + PKCE in the user's browser, with dynamic client registration — no client id, no secret, no
token anywhere in these files.

**Checked here:** `claude plugin validate` passes for both plugins and the marketplace; the Cursor manifests
validate against `cursor/plugins`' published JSON schemas; `plugin.json` validates against the Agent Plugins
1.0.0 schema. **Not checkable here:** `mcp.json` carries OpenAI's `extensions["com.openai"].auth` block, which
the generic Agent Plugins schema does not allow — OpenAI's own scan is what judges it.

## What the servers already meet

- Every tool has a `title` and all of `readOnlyHint`, `destructiveHint`, `openWorldHint`, `idempotentHint`
  set explicitly (Claude's and ChatGPT's review both require it; a registry spec in each server enforces it).
- Unauthenticated `POST /mcp` answers `401` with `WWW-Authenticate: Bearer resource_metadata=…`.
- The protected-resource metadata's `resource` is the MCP url itself, path included
  (`/.well-known/oauth-protected-resource/mcp`). **This needs the server change in the same PR deployed —
  to production, so it needs a promote.**
- `/.well-known/openai-apps-challenge` serves the `OPENAI_APPS_CHALLENGE_TOKEN` var as plain text (404 while
  unset) — the domain verification ChatGPT's submission asks for.
- Public pages: `/privacy`, `/terms`, `/contact` on both domains; the connect guide at
  `https://traileo.app/docs/connect` and `https://agenticom.app/docs/connecting-to-agenticom`.

## Submitting — what each host needs, in order

### 0. Before any host

1. The PR that added this folder is merged and **promoted to production** (the metadata change above).
2. **A public GitHub repository holding this folder.** Claude's plugin directory and Cursor's marketplace both
   read a plugin from a repository, and both need it public by the time the listing goes live. `devzai` is
   private, so copy `plugins/` to its own public repository (for example `webzai-labs/agent-plugins`) and keep
   it in sync from here. The copy must contain no symlinks.
3. **A reviewer test account per product**, on production, with sample data — not a real user's account. It
   must sign in with email + password, **no MFA, no email code, no magic link** (ChatGPT's rule). The traileo
   account needs a project named **Demo Shop** with a few feedbacks (one about a checkout button), one of them
   assigned to the account; the agenticom account needs a spec named **Onboarding**. The test cases in
   `plugin.json` refer to them.
4. **A walkthrough video per product** for ChatGPT (`demo_recording_url`, currently `TODO`): connecting, the
   sign-in, and two or three of the positive test cases being run.
5. The publisher name. The files say **Amir Gabay** (traileo charges as a private person). ChatGPT replaces it
   with the verified developer identity's name; Claude asks for a company name and contact.

### 1. Claude

Two separate submissions per product, both at **claude.ai → admin settings → Directory** (claude.ai/directory/manage):

- **MCP connector**: server url `https://<product>.app/mcp`, authentication `oauth_dcr`. Asks for: icon
  (`assets/logo.png`), one-liner (≤200 chars) and description (≤2,000), 1–5 categories, documentation url,
  privacy policy url, support contact, the test account, data-handling answers and the acknowledgements.
  Claude's hosted apps sign in with redirect `https://claude.ai/api/mcp/auth_callback`; dynamic registration
  accepts it, nothing to configure.
- **Plugin bundle**: the public repository, plugin path `traileo` (then `agenticom` as a second submission).
  Run `claude plugin validate ./<product>` first. Bump `version` in `.claude-plugin/plugin.json` on every update.

### 2. Cursor

Submit at **cursor.com/marketplace/publish**, from the public repository; the repository's
`.cursor-plugin/marketplace.json` lists both plugins. Every plugin is reviewed by hand, and the queue has been
reported slow.

A one-click install link (no marketplace needed) — format as documented by Cursor, worth verifying once in
Cursor before it goes on a page:

- traileo: `cursor://anysphere.cursor-deeplink/mcp/install?name=traileo&config=eyJ1cmwiOiAiaHR0cHM6Ly90cmFpbGVvLmFwcC9tY3AifQ==`
- agenticom: `cursor://anysphere.cursor-deeplink/mcp/install?name=agenticom&config=eyJ1cmwiOiAiaHR0cHM6Ly9hZ2VudGljb20uYXBwL21jcCJ9`

(`config` is base64 of `{"url": "https://<product>.app/mcp"}`.)

### 3. ChatGPT

In the OpenAI Platform dashboard (plugins), after **individual or business verification** of the publisher:

1. Connect the MCP server `https://<product>.app/mcp`, OAuth, client mode **DCR**.
2. **Domain verification**: the dashboard issues a token. Set it as the `OPENAI_APPS_CHALLENGE_TOKEN` var on
   that product's **production** worker (traileo's worker is in Nir's Cloudflare account) — then
   `https://<product>.app/.well-known/openai-apps-challenge` serves it. Setting a production var is Amir's.
3. **Scan tools.** If the scan flags something, it is a server change: say what it flagged.
4. Upload the package: a ZIP of the product folder (`plugin.json`, `mcp.json`, `skills/`, `assets/`, README,
   LICENSE). Fill `review.demo_recording_url` first. Test credentials go in the dashboard's review form, never
   in the ZIP.
5. If the dashboard shows the OAuth callback url it uses, nothing needs registering: dynamic registration
   accepts whatever redirect the client registers.

## Open points

- **License**: the plugin folders say MIT. They hold only configuration and two short skills, not product
  code, but it is a choice — change `license` and `LICENSE` together if it should be something else.
- **agenticom's `/contact`** answers 200 but is the app shell, not a written support page; ChatGPT's
  `supportURL` must be a customer-support page. Confirm it shows something useful signed out, or point
  `supportURL` elsewhere.
- **traileo's help center (`/help`)** is not in production yet; the documentation url used is the
  server-served connect guide (markdown). Claude's directory asks for setup and usage docs a person can
  read — a help article would serve better once `/help` ships.
- **agenticom's ChatGPT listing**: agenticom's planning decided inline-rendering hosts are not its target
  (`planning/agenticom-planning/decisions.md`). This plugin has no UI widget — it is the plain tool surface,
  which ChatGPT accepts — but listing it there is a product decision.
