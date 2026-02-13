# People Schema

The people file tracks everyone you interact with professionally and personally. Single file, updated in place.

## Columns

| Column | Type | Description |
|--------|------|-------------|
| name | text | Full name |
| org | text | Organization/company |
| role | text | Their role/title |
| relationship | enum | client, partner, colleague, advisor, friend, family, prospect |
| category | enum | personal, business, both |
| email | text | Primary email |
| last_contact | YYYY-MM-DD | Date of most recent interaction |
| next_action | text | What's the next thing to do with/for this person |
| notes | text | Compact 1-2 sentence summary |
| tags | text | Comma-separated tags |

## Rules

- Keep notes to 1-2 sentences max. This is a summary, not a history.
- Update `last_contact` and `notes` after every interaction.
- `next_action` should always reflect the current next step. Clear it when done.
- Names must be consistent — use the same spelling everywhere so interactions can be matched.
