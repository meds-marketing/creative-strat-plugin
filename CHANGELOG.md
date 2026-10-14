# Changelog

## 0.3.0

- Add month-aware production status from the actual influencer Tracker workbooks, with live reads, paginated creator rows and explicit snapshot freshness.
- Include tracker production alongside assignment records in the workspace and optional overview.
- Exclude test tabs, preserve internal-only Tracker access and distinguish unavailable sources from empty months.
- Server protocol is 1.3.0. Existing Google grants and stable connection identifiers remain valid.

## 0.2.2

- Display the plugin as `meds-marketing`, retaining existing package, server and skill identifiers.
- Bundle the Meds Marketing brand logo as a PNG and reference it for both the listing and composer icon.
- Validate icon references, PNG dimensions and matching presentation metadata before export.

## 0.2.1

- Publish the Creative Strat plugin and Codex/Claude Code marketplaces in a dedicated public repository.
- Point installation instructions to `meds-marketing/creative-strat-plugin`.
- Retain the hosted MCP endpoint, Google OAuth, linked identity and current workspace permission model.
- Backend protocol remains 1.2.0; this packaging update adds no permission or provider capability.

## 0.2.0

- Optional full-document script review with pending suggestions and explicit direct updates.
- Preserve proposals on revision conflicts and reconcile uncertain saves with the original command/key.
- Tools-only clients complete the same workflows in chat; inline rendering depends on host support.

## 0.1.0

- Creative Strat workflow skill, client setup and optional production overview.
