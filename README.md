# Health of AI — A Local-First Operating System for Work and Life

## What It Is

A folder of structured files that any AI can read. Your priorities, logs, contacts, and workflows live in flat files — markdown and CSV — on your local filesystem, backed up to GitHub.

AI reads them at the start of every session and picks up exactly where you left off. No re-explaining. No lost context. No SaaS dependency for managing your life.

The system compounds as data accumulates. Every meeting processed, every email triaged, every decision logged makes the next AI session smarter than the last.

## Why It Works

AI tools today lose context between sessions. Chat history gets buried. Memory features are shallow. You end up re-explaining your situation every time you start a new conversation.

This system solves that by giving AI structured, persistent files to read every time. The files are the memory. The AI is the interface.

The result: AI that knows your full picture on demand — your deadlines, your relationships, your priorities, your history — and can give you real, actionable guidance instead of generic advice.

## The Before and After

**Without this system:** You open an AI chat and say "what should I work on today?" The AI says something vague like "check your calendar and prioritize your tasks." Not super useful.

**With this system:** You say "daily check-in" and the AI reads your active dashboards, scans your log for open items, checks your calendar, reviews your email, and gives you a prioritized briefing: "You have a client call at 2pm — here's what you discussed last time and what you need to follow up on. Your proposal deadline is Friday and it's not started yet. Your partner's birthday is tomorrow and you haven't made a reservation."

That's the difference between AI as a toy and AI as infrastructure.

## How to Use It

**Option 1: Clone and customize**
```bash
git clone https://github.com/YOUR-USERNAME/healthofai.git
```
Then fill in your priorities, contacts, and recurring commitments.

**Option 2: Build fresh**
Use the build prompt to generate the entire system from scratch, customized to your setup.

For daily use, see `healthofai-os/WORKFLOW.md`.
For how AI operates within the system, see `healthofai-os/CLAUDE.md`.

## Folder Structure

```
healthofai/
├── README.md              ← You are here
├── CLAUDE.md              ← AI entry point — routes to the OS
├── healthofai-os/         ← The operating system
│   ├── CLAUDE.md          ← AI brain — all behaviors defined here
│   ├── WORKFLOW.md        ← Your daily playbook
│   ├── CHANGELOG.md       ← Version history
│   ├── prompts/           ← Detailed workflow instructions for AI
│   ├── log/               ← Monthly CSV logs of tasks, ideas, decisions
│   ├── people/            ← Contacts, interactions, relationship data
│   ├── personal/          ← Personal priorities and active dashboard
│   ├── business/          ← Business priorities and active dashboard
│   └── reference/         ← Tools, setup, recurring commitments
├── my-work/               ← Your work and business projects
└── my-projects/           ← Your personal projects
```

- **healthofai-os/** — The operating system. Manages priorities, logs, contacts, and workflows across everything in this workspace.
- **my-work/** — Where your work and business projects live. Clone repos, create folders, whatever you need. The OS tracks priorities across all of them.
- **my-projects/** — Where your personal projects live. Side projects, courses, hobbies. Same deal — the OS sees across everything.

## Who Made This

Built by [Chief Health AI](https://chiefhealthai.com). Born from a system called iRD-OS, built in a single day and battle-tested immediately.

Open-sourced because we believe the health of your AI starts with giving it structured context. If your AI doesn't know your priorities, your relationships, and your commitments, it can't actually help you. This system fixes that.
