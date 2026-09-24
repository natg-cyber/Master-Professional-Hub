# Data model

The app build prompt contains the implementation-ready field list. This page summarizes the core entities and their relationships.

```text
ProfessionalProfile
  └── reused for coaching context; contains user-provided sector, roles, optional geography/goal

Opportunity 1 ─── * CareerArtifact
Opportunity 1 ─── * RedFlag
Opportunity * ─── * Contact (optional, user-created relationship)
Contact 1 ─── * Conversation
Conversation * ─── * Opportunity (optional, confirmed by user)
```

## Entities

- **ProfessionalProfile:** target sector, roles, optional geography and goal; user supplied, refreshable.
- **Opportunity:** one job/candidacy with company, role, source, JD, status, scores, skills/gaps, next action, red flags, and artifact references.
- **Contact:** professional identity/context with source and verification note; no inferred personal attributes.
- **Conversation:** user-reported date/channel, summary, learnings, commitments, follow-up and optional opportunity links.
- **CareerArtifact:** resume/letter/interview material with type, version, source opportunity, and version-specific approval state.
- **RedFlag:** stable ID, description, evidence status, and resolution state scoped to one opportunity.

Use stable IDs. Linking records must not copy/duplicate the opportunity or contact. Retain unknown imported columns/values during workbook round trips.
