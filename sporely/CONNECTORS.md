# Connectors

## Bundled: Sporely (optional)

The plugin bundles the Sporely connector (`https://sporely.io/mcp`). It is read-only and needs a Sporely account. Only the `sporely-board` skill uses it. The other three skills work without a Sporely account.

## Not bundled: HubSpot

`event-roi`, `deal-source-audit` and `pipeline-by-source` read deals, contacts and lists from HubSpot. Connect HubSpot's own connector in Claude (Settings, then Connectors). If no HubSpot connector is available, each skill falls back to CSV exports and tells you which export to make.
