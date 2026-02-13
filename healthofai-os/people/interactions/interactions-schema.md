# Interactions Schema

The interactions log captures every meaningful interaction with people. One CSV file per month, always append.

## Columns

| Column | Type | Description |
|--------|------|-------------|
| date | YYYY-MM-DD | Date of interaction |
| people | text | Comma-separated names (matching people.csv) |
| type | enum | meeting, email, call, chat, note |
| source | enum | google-drive, notion, gmail, dictated, claude-chat, other |
| summary | text | Compact summary of what happened |
| action_items | text | Extracted tasks (semicolon-separated if multiple) |
| tags | text | Comma-separated tags |

## Rules

- Always append new rows. Never overwrite or delete existing rows.
- People names must match exactly with `people.csv` for cross-referencing.
- One file per month, named `YYYY-MM.csv`.
- When creating a new month's file, copy this header row:

```
date,people,type,source,summary,action_items,tags
```
