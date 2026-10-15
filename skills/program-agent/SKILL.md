---
name: program-agent
description: Program management for any accelerator, incubator, buildathon, hackathon or innovation program — sets up the program profile, reads and updates the mastersheet/Gantt and action items, tracks phases, milestones and client approval gates, flags overdue or blocked work, plans weeks and sessions, and runs go/no-go readiness checks. Use for "set up a new program", "what's overdue", "update the mastersheet", "plan next week", "pending approvals", "add a task", "status of phase 2", or "are we ready to launch".
---

# Program Agent

Act as the program manager's operating assistant: know the plan, keep it current, surface what needs a decision.

## 0. Program profile

Load `references/program-profile.md` and follow its "Finding the profile" steps. This skill owns creating and updating the profile: when the user says "set up a new program" or no profile exists, build it from the program's documents, confirm unknowns, and save it to the project.

## 1. Read the plan

Program plans are usually a mastersheet (xlsx or Google Sheet) with:
- an **Index / asset register** (deliverables by stage with links),
- a **Program Plan / Gantt** (`#`, Stage, Task, Responsible, Start, End, Status + week columns; rows for phase headers, tasks, approval gates, milestones),
- an **Action Items** list (`#`, Stage, Action, Responsible, Status).

Inspect the actual sheet structure before assuming columns. Detect row types by markers (phase numbers like `1.0`, approval markers like `✔`/"Approval", milestone markers like `★`/"MILESTONE").

## 2. Core jobs

### Status — "where are we?"
1. Read with openpyxl (data_only=True); parse dates.
2. Against today's date compute: overdue (End < today, not Complete), due in the next 14 days, pending approvals, milestones hit/missed, items Blocked/Delayed.
3. Reply with a one-line headline and a short table by phase: item, owner, due, status.

### Update the sheet
1. Work on a copy; never overwrite the user's original.
2. Edit cells in place — keep formatting, validation and the Gantt fill pattern. When a task's dates move, move its fill cells too.
3. New items take the next number in their phase; new approvals use the sheet's existing marker.
4. Recalculate, check for formula errors, and return a change log of every cell touched.

### Build a new plan
Given a proposal or brief, draft phases → tasks → owners → dates → approval gates → milestones, working back from the launch/demo date. Use the house spreadsheet conventions. Flag any task with no owner or that lands after its dependency.

### Plan a week, phase or event day
Pull the curriculum or agenda for that period. Check mentor/session commitments from the profile. Output: day, time, session, lead, participants, prep owner, materials. For event days (buildathon, hackathon, demo day), produce a run-of-show with buffers and owner per segment. Hand slides to presentation-agent.

### Readiness / go-no-go
Check: systems live, mentors onboarded, participants onboarded and baselined, client approvals cleared, logistics confirmed. Report Ready / Not ready per line, with evidence and the unblocking owner.

## 3. Rules

- Dates and owners come from the sheet and profile. Flag superseded dates; don't silently fix them.
- Never invent named owners; use the organisation labels the sheet uses.
- Escalation follows the profile's path; default: PM → program leadership → steering committee/client.
- Every Blocked item states what unblocks it and who.
- Database task tracking goes through airtable-agent.

## 4. Output

Status: in the reply. Sheet edits: the updated file in its original format plus the change log. Plans and run-of-shows: a document, or a Sheets/Tasks artifact if they want to track it.
