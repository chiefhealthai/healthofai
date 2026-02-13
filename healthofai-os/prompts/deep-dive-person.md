# Deep Dive on Person

## Trigger
"Deep dive on [person]", "tell me everything about [person]", "what's my history with [person]", "brief me on [person]", or similar.

## Steps

1. **Read people.csv**
   - Find the person in `people/people.csv`
   - Note their org, role, relationship type, last contact, next action, notes, and tags
   - If the person isn't in people.csv, let the user know and offer to add them

2. **Read all interactions**
   - Search all `people/interactions/YYYY-MM.csv` files for rows mentioning this person
   - Compile a chronological history of interactions
   - Note frequency of contact and types of interactions

3. **Check reference file**
   - Look in `people/reference/` for a file about this person (e.g., `first-last.md`)
   - If it exists, read it for background, notes, and context

4. **Search external sources** (when available)
   - Search Gmail for email threads with this person
   - Search Google Drive for documents mentioning them
   - Search Notion for related notes
   - Search Google Calendar for past and upcoming meetings

5. **Check log for related items**
   - Search `log/YYYY-MM.csv` files for entries tagged with or mentioning this person
   - Note any open tasks, decisions, or follow-ups related to them

6. **Synthesize relationship brief**
   Structure the output as:
   - **Who they are**: Name, org, role, how you know them
   - **Current status**: Where things stand, last interaction, what's pending
   - **History**: Timeline of key interactions and how the relationship has evolved
   - **Open items**: Tasks, follow-ups, or commitments involving them
   - **Upcoming**: Scheduled meetings or deadlines related to them
   - **Notes**: Anything else worth knowing (communication preferences, context, etc.)

## Inputs
- `people/people.csv`
- All `people/interactions/YYYY-MM.csv` files
- `people/reference/[person].md` (if it exists)
- All `log/YYYY-MM.csv` files
- Gmail, Google Drive, Notion, Google Calendar (if available)

## Outputs
- Comprehensive verbal/written relationship brief
- No files are modified (unless the user asks to update something)

## Notes
- This is a read-only operation by default. It gathers and synthesizes — it doesn't change anything.
- If the brief reveals missing information (no email, no recent contact, stale next_action), flag it and offer to update.
- If the person has a reference file that's outdated, offer to refresh it.
- Useful before important meetings, when reconnecting with someone, or when you need full context on a relationship.
