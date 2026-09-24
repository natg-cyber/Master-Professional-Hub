# Roadmap

## Stage 1 — Local-first MVP

- First-use professional profile and three-way workflow router.
- Opportunity list/detail, contact list, conversation notes, optional relationships.
- Application and red-flag states; resume/cover-letter approval gates.
- Local persistence, search/filter, editable drafts, data export to JSON/CSV.

## Stage 2 — Job Tracker compatibility

- Import workbook with preview, header-based mapping, duplicate decisions, and unknown-field retention.
- Export an updated copy preserving source worksheets, headers, data, and supported formulas.
- Round-trip using a blank/sanitized copy of the real workbook.

## Stage 3 — Optional AI assistance

- Configurable provider adapter for assessment, draft wording, interview practice, and research summaries.
- Evidence references, user review, and explicit privacy choice before sending personal data to a provider.
- No automatic applications, outreach, or workbook writes.

## Stage 4 — External integrations (only after API and authorization exist)

- Job search, calendar, or other connectors.
- Clearly scoped permissions, visible drafts, and user-controlled actions.

## Acceptance checkpoints

- A user can run networking without creating an opportunity.
- A user can link and unlink a conversation and opportunity without duplicate records.
- Cover letter gate blocks unapproved resume versions.
- Import/export does not alter the user's source workbook.
- A sanitized export can be imported again without losing supported records or unknown fields.
- The interface identifies when it is using coaching, Google XYZ, senior recruiter first-pass/red-flag review, or START, without inventing evidence or forcing a method into an unsuitable interaction.
