# Daily Check-In

## Trigger
"Daily check-in", "morning briefing", "tell me everything I need to know", "what's my day look like", "catch me up", or similar.

## Steps

1. **Read dashboards**
   - Read `personal/active.md` — note all priorities and open items
   - Read `business/active.md` — note all priorities, ongoing work, and open items

2. **Check log for open items**
   - Read the current month's `log/YYYY-MM.csv`
   - Filter for `status = open` or `status = in-progress`
   - Note any high-priority items that need attention today

3. **Check recurring commitments**
   - Read `reference/recurring.md`
   - Identify anything due today or this week
   - Flag upcoming deadlines

4. **Check calendar** (when Google Calendar is available)
   - Pull today's events
   - Note meeting times, participants, and any prep needed
   - Cross-reference with `people/people.csv` for context on attendees

5. **Scan email** (when Gmail is available)
   - Check for urgent or time-sensitive messages since yesterday
   - Do not summarize every email — only flag what needs action

6. **Synthesize briefing**
   - Lead with the most important/urgent items
   - Group by: "Must do today", "Should address this week", "On your radar"
   - If the user shared ideas or context before triggering, weave those in
   - Keep it concise — this is a briefing, not a novel

## Inputs
- `personal/active.md`
- `business/active.md`
- `log/YYYY-MM.csv` (current month)
- `reference/recurring.md`
- Google Calendar (if available)
- Gmail (if available)

## Outputs
- Verbal/written briefing to the user
- No files are modified during check-in (unless the user asks to update something)

## Notes
- If the user hasn't filled in their active.md files yet, nudge them to do so — the check-in is only as good as the data.
- If workload looks overwhelming (5+ high-priority open items), proactively flag it and suggest prioritization.
- Tone should be direct and useful — like a trusted chief of staff giving you the morning brief.
