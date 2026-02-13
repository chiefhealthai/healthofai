# Plan Task

## Trigger
"Plan [task]", "let's work on [task]", "break down [task]", "help me think through [task]", or similar.

## Steps

1. **Identify the task**
   - Clarify what the user wants to plan if not obvious
   - Check `active.md` files for existing context on this task
   - Check `log/YYYY-MM.csv` for related entries

2. **Find or create a detail file**
   - Search `personal/` and `business/` for an existing `.md` file related to this task
   - If none exists, create one with a descriptive filename (e.g., `website-redesign.md`, `q2-hiring-plan.md`)
   - Place it in `personal/` or `business/` based on the task category

3. **Gather context**
   - Read any existing detail file content
   - Check related log entries for previous decisions, notes, ideas
   - Check `people/people.csv` for relevant contacts
   - Ask the user for any additional context needed

4. **Break down the task**
   - Define the outcome: what does "done" look like?
   - List the major steps or phases
   - Identify dependencies, blockers, or unknowns
   - Estimate relative effort for each step (not time — just small/medium/large)
   - Note who else needs to be involved

5. **Write the plan**
   - Structure the detail file with:
     - **Goal**: One-sentence description of the outcome
     - **Steps**: Ordered list of what needs to happen
     - **Open questions**: Things to figure out
     - **Dependencies**: What's blocking or needed
     - **Notes**: Context, constraints, ideas
   - Reference the detail file from `active.md`

6. **Update active dashboard**
   - Add or update the task entry in the relevant `active.md`
   - Include a reference to the detail file: `→ See business/website-redesign.md`

## Inputs
- User request or task description
- `personal/active.md` and `business/active.md`
- `log/YYYY-MM.csv`
- Any existing detail `.md` files
- `people/people.csv` (if people are involved)

## Outputs
- New or updated detail `.md` file in `personal/` or `business/`
- Updated `active.md` with reference to detail file
- Optional: new rows in `log/YYYY-MM.csv` for sub-tasks

## Notes
- The goal is to make the task actionable, not to over-plan. A good plan fits on one screen.
- If the task is simple enough that it doesn't need a detail file, just update active.md directly.
- For tasks that live in other repos (e.g., `my-work/some-project/`), the detail file can reference that location.
