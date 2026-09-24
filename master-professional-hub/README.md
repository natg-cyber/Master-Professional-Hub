# Master Professional Hub

**A bilingual career-coaching and networking workflow, designed to grow into a personal interactive app.**

This repository brings together the product workflow, AI-agent prompts, app build specification, and Job Tracker schema for a personal system supporting career development in urban planning, development, project coordination, permitting, construction administration, housing, and related fields.

> **Project status:** Product and workflow specification. The interactive application is not implemented yet.

## Start here

1. Read the [product overview](docs/product-overview.md).
2. Follow the [complete workflow](docs/workflow.md).
3. Review the [methodologies](docs/methodologies.md) that shape coaching, resume, red-flag, and interview work.
4. Review the [Master Professional Hub prompt](prompts/master-professional-hub.md) to run the agent workflow.
5. Use the [app build prompt](prompts/app-build-prompt.md) with a software-building agent to implement the application.
6. See the [tracker schema](templates/job-tracker-schema.md) before importing or exporting a workbook.

## Core interaction

At first use, the person introduces their professional sector and target roles. The agent reuses that profile, then asks which path to take:

1. Work on a job opportunity or application.
2. Work on networking independently.
3. Connect networking with an existing opportunity.

The app specification includes local data management and downloadable XLSX/CSV/JSON exports. No job applications or messages are sent automatically. Its visible methods are coaching practice, Google XYZ resume writing, senior recruiter first-pass/red-flag reading, and START interview stories.

## Repository layout

```text
master-professional-hub/
├── README.md
├── .gitignore
├── docs/
│   ├── data-model.md
│   ├── product-overview.md
│   ├── roadmap.md
│   └── workflow.md
├── private-data/
│   └── README.md
├── prompts/
│   ├── app-build-prompt.md
│   └── master-professional-hub.md
└── templates/
    └── job-tracker-schema.md
```

## Privacy

The working Job Tracker contains real records and is intentionally **not included**. Do not commit resumes, contact details, application notes, interview prep, or a populated tracker. Use a blank, sanitized workbook for development and keep personal files in an ignored local folder. See [private data guidance](private-data/README.md).

## Current scope and limitations

- The prompts and workflows are ready for review and iteration.
- Networking can be independent or optionally linked to a job opportunity.
- The app build prompt specifies import/export and workbook compatibility, but this repository does not yet contain app source code.
- Search integrations, AI-provider connections, cloud sync, and messaging are future integrations, not implemented capabilities.
- No license is included. Choose a license before publishing if you want others to reuse or modify this work.

## Suggested next step

Build the local-first MVP in the [roadmap](docs/roadmap.md): opportunity and networking records, workflow states, user-approved links, and safe data export. Add Excel import/export after the core data model works.
