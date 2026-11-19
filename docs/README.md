# Documentation map

Document layout accepted by the project owner on 2026-11-19 in [Setup 3](https://github.com/worldofxobu/wow-offline-viewer/issues/4).

Start with the [Setup guide](planning/setup.md). The [GitHub project](https://github.com/users/worldofxobu/projects/1) tracks current work; this map explains where lasting knowledge belongs.

| Source | Responsibility |
| --- | --- |
| [Project README](../README.md) | Purpose and entry point for a fresh checkout. |
| [Constitution](../.specify/memory/constitution.md) | Ratified principles and amendment rules. |
| [Agent instructions](../AGENTS.md) | Agent behavior, workflow invocation and automatic commit/push authorization. |
| [Contribution guide](../CONTRIBUTING.md) | How to take an issue, verify a change and submit it for review. |
| [Setup guide](planning/setup.md) | The short working method and initial coding gate. |
| [Architecture decisions](architecture/decisions/README.md) | Significant choices, evidence, alternatives and consequences. |
| [Discovery proposal](planning/project-discovery-proposal.md) | Historical initial observations and proposed options; not current status or accepted architecture. |

## Add documents when needed

- `specs/NNN-feature-name/`: Spec Kit creates feature behavior (`spec.md`), design (`plan.md`), work decomposition (`tasks.md`) and relevant research/contracts/validation scenarios. These directories do not exist yet.
- `docs/architecture/decisions/NNNN-short-title.md`: short ADRs following the linked guidance.
- `docs/discovery/`: versioned schema findings, compatibility evidence and unresolved technical questions when discovery starts.
- `docs/development/`: verified setup, test and release commands once the tooling is selected.
- `tests/fixtures/`: synthetic or reviewed sanitized data with provenance and expected results once fixtures are introduced.

Do not create empty directories or application scaffolding to match this list. Preserve the existing Spec Kit skills, templates, scripts and provenance manifests; review upgrades separately.

## Keep one home for each fact

Specs define intended behavior; ADRs record significant decisions. Feature task lists hold detailed implementation work; GitHub issues link task IDs and track ownership, dependencies, progress and review. Avoid copying whole task lists or plans into issues.

Record lasting findings and accepted decisions in the appropriate repository document, then link that document from the issue/PR. Keep reproducible acceptance scenarios and validation commands with the feature or development docs; record actual execution results and limitations in the issue/PR.

Update affected documents with a change. Label proposals and assumptions explicitly; promote a proposed decision to accepted only with recorded owner approval. Do not silently rewrite ratified principles or accepted ADR history.
