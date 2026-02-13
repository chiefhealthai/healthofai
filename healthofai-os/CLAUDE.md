# Health of AI OS — Operating System Brain

## Project Overview

Health of AI OS is a local-first operating system that uses structured flat files (markdown + CSV), git for version control and backup, and AI as the dynamic interface. Through this system, you manage your work, projects, contacts, and life — all from a single repository of plain files that any AI can read.

The system compounds over time. Every meeting processed, every email triaged, every decision logged makes the data richer and the AI more useful.

## Environment Awareness

This system may be accessed from different AI environments. Adapt behavior accordingly:

- **Claude Code (terminal)** — Focus on file operations, git, building, and direct filesystem manipulation. Full access to read and write all files. Use this for hands-on work.
- **Claude Cowork (browser)** — Leverage connected services: Google Calendar, Gmail, Google Drive, Notion, and other MCP integrations. Use this for richer context gathering — checking calendar, scanning email, pulling meeting transcripts.
- **Claude Chat (conversation)** — Strategic conversation, planning, brainstorming. Use this when you need to think through problems or plan approaches without needing file access.
- **Claude Code on iOS (mobile)** — Quick updates and queries from phone. See WORKFLOW.md for mobile-specific rules about session management and PR workflow.

Core behaviors remain the same regardless of environment. Update behaviors as technology evolves.

## Core Behaviors

> **Note:** The triggers listed below are examples, not exact commands. Recognize natural language variations — "what happened in my meetings today," "anything I need to deal with," "catch me up," "what's on my plate" — and map them to the appropriate behavior. When in doubt, ask the user which behavior they're looking for.

### Daily Check-In

**Triggers:** "daily check-in", "tell me everything I need to know", "what's my day look like", "morning briefing", "catch me up", or similar.

**Steps:**
1. Read `personal/active.md` and `business/active.md`
2. Check the current month's log CSV (`log/YYYY-MM.csv`) for open items
3. Check `reference/recurring.md` for upcoming deadlines
4. Check Google Calendar for today's events (when available)
5. Quick scan of Gmail for anything urgent or time-sensitive since yesterday (when available)
6. Synthesize into a prioritized briefing

If the user provides context or ideas first, incorporate those into the briefing.

**Detailed prompt:** See `prompts/daily-check-in.md`

### Process Meeting

**Triggers:** "process meeting", "I just had a meeting with [person]", "process my [meeting] meeting", or similar.

**Steps:**
1. Check Google Calendar to identify the meeting (when available)
2. Search Google Drive and Notion for transcripts (when available)
3. Extract tasks, decisions, ideas, and follow-ups
4. Append structured rows to the current month's `log/YYYY-MM.csv`
5. Update the relevant `active.md` (personal or business)
6. Update `people/people.csv` with compact latest note for each person mentioned
7. Add row(s) to `people/interactions/YYYY-MM.csv`
8. If a person is new, add them to `people/people.csv`
9. If the meeting warrants a dedicated detail file, create one in the appropriate folder and reference it from `active.md`

**Detailed prompt:** See `prompts/process-meeting.md`

### Process Inbox

**Triggers:** "process inbox", "check my email", "process today's email", or similar.

**Steps:**
1. Search Gmail for recent threads (when available)
2. Extract action items, decisions, and information
3. Append to `log/YYYY-MM.csv`
4. Update `active.md` files as needed
5. Update `people/people.csv` and `people/interactions/YYYY-MM.csv` as needed
6. Do not draft responses to emails unprompted — just extract action items and information

**Detailed prompt:** See `prompts/process-inbox.md`

### Process Chat

**Triggers:** "process this chat summary", "here's what I was thinking about", "process chat", or similar.

**Steps:**
1. Parse the provided summary for tasks, ideas, decisions
2. Append to `log/YYYY-MM.csv`
3. Update `active.md` files
4. Create detail `.md` files if warranted

**Detailed prompt:** See `prompts/process-chat.md`

### What's Next

**Triggers:** "what's next", "what should I do", "what's the priority", or similar.

**Steps:**
1. Read both `active.md` files
2. Check `log/YYYY-MM.csv` for open high-priority items
3. Check calendar for upcoming commitments (when available)
4. Recommend 1-3 highest-impact actions
5. Do not overwhelm — if there are more than 5 high-priority open items, flag that the plate is full

### Weekly Review

**Triggers:** "weekly review", "week in review", or similar.

**Steps:**
1. Read the full week's log entries
2. Read both `active.md` files
3. Read the week's interactions
4. Synthesize: what got done, what slipped, what's coming next week
5. Archive completed items from `active.md`
6. If end of month, snapshot `active.md` to `archive/`

**Detailed prompt:** See `prompts/weekly-review.md`

### Update Contacts

**Triggers:** "update contacts", or automatically after any interaction processing.

**Steps:**
1. Update `people/people.csv` — keep the notes column compact (latest summary, not appending)
2. Add interaction row to `people/interactions/YYYY-MM.csv`

**Detailed prompt:** See `prompts/update-contacts.md`

### Deep Dive on Person

**Triggers:** "deep dive on [person]", "tell me everything about [person]", "what's my history with [person]", or similar.

**Steps:**
1. Read `people/people.csv` for their metadata
2. Read all interaction rows mentioning them
3. Check `people/reference/` for their file
4. If available, search Gmail and Google Drive for additional context
5. Synthesize a comprehensive relationship brief

**Detailed prompt:** See `prompts/deep-dive-person.md`

### Plan Task

**Triggers:** "plan [task]", "let's work on [task]", "break down [task]", or similar.

**Steps:**
1. Check if there's a detail `.md` file for that task
2. If not, create one in the appropriate folder (`personal/` or `business/`)
3. Read relevant context from `active.md` and log
4. Help plan the approach, break it down, and optionally draft within the detail file

**Detailed prompt:** See `prompts/plan-task.md`

## File Conventions

- **Log CSV:** One file per month (`YYYY-MM.csv`). Columns defined in `log/schema.md`. Always append, never overwrite existing rows.
- **People CSV:** Single file (`people/people.csv`). Update in place. Keep notes column to 1-2 sentences max.
- **Interactions CSV:** One file per month (`people/interactions/YYYY-MM.csv`). Always append.
- **active.md:** Living document. Update in place. Completed items move to the "## Completed" section, then get swept to archive periodically.
- **Detail .md files:** Created in `personal/` or `business/` for tasks that need more space. Referenced from `active.md`.
- **All dates in ISO format** (YYYY-MM-DD).
- **When creating new monthly files**, copy the header row from the schema.

## Pacing and Wellbeing

This system should keep the user productive but not overwhelmed. When workload is high, proactively suggest prioritization, delegation, or deferral. Don't just pile on tasks — help stay strategic.

If there are more open items than one person can realistically handle, say so. Recommend what to defer or delegate. The goal is sustainable productivity, not burnout.

## Git Workflow

After significant updates (morning check-in, meeting processing, end-of-day), remind the user to commit and push. Offer to help with git operations.

Suggested commit messages follow the pattern:
- `daily: Morning check-in YYYY-MM-DD`
- `meeting: Process [meeting name]`
- `inbox: Process email YYYY-MM-DD`
- `review: Weekly review YYYY-MM-DD`
- `update: [description of what changed]`

## Cross-Folder Awareness

Health of AI OS sits alongside other folders in this workspace:
- `my-work/` — Work and business projects
- `my-projects/` — Personal projects

When tasks reference other projects (e.g., folders in `my-work/` or `my-projects/`), note the connection but don't modify other repos unless explicitly asked. `active.md` can reference tasks that live in other folders using relative paths.
