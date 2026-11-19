# WoW Offline Viewer Constitution

**Status: ratified by the project owner on 2026-11-19.**

## Core Principles

### I. Simple, modular and maintainable design
The application MUST follow KISS, DRY, YAGNI, separation of concerns and clean code principles.
Modules MUST have clear responsibilities and testable boundaries; domain rules MUST remain
independent of UI frameworks and imported-file schemas. Extensibility and reusability MUST serve
demonstrated needs, without premature abstractions, speculative features or unnecessary complexity.

### II. Careful dependency reuse
Development dependencies MUST be free/open-source and kept to those justified by current needs.
Reliable, established libraries MUST be evaluated before reimplementing existing functionality.
Dependency choices MUST consider maintenance, security and licensing, not dependency count alone.
Required tool versions and setup/build/test commands MUST be documented; builds and tests MUST NOT
require a paid IDE or AI subscription.

### III. Security and data integrity
Imported files MUST be treated as untrusted and read-only, and MUST NOT be executed.
Import and failure handling MUST preserve source data and validate input before using it.
Raw player data MUST stay local and out of commits, external tools, logs and public artifacts.
Tests and shared examples MUST use synthetic or reviewed sanitized data.

### IV. Specification-driven, independently verifiable changes
Features MUST follow specification-driven development with reviewed scope, plans and small tasks.
Changes MUST use version control and focused branches/PRs with acceptance criteria, relevant checks
and review. Each change MUST be independently verifiable and respect the accepted architecture;
significant architectural changes MUST be documented in ADRs.
Work one task at a time and ask only decisions needed now, normally one focused question at a time.

### V. Meaningful automated testing
Behavioral feature specifications MUST explicitly require appropriate automated tests, including
relevant failure and safety cases. Bug fixes MUST include regression tests.
Changed behavior MUST have verification evidence; checks MUST NOT be weakened to hide failures.
Reported results MUST distinguish passed, failed and not run, including material limitations.

### VI. Durable knowledge and accountable AI assistance
All project knowledge needed to develop and maintain the application MUST persist in
version-controlled documentation rather than depend on AI context.
Principles belong in the constitution, behavior in feature specs, and architectural decisions in
ADRs; issues MUST link relevant documents and evidence. Affected docs MUST change with the work.
AI agents MUST verify assumptions against evidence or mark them unresolved, respect the existing
architecture, and MUST NOT claim unexecuted tests have passed.

## Scope and boundaries

The initial product is a Windows desktop viewer for character, profession and recipe data.
Supported inputs, frameworks, storage and distribution MUST be decided through discovery and ADRs.
Application feature implementation MUST wait for the
[Setup readiness gate](../../docs/planning/setup.md#coding-gate).

## Development workflow

Features MUST follow: specify → clarify relevant uncertainties → review → plan → tasks →
analyze → review readiness → implement → verify/review → merge.
Setup and administrative work MAY use focused issues without full feature specifications.
A task is ready when its outcome, acceptance criteria, dependencies and verification are clear.
It is done when those criteria are met, checks and review are recorded, and affected docs are current.
Review policy MUST fit the actual maintainers; do not assume a second reviewer exists.

## Governance

After ratification, these principles govern project work; detailed procedures belong in the
[contribution guide](../../CONTRIBUTING.md) and scoped repository instructions.
Amendments MUST record rationale, impact and owner approval, and reconcile affected documents.
Use semantic versions: major for incompatible rule changes, minor for new or expanded rules,
patch for clarifications. Check compliance during planning and PR review; any exception MUST have
explicit owner approval, a recorded rationale and a bounded scope.

**Version**: 1.0.0 | **Ratified**: 2026-11-19
**Last Amended**: 2026-11-19
