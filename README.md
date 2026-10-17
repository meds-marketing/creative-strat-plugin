# meds-marketing

Connect your agent to the creative-operations workspace. Read production issues, inspect scripts and performance, save requested internal records, and review script proposals.

[GitHub](https://github.com/meds-marketing/creative-strat-plugin) · [Releases and ZIP download](https://github.com/meds-marketing/creative-strat-plugin/releases/latest) · [Connection setup](https://creator.meds-marketing.com/integrations/agent-clients)

Endpoint: https://creator.meds-marketing.com/mcp

The plugin is displayed as `meds-marketing`. Its package, MCP server and workflow skill identifiers remain `creative-strat` so existing installations and Google connections continue to work. The Meds Marketing logo is bundled as `assets/icon.png` and referenced by both listing and composer icon fields in the portable and Codex manifests.

## Codex

```sh
codex plugin marketplace add meds-marketing/creative-strat-plugin
codex plugin add creative-strat@creative-strat
codex mcp login creative-strat --scopes cs:read
```

Complete Google OAuth when prompted. If this client does not expose plugin-server OAuth login, configure a direct connection instead (do not keep duplicate connections enabled):

```sh
codex mcp add creative-strat --url https://creator.meds-marketing.com/mcp
codex mcp login creative-strat --scopes cs:read
```

## Claude Code

```sh
claude plugin marketplace add meds-marketing/creative-strat-plugin
claude plugin install creative-strat@creative-strat --scope user
claude mcp login plugin:creative-strat:creative-strat
```

Start a new session after installation. Read the creative-strat skill when working in the workspace. For a manual connection, use `claude mcp add --transport http --scope user creative-strat https://creator.meds-marketing.com/mcp`, then `claude mcp login creative-strat`.

## Monthly status (0.3.0)

Ask "What is the latest status for October?". The agent uses `cs_get_production_status` with the selected YYYY-MM month to read the real influencer Tracker. It returns full-month counts, paginated rows, source links and live retrieval times. Existing assignment tables are a separate workflow and may be empty while the Tracker contains production. Internal role is required. A dated snapshot fallback cannot verify the latest status; test tabs are excluded. Recorded approval and brief-sent fields do not prove asset delivery.

## Access and example tasks

Start with read access. Ask “What needs attention for BlueChew?”, “Show the production overview”, or “Find the script for this assignment.” For authoring, reauthorize the connection with `cs:read cs:write` through your client's supported OAuth configuration, then inspect the consent screen. Codex's explicit path is `codex mcp login creative-strat --scopes cs:read,cs:write` for a direct connection. Never assume editing was granted until the tool catalog/context confirms it. Intake metadata uses a separate `cs:intake.read` scope.

Connect with any Google profile explicitly linked to your Creative Strat user. Linking another sign-in does not connect its inbox. Manage clients and disconnect at https://creator.meds-marketing.com/integrations/agent-clients. Browser logout does not revoke agent grants.

Chat is complete in tools-only clients; MCP Apps rendering depends on the host. No email sending, Sheets writes, publishing or media generation is included. A package installation is not proof of an authenticated connection. Reconnect/restart a client with a stale catalog after a server or package update.

The public repository contains only the plugin, client marketplaces and setup instructions. Application/backend code and internal operational documentation are maintained separately. Local installation uses the same commands with the public repository checkout path as marketplace source. No credentials or registered ChatGPT app binding are included.

## Inline script review (0.2.0)

Ask your agent to show a script proposal. `cs_show_script_review` compares the full current and proposed documents. Read-only users can inspect it; internal write grants can save a pending document suggestion or apply a direct update. Changed scripts require a fresh rebased proposal. Unknown save responses retain their original command/key for safe checking. Chat remains complete in tools-only clients. Proposal state is temporary; keep it in chat for recovery after reconnecting.


## Update and troubleshoot

Update the marketplace in your client, then update/reinstall `creative-strat@creative-strat` and start a fresh session. Claude Code supports `claude plugin marketplace update creative-strat` followed by `claude plugin update creative-strat@creative-strat`. Codex supports `codex plugin marketplace upgrade creative-strat` followed by `codex plugin add creative-strat@creative-strat`. Review the client context before editing; updating a plugin does not grant editing access.

If you previously added the private application repository as the `creative-strat` marketplace, it can also include other plugins. Use a clean client setup or migrate those other plugin sources before replacing that shared marketplace. Existing authenticated connections need no new Google grant solely for this public packaging release.

Use the hosted connection page for workspace access questions. Open a GitHub issue for plugin setup problems with your client version and sanitized error message; omit tokens, private script bodies and creator contact details.

## App data parity (0.4.0)

Script discovery includes organization-owned standalone imports. Registered Google Docs links resolve to the saved app document; reviews and edits use its exact revision. Saved assignments and influencer briefs are separate tools from monthly Tracker production. Performance evidence includes actual date coverage. Local script saves do not export to Google Docs or send email.
