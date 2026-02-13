# Process Meeting

## Trigger
"Process meeting", "I just had a meeting with [person]", "process my [meeting name] meeting", or similar.

## Steps

1. **Identify the meeting**
   - Check Google Calendar for the meeting details (when available)
   - Ask the user if unclear: who was it with? What was it about?

2. **Find the transcript**
   - Search Google Drive for meeting recordings or transcripts (when available)
   - Search Notion for meeting notes (when available)
   - If no transcript is available, ask the user to summarize or paste notes

3. **Extract structured information**
   - **Tasks**: Action items with owners and deadlines if mentioned
   - **Decisions**: What was decided
   - **Ideas**: Ideas that came up worth capturing
   - **Follow-ups**: Things to circle back on later
   - **Key information**: Important facts, updates, or context shared

4. **Update log CSV**
   - Append rows to `log/YYYY-MM.csv` for each extracted item
   - Set `source` to `meeting`
   - Set `type` appropriately (task, decision, idea, note, followup)
   - Set `status` to `open` for tasks/followups, `done` for decisions/notes
   - Set `priority` based on urgency/importance discussed

5. **Update active dashboard**
   - Add new tasks/priorities to the relevant `active.md` (personal or business)
   - If a task is significant enough, create a detail `.md` file and reference it

6. **Update people records**
   - For each person in the meeting:
     - Update `people/people.csv`: set `last_contact` to today, update `notes` with compact summary, set `next_action` if applicable
     - If the person is new, add a row to `people.csv`
   - Add a row to `people/interactions/YYYY-MM.csv` with the meeting summary

7. **Create detail file if warranted**
   - If the meeting produced enough content for a standalone document (project plan, proposal notes, complex decision), create a `.md` file in `personal/` or `business/`
   - Reference the file from `active.md`

## Inputs
- Google Calendar (if available)
- Google Drive / Notion transcripts (if available)
- User-provided notes or summary
- `people/people.csv` (to check for existing contacts)
- `log/YYYY-MM.csv` (to append)
- Relevant `active.md`

## Outputs
- New rows in `log/YYYY-MM.csv`
- Updated `active.md` (personal or business)
- Updated `people/people.csv`
- New row(s) in `people/interactions/YYYY-MM.csv`
- Optional: new detail `.md` file

## Notes
- Always confirm extracted items with the user before writing to files: "Here's what I extracted — anything to add or correct?"
- If multiple people were in the meeting, create one interaction row with all names comma-separated.
- Keep interaction summaries concise — 1-3 sentences max.
