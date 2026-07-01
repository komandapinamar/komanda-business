<!--
Sync Impact Report
- Version change: unratified template -> 1.0.0
- Principles established:
  - I. Business Acquisition Ownership
  - II. Static-First Public Delivery
  - III. Contract-First Registration
  - IV. Independent Delivery and Degraded Operation
  - V. Measurable Acquisition Quality
- Sections established:
  - Architecture and Operational Boundaries
  - Development Workflow and Quality Gates
- Removed sections: none; template placeholders were replaced by ratified content.
- Dependent artifacts:
  - ✅ updated: .specify/templates/plan-template.md
  - ✅ updated: .specify/templates/spec-template.md
  - ✅ updated: .specify/templates/tasks-template.md
  - ✅ updated: README.md
  - ➖ not present: .specify/templates/commands/
- Follow-up:
  - ⚠ The first feature plan must establish concrete page-weight,
    time-to-usable, and registration-completion budgets.
-->
# Komanda Business Constitution

## Core Principles

### I. Business Acquisition Ownership

This repository MUST own Komanda's Astro public site at `komanda.com`, including
public and SEO content, commercial plan presentation, the gastronomic-business
registration experience, and acquisition analytics.

Public plan definitions and identifiers MUST have one source of truth in this
repository. Operational identities, tenants, memberships, locations, entitlements,
catalogs, carts, payments, orders, and printing MUST remain owned by Komanda Core.
This repository MUST NOT duplicate Core business rules, import private Core modules,
or access the Core data store directly.

Rationale: an explicit boundary keeps acquisition content independently editable
without creating a second implementation of the operational product.

### II. Static-First Public Delivery

Public marketing and plan pages MUST expose useful content without requiring Komanda
Core or client-side JavaScript at render time. Astro pages MUST be static-first, and
client-side code MUST be limited to interactions that require it.

Every feature plan and release MUST declare and measure a page-weight budget, a
time-to-usable target, and any route-specific performance target. An unapproved
regression against an active budget MUST block release.

Rationale: the public acquisition site must remain fast, indexable, and available
independently from the operational product.

### III. Contract-First Registration

This repository MUST own the registration form, validation feedback, submission UX,
and retry experience. Komanda Core MUST remain the sole owner of the indivisible
creation of the account, tenant, initial location, and owner membership.

Registration and every other Core interaction MUST use a documented and versioned
service contract. Contract changes MUST be backward compatible or introduced under a
new version with a migration and retirement window. Consumer contract tests are
mandatory for registration and every changed Core integration.

Cross-boundary calls MUST define timeouts, retry policy, idempotency, and correlation
identifiers. When provisioning cannot be confirmed, the site MUST NOT claim success
or imply that a tenant exists. It MUST show a retryable state and MAY retain a pending
registration intent only with explicit consent and a defined retention policy.

Rationale: the acquisition journey can evolve independently only when Core remains
authoritative and failure behavior is explicit.

### IV. Independent Delivery and Degraded Operation

This repository MUST have its own build, deployment, rollback, runtime configuration,
health checks, and release cadence. A Business release MUST NOT require a simultaneous
Core release unless a documented, backward-compatible migration sequence covers the
complete rollout.

Marketing content and plan presentation MUST remain available when Core is
unavailable. Core-dependent actions MUST fail visibly and safely without affecting
static content. Every plan MUST identify shared infrastructure and external services
that remain common failure domains.

Rationale: repository separation must reduce deployment coupling and preserve the
public site during operational outages.

### V. Measurable Acquisition Quality

Every feature MUST define measurable outcomes for the affected discovery,
plan-selection, and registration journeys. Critical registration paths MUST have
automated browser or integration coverage in addition to contract tests.

Acquisition analytics MUST be purposeful, documented, and scoped to this repository.
The site MUST NOT expose credentials, registration data, or operational tenant data in
client bundles, analytics payloads, logs, or user-visible errors. Diagnostics for
cross-boundary requests MUST include a correlation identifier without sensitive
payloads.

Rationale: conversion, reliability, and privacy require explicit evidence rather than
assumptions based on a successful build.

## Architecture and Operational Boundaries

This repository contains the independently deployable Astro surface at `komanda.com`:

- Public landing pages, SEO metadata, acquisition content, and plan presentation.
- The business-registration form and its validation, submission, retry, and status
  experience.
- Acquisition analytics and consented storage for pending registration intents when
  a feature explicitly requires them.

Komanda Core owns `app.komanda.com`, tenant storefronts, authentication, tenant
provisioning, entitlements, catalog, checkout, orders, payments, printing, and all
authoritative operational data. This repository passes versioned plan identifiers and
registration requests to Core, while Core validates those inputs and enforces the
resulting entitlement snapshot.

Business and Core MUST NOT share a writable database. This repository MAY store
public content, acquisition analytics, and consented pending intents, but it MUST NOT
store authoritative operational identity or tenant records. Mobile applications and
tenant-facing product surfaces are outside this repository.

## Development Workflow and Quality Gates

Every feature specification MUST identify:

1. The acquisition capability and source of truth being changed.
2. Affected public routes and registration steps.
3. Core contract changes and compatibility expectations, or explicitly state none.
4. Behavior when Core or another external dependency is unavailable.
5. Static-rendering impact and measurable page-weight and time-to-usable budgets.
6. Analytics, consent, retention, and sensitive-data impact.
7. Measurable discovery, conversion, and registration outcomes.

Every implementation plan MUST pass the Constitution Check before research and again
after design. A failed gate requires an explicit Complexity Tracking entry with the
reason, rejected compliant alternative, owner, and removal or migration plan.

Delivery MUST include consumer contract tests for changed Core integrations,
automated coverage for critical registration paths, performance-budget evidence, and
validation of static rendering and degraded behavior. This repository's pipeline MUST
validate and deploy it independently.

Pull requests MUST state which constitutional gates apply and provide evidence for
each one. Reviewers MUST reject changes that duplicate Core logic, introduce direct
Core data access, make marketing content depend on Core at render time, weaken
sensitive-data handling, or bypass declared performance budgets.

## Governance

This constitution supersedes informal architecture notes and implementation
convenience for the Business repository. Amendments require a documented proposal
describing the motivation, affected routes or contracts, migration impact, and
updates required in dependent templates and runtime guidance.

Versions follow semantic versioning:

- **MAJOR**: removes or incompatibly redefines a principle or ownership boundary.
- **MINOR**: adds a principle, mandatory gate, or materially expands governance.
- **PATCH**: clarifies wording without changing obligations.

Every amendment MUST update the Sync Impact Report, version, and last-amended date.
The ratification date remains the original adoption date. Amendments that change a
Core boundary MUST identify and coordinate the corresponding Core constitution or
contract update; unrelated governance evolves independently.

Compliance is reviewed during specification, planning, task generation, and pull
request review. Exceptions MUST be explicit, temporary, approved by the project
owner, and tracked with a concrete remediation condition. Silent exceptions are
prohibited.

**Version**: 1.0.0 | **Ratified**: 2026-07-01 | **Last Amended**: 2026-07-01
