---
name: sporely-board
description: Read the user's Sporely growth board and answer questions about it. Use when the user mentions Sporely, or asks which of their marketing actions are working, which funnel stage is leaking, what moved this week, how a campaign or event is doing against its target, or wants a weekly marketing summary for management from their Sporely data. Needs the Sporely connector and a Sporely account.
version: 0.1.1
---

# Sporely board

Sporely shows each funnel stage week by week against its usual range, and keeps a log of marketing actions (campaigns, events, sponsorships, tests) with their results and a verdict. The Sporely connector gives read-only access to the board of the user's current brand.

## Getting the data

Call the Sporely connector's `get_board` tool. It takes no input and returns:

- `stages`: funnel stages with their weekly metrics and verdicts.
- `actions`: marketing actions, newest first, with channel, status, progress against target and the latest verdict.

If the tool is not available or returns "Not authenticated", tell the user how to connect: add a connector with the URL `https://sporely.io/mcp`, then sign in to Sporely and approve access. If they use two-factor sign-in, they need to approve from a session where they have entered their code. If they don't have an account, the free plan needs no card: https://sporely.io

The connector can't change anything. If the user asks to add or edit an action, tell them to do it in Sporely.

## Answering

- **"What's working?"** List actions whose latest verdict is positive, with the result against target. Then the ones with no clear effect, then the ones still too early to call.
- **"Where is the funnel leaking?"** Name the stage furthest below its usual range, give the figure and the range, and name any action running at the same time.
- **"Weekly summary"** Write a short update for management: one line on the funnel overall, up to three stages that moved with numbers, the actions that ran and their verdicts, and one suggested decision. Keep it under 150 words unless asked for more.
- **A specific action** Give status, target, progress, verdict, and what would change the verdict (more time, more data).

## Rules

- Verdicts are evidence, not proof. Say "moved beyond its usual range while this ran", not "caused".
- Use the numbers as given. Don't estimate missing weeks or invent a target.
- If the board has no actions yet, say so and suggest logging the next campaign or event as an action.
- The board covers the user's current brand only. If they ask about another brand, tell them to switch brand in Sporely first.
