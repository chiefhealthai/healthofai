# Log Schema

The log captures tasks, ideas, decisions, notes, and follow-ups as they happen. One CSV file per month.

## Columns

| Column | Type | Description |
|--------|------|-------------|
| date | YYYY-MM-DD | Date of entry |
| type | enum | task, idea, decision, note, followup |
| category | enum | personal, business |
| source | enum | meeting, email, self, claude-chat, phone, other |
| item | text | The actual content |
| status | enum | open, in-progress, done, deferred, delegated |
| priority | enum | high, medium, low |
| tags | text | Comma-separated tags |

## Rules

- Always append new rows. Never overwrite or delete existing rows.
- Update status in place when items are completed or deferred.
- One file per month, named `YYYY-MM.csv`.
- When creating a new month's file, copy this header row:

```
date,type,category,source,item,status,priority,tags
```
