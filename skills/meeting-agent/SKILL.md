---
name: meeting-agent
description: Turns meeting recordings and transcripts (Fireflies or pasted notes) from any program into minutes, decisions and owned action items, then pushes the action items to the program mastersheet or Airtable after confirmation. Use for "write up the meeting", "minutes from today's steering committee", "what did we decide", "pull the actions from the Fireflies call", "log the actions in Airtable", "update the action items from the standup", or "send a recap".
---

# Meeting Agent

Turn a conversation into a record people can act on: what was decided, who does what by when.

Load `references/program-profile.md` (governance, owners, status vocabulary, tools) and `references/minutes-templates.md`.

## 1. Find the meeting

- **Fireflies connected:** use `fireflies_search` or `fireflies_get_transcripts` by title, date or participant; confirm the match with the user if more than one fits. Pull `fireflies_get_summary` and `fireflies_get_transcript`. Work from the transcript; treat Fireflies' summary as a hint, not the record.
- **Pasted or attached notes/transcripts:** use those.
- **Nothing given:** ask which meeting (title or date).

## 2. Identify the meeting type

Steering committee · client update · internal standup · mentor/EIR sync · selection committee · founder check-in · partner call · event debrief. The type sets the template in `references/minutes-templates.md`.

## 3. Extract

- **Attendees** — from the meeting record; mark anyone only mentioned as "referenced".
- **Decisions** — only what was actually agreed. Phrase as "Agreed: …" with who agreed. Suggestions and opinions are not decisions; put them under Discussion.
- **Action items** — each needs: action (verb first, concrete), owner, due date, source (timestamp or quote). If the owner or date wasn't stated, write `[owner?]` / `[date?]` — never assign one.
- **Open questions / parked items.**
- **Risks or escalations** raised, with the escalation level from the profile.
- **Approval gates** touched (e.g. client sign-offs) and their new state.

Rules: attribute statements to speakers carefully; when the transcript is ambiguous, say so. No invented quotes. Keep sensitive personal remarks about participants (founders, mentors) out of minutes that go to a wider audience; flag them to the user instead.

## 4. Write the minutes

Use the template for the type. Lead with decisions and actions; keep discussion short. Run external-facing minutes through humaniser-agent's rules.

## 5. Push the actions (on confirmation)

Show the action list as it will be written, then ask: mastersheet, Airtable, both, or neither.

- **Mastersheet (Action Items tab):** add rows with the next number in the right stage, Action, Responsible, Status = Not Started (or the profile's vocabulary). Match against existing open items first — update instead of duplicating. Work on a copy; return a change log. (See program-agent's sheet rules.)
- **Airtable:** follow airtable-agent's read sequence to find the actions/tasks table; match existing records by text and owner; create or update in batches of up to 10 after the user's yes.
- Note the meeting date and link on each item so it traces back.

## 6. Recap message (optional)

Draft a short recap for email or WhatsApp: decisions, actions with owners and dates, next meeting. Draft only — never send without a clear yes; a Gmail draft is fine when asked.

## Output

Minutes as a document (or in the reply for short internal meetings), the action list as a table, and a one-line note of where the actions were pushed.
