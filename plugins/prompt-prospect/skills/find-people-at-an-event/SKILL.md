---
name: find-people-at-an-event
description: Show who is going to a researched conference and why, filtered by role, company, fit or relationship (speaker, sponsor, exhibitor, engaged attendee). Use when the user asks who will be at an event, wants a list of people or companies from it, or asks why someone is on the list.
---

Work from evidence the workspace already holds. Nothing here spends credits.

1. **Resolve the event.** Call `list_my_events` and match the user's words to a saved event. If it is not saved, hand over to the `plan-a-conference` skill. If research has not finished (`event_overview` shows `research.status` other than complete or partial), say what has been found so far and when to check back.
2. **Filter, do not dump.** Call `list_event_people` with the narrowest useful filters: `q` for a role, company or name; `relationship` for speakers, sponsors, exhibitors or engaged attendees; `fit` for STRONG and PLAUSIBLE when the user wants matches; `edition` for a past year. Default `limit` is 40; page with `offset` only when the user asks for more.
3. **Present people with their evidence.** For each person give name, headline, company and the one-line reason they are on the list (the evidence excerpt and source). Group by relationship when the list mixes them. Companies come from `list_event_companies` with their role and how many of their people are in the event.
4. **Go deeper on request.** `person_evidence` returns every observation for one person; use it when the user asks "why is this person here" or doubts an entry. `search_prospects` searches across every saved event when the user asks about a person or company rather than one event.
5. **Save decisions.** When the user says they want to meet someone, call `set_people_status` with `pursue` (or `watch` for later, `dismiss` to drop), passing the people's `link_id` values from `list_event_people` as `link_ids`, and `note_person` with the person's `link_id` as `event_person_id` to keep what they said, in their words.

Boundaries: attendance is only ever what the evidence shows; say "listed as a speaker" or "engaged with the event's posts", never "will attend". Do not fabricate contact details; the tools return LinkedIn profile URLs, not emails or phone numbers.
