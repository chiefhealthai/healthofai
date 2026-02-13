# Update Contacts

## Trigger
"Update contacts", or automatically triggered after processing any meeting, email, or interaction.

## Steps

1. **Identify people to update**
   - From the interaction just processed (meeting, email, chat), list all people mentioned
   - Check if each person already exists in `people/people.csv`

2. **Update existing contacts**
   - For each known person:
     - Update `last_contact` to today's date
     - Update `notes` with a compact summary of the latest interaction (replace, don't append — keep it 1-2 sentences)
     - Update `next_action` if a new action was identified
     - Update `org`, `role`, or other fields if new information was learned

3. **Add new contacts**
   - For each person not already in `people.csv`:
     - Add a new row with all known fields
     - Set `last_contact` to today
     - Set `relationship` and `category` based on context
     - Leave unknown fields empty rather than guessing

4. **Log the interaction**
   - Add a row to `people/interactions/YYYY-MM.csv`
   - Include all people involved (comma-separated in the `people` column)
   - Write a concise summary (1-3 sentences)
   - List action items (semicolon-separated if multiple)

5. **Create reference file if warranted**
   - For key contacts who come up frequently, consider creating a file in `people/reference/` (e.g., `john-smith.md`)
   - Include: background, relationship history, key projects, preferences, communication style
   - Only do this for important recurring contacts, not everyone

## Inputs
- Context from the interaction just processed
- `people/people.csv`
- `people/interactions/YYYY-MM.csv`

## Outputs
- Updated rows in `people/people.csv`
- New row(s) in `people/interactions/YYYY-MM.csv`
- Optional: new reference file in `people/reference/`

## Notes
- **Keep notes compact.** The notes field in people.csv is for a current snapshot, not a running history. That's what the interactions CSV is for.
- **Names must be consistent.** Always use the same spelling/format as existing entries in people.csv. Check before adding a new row — they might already be there under a slightly different name.
- This behavior often runs automatically after process-meeting or process-inbox. It doesn't always need to be triggered explicitly.
