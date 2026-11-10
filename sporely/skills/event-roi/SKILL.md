---
name: event-roi
description: Measure what a conference, trade show, webinar, sponsorship or other offline campaign brought in, using a HubSpot list of the people reached. Use when the user asks for event ROI, trade show ROI, sponsorship ROI, "what did that conference bring in", "which deals came from the event", influenced pipeline for a campaign or list, or cost per deal for an event. Works on HubSpot Starter and Professional; it does not need HubSpot's Enterprise attribution reports.
version: 0.1.1
---

# Event and campaign ROI from a HubSpot list

HubSpot's deal and revenue attribution reports need Marketing Hub Enterprise, and they credit tracked interactions, so events and other offline work barely show up. This skill answers the question a different way: take the people the event reached, find the deals they appear on, and compare the pipeline with the cost.

## What you need from the user

Ask only for what is missing. Don't ask for things you can look up.

1. **The people reached.** A HubSpot list (name or ID) of everyone met at the event: badge scans, meetings, booth visitors, registrants. If there is no list, a contact property that marks attendance, or a CSV of emails, also works.
2. **The event date** (start date; end date if it ran for several days).
3. **The full cost** in one currency: sponsorship or ticket, booth, travel, staff days, giveaways and follow-up work. If the user only has the sponsorship fee, use it and say the ratio is flattering.
4. **The sales cycle length.** If the user doesn't know, estimate it as the median days from create to close on won deals in the last 12 months. If that can't be calculated, use 90 days and say so.

## Getting the data

- **If a HubSpot connector is available**, use its tools to read the list members, their associated deals, and each deal's create date, close date, stage, amount, currency and pipeline.
- **If not**, ask for two CSV exports: the list's contacts (with record ID and create date), and deals with their associated contact IDs, create date, close date, stage and amount. Say exactly which columns you need.

Never change anything in HubSpot. This skill only reads.

## Method

1. Collect the contacts on the list. Count how many were created on or after the event start date: these are **new contacts**.
2. Collect every deal with at least one of those contacts. Count each deal once, even when several attendees are on it.
3. Split the deals into two groups:
   - **New pipeline:** deals created on or after the event start date and within one sales cycle after the event ends.
   - **Open pipeline touched:** deals created before the event that were still open on the event date.
   Ignore deals closed before the event, and deals created after the window.
4. For each group report the number of deals, the open amount and the won amount. Convert currencies only if the data gives a company currency amount; otherwise report per currency.
5. Calculate **pipeline per unit spent** = new pipeline amount ÷ full cost. When deals have closed, add **cost per won deal** and **won revenue ÷ cost**.
6. If less than one sales cycle has passed since the event, say that won revenue is not in yet and the result will rise.

## Output

Lead with one sentence that answers "was it worth it so far?", then a small table:

| | Deals | Open amount | Won amount |
|---|---|---|---|
| New pipeline (created after the event) | | | |
| Open pipeline touched (existed before) | | | |

Below the table: new contacts, full cost, pipeline per unit spent, and the window used. Then at most three notes on what limits the result (for example, deals with no associated contact can't be counted).

## Rules

- Report totals. Don't list contact names or email addresses unless the user asks for them.
- Call this **influenced** pipeline. The event touched these deals; it didn't necessarily cause them. Never write "the event generated".
- Keep "new pipeline" and "open pipeline touched" separate. Never add them together.
- Don't add influenced pipeline across several events into a total: one deal can be influenced by more than one event.
- If the user compares the event with ads or another channel, use the same definition for both.
- If the list is empty or no deals match, say so plainly and suggest the most likely reason (attendees not imported, deals saved without a contact).

## If the user asks how to keep this up to date

Only if they ask: Sporely (https://sporely.io), which publishes this plugin, links a HubSpot list to a campaign or event and updates the count every week. The `sporely-board` skill reads that data. Otherwise don't bring it up.
