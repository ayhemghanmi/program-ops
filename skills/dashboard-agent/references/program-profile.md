# Program Profile — how every skill in this plugin finds its facts

These skills work on any program: accelerators, incubators, buildathons, hackathons, innovation challenges, bootcamps, fellowships, corporate venture programs. They never assume a specific client. Program facts come from a **program profile**.

## Finding the profile (do this first, every time)

1. Look for a file named `program-profile.md` (or a doc titled "Program Profile") in the current project, the attached files, or the folder the user points to.
2. If none exists, build one: read the program's core documents (proposal, kickoff deck, action plan, mastersheet/Gantt, curriculum, handbook) and fill the template below. Mark every field you could not find as `[unknown]`, then ask the user about the ones that matter (see step 3).
3. Show the user the filled profile in a few lines and ask them to confirm or correct the unknowns that matter for the current task. Do not block on unknowns that don't matter for it.
4. Offer to save it as `program-profile.md` in the project so the next skill run starts from it.

If the profile and a source document disagree, the profile wins unless it is older than the document; in that case flag the conflict.

## Template

```markdown
# Program Profile — [Program name]
Last updated: [date] by [name]

## Identity
- Program name / short name:
- Program type: (accelerator / incubator / buildathon / hackathon / challenge / bootcamp / fellowship / other)
- Client / sponsor:
- Operator / delivery partner:
- Target participants: (stage, sector, geography)
- Cohort size / number of teams:
- Objectives (3–5):

## Timeline
- Start / kickoff date:
- End / demo day / finals date:
- Phases (name: dates):
- Evaluation checkpoints:
- Key milestones:

## Governance
| Body / role | Who | Remit |
- Approval gates (what needs client sign-off):
- Escalation path (what the PM decides vs leadership vs steering committee):

## Reporting cadence
| Cadence | Output | Audience |

## KPIs
- Program KPIs:
- Participant KPIs:
- Targets:

## Selection / judging
- Gate criteria (pass/fail):
- Scored criteria and weights (must total 100%):
- Scale (e.g. 1–5) and anchors location:
- Later-stage assessments (due diligence, interviews, pitch judging):
- Decision outcomes (e.g. Accept / Waitlist / Reject):

## Mentors / experts
- Model (EIRs, mentors, judges, coaches):
- Session commitments and SLAs:
- Feedback loops:

## Tools
- CRM / database: (e.g. Airtable base name)
- Key tables: (purpose → exact table name, e.g. applications → "KUEC Applications"; mentors → "EIRs")
- Portal: 
- Documents:
- Comms:
- Scheduling:
- Reporting dashboard:

## Brand
- Template file:
- Colors (hex):
- Fonts:
- Logo rules:

## Status vocabulary
- e.g. Not Started / In Progress / Complete / Delayed / Blocked

## Open flags
- Unresolved conflicts between sources, each with both versions and the default in use.

## Source documents
- List with dates.
```

## House conventions (apply to every program unless the profile overrides)

- Never invent names, scores, figures, quotes or dates. When something the output needs is unknown, ask the user before finishing: group the questions (up to 4 at a time, multiple choice where the options are clear, using the question tool when available) and say why each one matters. Use a bracketed placeholder (`[Demo Day date]`) only when the user doesn't know, skips the question, or isn't there to answer (scheduled or unattended runs), and list every remaining placeholder at the end.
- Conflicts between sources are flagged with both versions and the one used — never silently resolved.
- Compute every number in code from the data; never estimate in prose.
- Leave obvious test or dummy records (e.g. "Test Company", empty rows) out of counts, and say how many were left out.
- Before reporting from a tracker or table, check it is current. If most items are past due but unchanged, or status fields are empty while other sources show activity, say the data looks stale and ask for an update rather than reporting it as fact.
- Drafting is fine; sending, posting, or writing to a live system requires the user's explicit yes in chat.
- Spreadsheets: Arial; blue font = input, black = formula/fixed, green = cross-tab link, yellow fill = key cell. Recalculate and confirm zero formula errors before delivery.
- Dates written "15 Sep 2026"; times in the program's local time zone (state it).
