# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]

**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command. See
`.specify/templates/plan-template.md` for the execution workflow.

**Owning Repository**: Komanda Business (Astro)

**Core Contract Impact**: [None, or contract plus compatibility impact]

## Summary

[Extract from feature spec: primary requirement + technical approach from research]

## Technical Context

**Language/Version**: [TypeScript and Node versions, or NEEDS CLARIFICATION]

**Primary Dependencies**: [Astro and relevant integrations, or NEEDS CLARIFICATION]

**Content/Storage**: [static content, CMS, consented pending intents, or N/A]

**Testing**: [unit, browser, contract, and performance tooling]

**Target Platform**: [modern web browsers and deployment platform]

**Project Type**: Astro public acquisition website

**Performance Budgets**: [page weight, time-to-usable, route targets]

**Accessibility Target**: [standard and verification approach]

**Scale/Scope**: [routes, content volume, expected registrations]

**Core Contracts**: [versioned contracts changed or None]

**Analytics and Privacy**: [events, consent, retention, sensitive-data handling]

**Degraded Mode**: [behavior when Core or another dependency is unavailable]

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- **Business ownership**: [PASS/FAIL — acquisition capability and source of truth identified]
- **Static-first delivery**: [PASS/FAIL — useful content renders without Core or unnecessary JS]
- **Contract-first registration**: [PASS/FAIL/N/A — versioning, compatibility, retry, and idempotency defined]
- **Independent delivery**: [PASS/FAIL — build, rollback, and degraded mode remain independent]
- **Measurable quality**: [PASS/FAIL — performance, journey, analytics, and privacy evidence defined]

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── contracts/
└── tasks.md
```

### Source Code (repository root)

```text
src/
├── components/
├── content/
├── layouts/
├── pages/
└── services/

public/

tests/
├── contract/
├── e2e/
└── unit/
```

**Structure Decision**: [Document the selected Astro structure and real paths]

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., server-rendered marketing route] | [specific need] | [why static rendering is insufficient] |
| [e.g., coordinated Core release] | [specific need] | [why a compatible contract rollout is insufficient] |
