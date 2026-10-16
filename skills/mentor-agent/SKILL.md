---
name: mentor-agent
description: Manages mentors, EIRs, coaches and judges for any program — sourcing and longlists, interview scoring, mentor–participant matching with written rationale, onboarding packs and engagement agreements, session tracking against service-level commitments, and satisfaction-trend alerts. Use for "build the mentor longlist", "match EIRs to startups", "why this match", "onboarding pack for mentors", "are mentors hitting their sessions", "who's behind on SLA", "mentor satisfaction trend", or "replace a mentor".
---

# Mentor Agent

This skill sources mentors, EIRs, coaches and judges. Sourcing startups or applicants belongs to sourcing-agent.

Get the right expert in front of each team, keep the engagement on track, and catch problems early.

Load `references/program-profile.md` (mentor model, commitments, SLAs, feedback loops, tools) and `references/mentor-framework.md`.

## 1. Sourcing and longlist

- Start from the cohort's needs: sectors, stages, top growth gaps (from diagnostics or applications).
- Gather candidates from sources the user names (their network lists, past programs' rosters, the database, LinkedIn profiles they share). Don't scrape or compile personal information beyond professional profile basics.
- Longlist table: name, current role, sectors, expertise tags, stage experience, geography, availability, source, gaps covered. Aim for ~1.5–2× the number of mentors needed.
- Flag coverage gaps: needs with no matching candidate.

## 2. Interview and scoring

Use the mentor rubric from scoring-agent's library (expertise, coaching style & empathy, track record, communication, availability) unless the program has its own. Score from interview notes only, one evidence line per score. Rank and propose a shortlist, labelled "suggested" for the client/committee to approve.

## 3. Matching

1. Build a matrix: participants × mentors, scoring fit on the factors in `references/mentor-framework.md`.
2. Propose primary matches (and a backup per participant). Respect capacity limits per mentor.
3. Write a 2–3 sentence rationale per match: the participant's top need, the mentor's relevant experience, the risk to watch.
4. Flag conflicts of interest (competing ventures, investments, employer overlap) for a human decision.
5. Guard against breadth bias: a profile that ticks every expertise box should not win by default. Weight evidence (track record, companies built, notable achievements) over self-selected tags, cap tag credit at the participant's top needs, and enforce each mentor's capacity (preferred number of startups) so one generalist isn't matched to everyone.
6. Say which matching factors could not be scored from the available data, and treat the result as a shortlist for a human decision, not a final match.
7. If the database shows no matches or empty statuses while calls show matching under way, flag the records as stale before tracking against them.
8. Recommend intro/chemistry sessions before confirming.

## 4. Onboarding pack

Assemble from the program's own documents. Ask the user for anything missing (session cadence, SLA, dates); use bracketed placeholders only for what they can't answer yet:
- Role definition and boundaries; session cadence and minimum commitment; response-time SLA
- Program calendar and key milestones; participant profiles for their matches
- First-session agenda and diagnostic; how to log sessions and actions; escalation path
- Engagement agreement / SLA summary for signature (drafted only — signing and sending stay with the team)

## 5. Session tracking against commitments

Pull the session log (Airtable via airtable-agent, or the tracker sheet). Compute in code, per mentor and per match, for the period:
- Sessions delivered vs required (e.g. min N per month)
- Days since last session; next session booked or not
- Response-time SLA breaches if timestamps exist
- Actions logged per session (empty logs are a quality flag)

Status per match: On track / At risk (one short, or no session booked within the window) / Off track (two+ short or SLA breached).

## 6. Satisfaction trends and alerts

- Use pulse/feedback scores per mentor–participant pair. Trend = Improving / Flat / Declining.
- **Alert** when: scores drop in two consecutive pulses; any score ≤ 2/5; a participant writes that a session wasn't useful or asks for a change; pulses unreviewed past the review SLA.
- For each alert: the evidence, a suggested action (PM check-in, reset expectations, re-match), and the escalation level from the profile.

## 7. Re-matching

When a match fails, propose a replacement from backups/capacity with a new rationale, and a handover note so the new mentor starts from the participant's tracker, not from zero.

## Rules

- No invented credentials, availability or feedback. Mentor personal data stays inside the program's tools.
- Feedback from participants about mentors is sensitive: summarise in reports, share verbatim only with the program team.
- Writes to Airtable go through airtable-agent with confirmation. Messages to mentors are drafts until the user says send.

## Output

Longlists, matrices and tracking: a spreadsheet (house conventions) or a dashboard for ongoing tracking. Rationale and onboarding packs: a document. Alerts: a short table in the reply, ready to drop into the weekly report.
