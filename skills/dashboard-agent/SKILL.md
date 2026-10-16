---
name: dashboard-agent
description: Builds live dashboards for any accelerator, incubator, buildathon, hackathon or innovation program, covering every part of the program in one place — overview, plan and approvals, sourcing funnel, selection and scores, cohort and per-startup pages, KPIs, mentors and sessions, workshops and feedback, meetings and actions, partners and leads, risks. Pulls live from Airtable and other connected tools, shows where every number comes from and how fresh it is. Use for "build the program dashboard", "live dashboard", "show me everything on one page", "startup scorecard page", "KPI dashboard", "EIR tracking dashboard", "steering committee dashboard", or "add a panel for…".
---

# Dashboard Agent

One live page per program that shows everything, with every number traceable to its source and a clear sign of how fresh it is.

Load `references/program-profile.md` (tools, key tables, KPIs, cadence, brand) and `references/dashboard-catalog.md` (panels and metrics by area). Before writing the page, load the `artifact-design` and `dataviz` skills, and `artifact-capabilities` for anything live.

## 1. Settle scope and audience

Ask, or infer from the request:
- **Audience:** program team (everything), client or steering committee (outcomes, approvals, risks; no sensitive notes), mentors (their teams only), founders (their own page only).
- **Areas:** default to all areas in the catalog that have data. "Every detail" means an overview plus a tab per area plus a page per participant, not one crowded screen.

Audience decides what's allowed on the page: founder feedback about mentors, interview notes, revenue and valuation figures, and security-sensitive details stay off anything shared beyond the program team unless the user says otherwise.

## 2. Map the data before designing

1. Find every source: the database (via airtable-agent's read sequence, using the profile's "Key tables"), the plan or mastersheet, meeting tools (Fireflies), documents.
2. For each catalog metric, record source table and field, or mark it "no data yet". Never fill a panel with sample numbers; show an empty state that says which field to fill.
3. Check data quality the way the tests did: which table is live when several fit, test or dummy records to exclude, empty fields (e.g. source channel), stale trackers. Put these in a "Data health" panel instead of hiding them.

Show the user the panel list with the source for each, and the gaps, before building.

## 3. Choose live or snapshot

- **Artifact type first:** if the session lists a Dashboard artifact type, build from it and follow its instructions.
- **Live (default for the program team):** a hand-built page that reads the viewer's own connectors at view time (the `mcp` capability, e.g. Airtable list/search tools), refreshing on open and on a sensible interval. Each viewer sees only what their own Airtable access allows, and the page can't be shared publicly. Learn tool arguments and result shapes from this session's tool schemas and one safe read; never guess them.
- **Snapshot (for clients, mentors or anyone without Airtable access):** Claude reads the data and writes it into the page's own database (`db`), with a visible "data as of" time. Offer a scheduled task to refresh it daily or weekly.
- A team dashboard can combine both: live for internal tabs, snapshot for the client view.

## 4. Build

- Overview first: 4–6 headline numbers with targets and direction, status of the current phase, next milestones and approvals, top risks.
- One tab per area from the catalog; one page per participant (profile, scores, KPIs vs baseline, mentor and sessions, actions, latest notes the audience may see).
- Every number shows its source (table/field or file) on hover or in a footnote, and every panel shows its last refresh time.
- Filters that matter: phase, sector, mentor, status. Remember a viewer's last tab or filter in browser storage only.
- Use the program brand from the profile; follow the dataviz skill for charts. Accessible in light and dark.
- Read-only by default. If the user wants edits from the page (e.g. tick an action done), each write is explicit, confirmed in the page, and limited to the fields named.

## 5. Check before handing over

- Compare 3–5 numbers on the page with a direct read of the source; they must match.
- Confirm test records are excluded and empty states say what's missing.
- Open each tab; check nothing overflows on a phone-width screen.
- Say in one line what was verified, which panels are waiting for data, and whether the page is live or a snapshot (and when it was taken).

## Rules

- No fabricated or sample data on a real program's dashboard, ever.
- No sensitive data on pages shared outside the program team without the user's explicit OK.
- Writes to the database only through airtable-agent's confirmation rules.
- Stale or contradictory data is shown as a data-health warning, not reported as fact.

## Output

A published dashboard page, a one-line summary of what it covers, the list of panels waiting for data, and an offer to schedule refreshes if it's a snapshot.
