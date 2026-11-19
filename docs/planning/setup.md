# Setup: ready for application coding

**Working method accepted by the project owner on 2026-11-19.**

The [constitution](../../.specify/memory/constitution.md) was ratified as v1.0.0 on 2026-11-19. Use the [documentation map](../README.md) and [contribution guide](../../CONTRIBUTING.md) for workspace instructions. Follow the project's current status and dependencies for the next task; ratification does not authorize feature coding.

Work is tracked in the [WoW Offline Viewer project](https://github.com/users/worldofxobu/projects/1). Use its **Stage = Setup** field and **Setup** milestone to find this work. This page is the short entry point; the [discovery proposal](./project-discovery-proposal.md) is background reference, not a checklist to read before each task.

## What comes first?

Agree on the working method → write the constitution → prepare the workspace → use Spec Kit for the first feature.

The constitution records the lasting rules we agree on. It does not require choosing a UI framework or answering every product question first. Ordinary setup work uses small GitHub issues; we do not need a full feature specification just to establish the process.

## Accepted working method

1. **One task at a time.** GitHub Issues describe outcomes and acceptance criteria; the project tracks status, priority and dependencies. Ask only the decisions needed for the current task, normally one focused question at a time.
2. **Keep durable knowledge in the repository.** The constitution holds lasting principles; short feature specs hold intended behavior; ADRs record significant technical choices. Link to these from issues rather than copying the same plan everywhere.
3. **Use Spec Kit for features.** Specify → clarify what matters → review → plan → tasks → analyze → review readiness → implement. Request appropriate automated tests explicitly in each behavioral spec. Do not run the bundled full workflow during setup: it proceeds into implementation.
4. **Use GitHub Flow for repository changes.** Small branch → focused pull request → relevant checks and review → merge into `main`. Project planning edits can happen directly in GitHub. Decide a practical review policy for the actual team; do not assume a second reviewer exists.
5. **Require evidence.** Behavior changes need meaningful tests; documentation needs appropriate document checks. Record what ran and any limitations. Keep build/test steps repeatable with free/open-source development dependencies; AI assistance is optional.
6. **Protect WoW data.** Access SavedVariables read-only, never execute them, and keep raw player data local. Use synthetic or reviewed sanitized fixtures. Select stack and architecture through short, evidence-based decisions when those tasks arrive.

## Setup checkpoints

| Order | Outcome | Depends on |
| --- | --- | --- |
| 1 | [Agree on this lightweight working method](https://github.com/worldofxobu/wow-offline-viewer/issues/2). | Owner review. |
| 2 | [Ratify a short project constitution](https://github.com/worldofxobu/wow-offline-viewer/issues/3) using `speckit-constitution`. | 1 |
| 3 | [Establish repository/AI instructions and document ownership](https://github.com/worldofxobu/wow-offline-viewer/issues/4). | 2 |
| 4 | [Agree and configure GitHub review and quality policies](https://github.com/worldofxobu/wow-offline-viewer/issues/5). | 1; actual CI checks are connected in 7. |
| 5 | [Confirm the first-release boundary and minimum supported input](https://github.com/worldofxobu/wow-offline-viewer/issues/1). | 2 |
| 6 | [Select the initial stack and verify developer tools](https://github.com/worldofxobu/wow-offline-viewer/issues/6). | 3, 5 |
| 7 | [Establish the initial QA/tooling baseline and honest CI checks](https://github.com/worldofxobu/wow-offline-viewer/issues/7). | 3, 4, 6 |
| 8 | [Prepare and review the first feature's spec, plan and small tasks](https://github.com/worldofxobu/wow-offline-viewer/issues/8). | 2–7 |

Each checkpoint has its own project issue with acceptance criteria. Dependencies determine when work becomes ready; do not start all checkpoints at once. GitHub is the source of truth for completion, so this page does not duplicate checkboxes or status reports.

The [first-release scope](first-release-scope.md) records the accepted browse flow and the remaining discovery questions. It also proposes where UI wireframes and feature design fit before coding.

## Coding gate

Setup ends when the working rules and constitution are accepted, developer setup is repeatable, repository checks are working, and the first feature has an accepted specification, architecture decisions, a reviewed plan and small tasks with test requirements.

Before that gate, scope is documentation, discovery, configuration and explicitly scoped tooling/test scaffolding. No application features or throwaway application prototypes. Skeleton build/test wiring, if needed after stack approval, belongs to checkpoint 7; do not report unimplemented application checks as passing.

Later feature questions are deferred until their checkpoint needs them. No final framework or storage choice has been made.
