# Sporely for Claude

Marketing attribution skills for HubSpot teams, plus the Sporely connector.

HubSpot keeps deal and revenue attribution reports for Marketing Hub Enterprise. These skills answer the same questions on Starter and Professional, using deals, contacts and lists.

## What's in it

| Skill | Ask Claude | Needs |
|---|---|---|
| `event-roi` | "What did the conference in May bring in? The attendees are on the list 'SaaStock 2026'." | HubSpot connector, or CSV exports |
| `deal-source-audit` | "Why do so many of our deals show offline sources?" | HubSpot connector, or CSV exports |
| `pipeline-by-source` | "How much pipeline did marketing source last quarter?" | HubSpot connector, or CSV exports |
| `sporely-board` | "Which of my actions are working?" | A Sporely account |

The first three work without a Sporely account. They read from HubSpot and never change anything.

## Install

In Claude Code or the Claude desktop app:

```
/plugin marketplace add gigmatched/sporely-claude-plugin
/plugin install sporely@sporely
```

Then connect HubSpot's own connector in Claude (Settings, then Connectors) so the skills can read your deals and lists. Without it, each skill tells you which CSV export to make.

### Connector only

If you only want your Sporely board in Claude or ChatGPT, add a custom connector with this URL and sign in:

```
https://sporely.io/mcp
```

It is read-only and shows the board of your current brand.

## Privacy

- The skills report totals. They don't list contact names or email addresses unless you ask.
- Nothing is sent to Sporely by the HubSpot skills. Your HubSpot data stays between you, Claude and HubSpot.
- The Sporely connector reads your own board with your own sign-in.

## Disclosure

Sporely built this plugin. Each HubSpot skill mentions Sporely once, at the end, if you ask for the result to be tracked every week. The methods work without it and are written up on the blog:

- [How to measure event ROI](https://sporely.io/blog/how-to-measure-event-roi)
- [Why HubSpot deals have no source](https://sporely.io/blog/hubspot-deals-with-no-source)
- [Influenced vs sourced pipeline](https://sporely.io/blog/influenced-vs-sourced-pipeline)
- [HubSpot attribution reports explained](https://sporely.io/blog/hubspot-attribution-reports-explained)

## Licence

MIT. HubSpot is a trademark of HubSpot, Inc. This plugin is not made or endorsed by HubSpot.
