# Health of AI OS — Your Daily Playbook

> **Rule #1: If you've been talking to any AI for more than 5 minutes about something that matters, summarize it before you close the chat. Paste the summary into your AI and say "process this chat summary." This is the one discipline the system requires from you.**

## Which AI Tool to Use

- **Claude Cowork** — Your chief of staff. Use for morning check-ins, processing meetings (it can access Calendar, Gmail, Drive, Notion), "what's next?" flow, strategic thinking, and any task that needs to reach outside your filesystem.
- **Claude Code** — Your builder. Use for editing files, updating active.md and CSVs, creating new detail files, git commits, coding, and anything hands-on in the terminal.
- **Either works** for most tasks. In practice, open both and use whichever fits the moment. The CLAUDE.md teaches both how to operate in this system.

## Morning Routine (5-10 min)

1. Open Claude Cowork at the `healthofai/` top-level folder for cross-project access
2. Optional: share any ideas or thoughts you woke up with
3. Say: "Daily check-in"
4. Review the briefing. Adjust priorities if needed.
5. Pick your first task.

## After Each Meeting

1. Make sure the transcript is captured (Gemini, Notion, or other tool)
2. Tell Claude: "Process my [meeting name/person] meeting"
3. Quick 30-second review of what was extracted
4. Approve or correct

## Throughout the Day

- Spin up Claude Cowork or Claude Code sessions for individual tasks
- When switching contexts, quickly tell the system what happened: "I finished X" or "I made progress on Y, here's where it stands"
- Use "what's next?" whenever you need direction

## End of Day (5 min)

1. "Process today's inbox" — Claude scans email
2. "End of day update" — Claude summarizes what moved
3. Commit and push to GitHub

## Weekly Review (Friday, 15 min)

1. "Weekly review" — Claude synthesizes the week
2. Review the synthesis, adjust priorities for next week
3. Archive completed items

## Git Hygiene

- Commit after morning check-in
- Commit after processing meetings
- Commit at end of day
- Push to GitHub at least once daily

## Mobile Workflow (Claude Code iOS)

When you're away from your computer, you can update and query Health of AI OS from your phone using Claude Code on iOS.

### Rules

- **One session at a time.** Only have one Claude Code iOS session open. Each session creates its own branch, and multiple open sessions will create conflicting branches that are messy to untangle.
- **Stick to your session.** Use the same session for both asking questions and making updates.
- **Always merge before starting fresh.** Complete the full cycle below before opening a new session.

### The Cycle

1. Open Claude Code iOS — ask questions, review your plan, make file updates
2. When done, tap **Create PR**
3. It bounces you to GitHub in your browser
4. Tap **Merge pull request** → **Confirm merge** → **Delete branch**
5. That session is now retired. Do not go back to it. Start a fresh session next time.

### Important: Session Lifecycle

Each Claude Code iOS session clones the repo at the moment you open it. It is a snapshot in time. That session does not automatically sync with changes merged to GitHub from other sessions or from your computer.

What this means:
- An old session will have outdated files if you have merged changes elsewhere
- Going back to a stale session and making more changes creates a branch that conflicts with or duplicates work already on main
- Once you Create PR and Merge, consider that session done
- Think of each session as disposable: use it, merge it, retire it

### Syncing Back to Your Computer

When you sit down at your desk, pull down everything merged from your phone:
```bash
cd /path/to/healthofai && git pull
```
