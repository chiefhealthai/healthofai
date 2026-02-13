# Process Chat

## Trigger
"Process this chat summary", "here's what I was thinking about", "process chat", "here's a summary from my conversation", or similar.

## Steps

1. **Receive the summary**
   - The user will paste or dictate a summary of a conversation they had (with AI, with a person, or their own thinking)
   - If no summary is provided, ask: "What were you discussing? Paste the summary or tell me the key points."

2. **Parse for structured items**
   - **Tasks**: Things to do, with owners if mentioned
   - **Ideas**: Concepts worth capturing for later
   - **Decisions**: Things that were decided or conclusions reached
   - **Notes**: Important context or information
   - **Follow-ups**: Things to revisit or circle back on

3. **Update log CSV**
   - Append rows to `log/YYYY-MM.csv`
   - Set `source` to `claude-chat` (or `phone`, `other` as appropriate)
   - Set `type` based on the content of each item
   - Set `status` to `open` for tasks/followups
   - Set `priority` based on apparent importance

4. **Update active dashboards**
   - Add significant tasks and priorities to the relevant `active.md`
   - Add ideas to the "Ideas & Thinking" section
   - If a task is complex enough, create a detail `.md` file

5. **Create detail files if warranted**
   - If the chat produced a substantial plan, analysis, or body of thinking, create a `.md` file in `personal/` or `business/`
   - Reference it from `active.md`
   - Title the file descriptively (e.g., `marketing-strategy-notes.md`, `vacation-planning.md`)

6. **Confirm with user**
   - Present what was extracted: "Here's what I captured — anything to add, correct, or remove?"
   - Make updates based on feedback

## Inputs
- User-provided chat summary or notes
- `log/YYYY-MM.csv` (to append)
- `personal/active.md` and `business/active.md` (to update)

## Outputs
- New rows in `log/YYYY-MM.csv`
- Updated `active.md` files
- Optional: new detail `.md` files in `personal/` or `business/`

## Notes
- This is the critical capture point for the system. Rule #1 from WORKFLOW.md: "If you've been talking to AI for more than 5 minutes about something that matters, summarize it before you close the chat."
- Be generous in what you capture — it's better to log something and defer it than to lose it entirely.
- If the summary mentions people, update `people/people.csv` and interactions as well.
