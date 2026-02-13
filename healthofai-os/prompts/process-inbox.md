# Process Inbox

## Trigger
"Process inbox", "check my email", "process today's email", "anything in my email I need to deal with?", or similar.

## Steps

1. **Scan email** (requires Gmail access)
   - Search Gmail for recent threads (since last check or since yesterday)
   - Focus on unread messages and threads with new replies
   - Skip newsletters, automated notifications, and obvious spam unless they contain action items

2. **Categorize each relevant thread**
   - **Action required**: Something you need to do
   - **Decision needed**: Someone is waiting for your input
   - **Information only**: Good to know, no action needed
   - **Follow-up**: Something you're waiting on from someone else

3. **Extract structured items**
   - For each action/decision/follow-up, create a clear one-line summary
   - Note who it's from, what's needed, and any deadline mentioned

4. **Update log CSV**
   - Append rows to `log/YYYY-MM.csv`
   - Set `source` to `email`
   - Set `type` and `priority` based on content
   - Set `status` to `open` for items needing action

5. **Update active dashboards**
   - Add new tasks to the relevant `active.md` if they're significant enough
   - Don't clutter active.md with minor email tasks — the log captures everything

6. **Update people records**
   - Update `people/people.csv` for anyone with a notable interaction
   - Add interaction rows for significant email exchanges
   - Don't log every routine email — use judgment

7. **Present summary to user**
   - Group by: "Needs your action", "Needs your decision", "FYI", "Waiting on others"
   - Keep it scannable — one line per item

## Inputs
- Gmail (required for full functionality)
- `log/YYYY-MM.csv` (to append)
- `personal/active.md` and `business/active.md` (to update)
- `people/people.csv` and `people/interactions/YYYY-MM.csv` (to update)

## Outputs
- New rows in `log/YYYY-MM.csv`
- Updated `active.md` files (if significant items found)
- Updated `people/people.csv` (for notable contacts)
- New rows in `people/interactions/YYYY-MM.csv` (for significant exchanges)
- Verbal summary to user

## Notes
- **Do not draft email responses unprompted.** Only extract information and action items. If the user wants help drafting a response, they'll ask.
- If Gmail is not available (e.g., in Claude Code without MCP), tell the user and suggest they use Claude Cowork or manually paste email summaries.
- Be selective — not every email needs to become a log entry. Focus on items that are actionable or important.
