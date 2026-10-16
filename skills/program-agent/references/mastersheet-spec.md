# Mastersheet Spec (house format)

Every new mastersheet uses `scripts/build_mastersheet.py` in this skill's folder. Don't hand-build workbooks; the script fixes the layout so every program looks like the KUEC mastersheet.

## Tabs
1. **Index**: asset register. Stage bands in navy, numbered assets (1.1, 1.2…), Link and Status columns.
2. **Program Plan**: the Gantt.
3. **Action Items**: #, Stage, Action Item, Responsible, Due, Status; overdue due dates turn red.

## Program Plan layout
- B1 program name; C2/D2 project start date; E2/F2 today's date.
- Rows 1 to 3 over the timeline: Year band, Month band (merged, alternating light blue), Week-commencing dates (Monday, rotated). Row 4 is the column header. Panes frozen at J5.
- Columns: # · Stage · Task · Responsible · Start · End · Status, then one column per week.
- Row types:
  - **Phase** (`1.0`): navy band across the whole row, white bold text.
  - **Task** (`1.1`, `1.2`…): plain row, task text wraps, row height grows with text.
  - **Approval** (`✔ APPR`): orange tag, cream row, "<Client> Approval" in Stage, "✔ <CLIENT> APPROVAL: …" in Task, status Pending or Approved.
  - **Milestone** (`★`): peach tag and "⬛ MILESTONE: …" text.
  - **Headline milestone** (last row): navy with amber text, e.g. "PROGRAM KICK-OFF: 11 January 2027".
- Timeline: light-blue bars for every week an item spans; ● on the end week; the end week turns green when Status is Complete; the current week is outlined and its header highlighted amber. All driven by conditional formatting, so editing dates or status updates the chart.
- Status dropdowns: Not Started, In Progress, Complete, Delayed, Blocked (approvals: Pending, Approved), each with its own colour.
- Legend under the plan. Print setup: A3 landscape, fit to width, header rows repeat.

## Building one
1. Draft the plan from the brief or proposal using `references/plan-library.md`, working back from kickoff. Ask the user for the kickoff date, program length, client short name, approval gates and owners if the documents don't give them. Never invent dates the user hasn't agreed; propose them and get a yes.
2. Write the plan as JSON (shape in the script's docstring), then run:
   `python3 <skill folder>/scripts/build_mastersheet.py plan.json "<Program Name> Mastersheet.xlsx"`
   File names: no dashes.
3. QA before sending:
   - Recalculate with LibreOffice and check for formula errors (zero allowed).
   - Render the Program Plan to an image and look at it: bars line up with dates, no "###", no overlapping text, months labelled, approvals and milestones styled.
   - Check every phase has at least one milestone, every client gate has an approval row, and no task ends after something that depends on it.
4. Deliver the .xlsx with a short summary: number of phases, tasks, approvals and milestones, date range, and anything still to confirm.

## Editing an existing mastersheet
Keep its format. If it was built with this spec, edit the plan JSON and rebuild, or edit cells in place; conditional formatting redraws the bars. If it's an older sheet (e.g. the original KUEC file), edit cells in place and don't restyle it unless asked.
