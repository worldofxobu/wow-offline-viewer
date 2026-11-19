# WoW Offline Viewer

WoW Offline Viewer is a planned Windows desktop application for browsing characters, professions and recipes from Altoholic/DataStore SavedVariables. The repository is in setup with Spec Kit initialized; supported inputs and the implementation stack are still to be decided.

Start with the short [Setup guide](./docs/planning/setup.md). It records the accepted working method and the checkpoints needed before application coding. The detailed discovery proposal is background reference.

## Start here

1. Open the [project](https://github.com/users/worldofxobu/projects/1) and the active Setup issue to find its outcome, acceptance criteria and dependencies.
2. Read [Contributing](./CONTRIBUTING.md) and the ratified [constitution](./.specify/memory/constitution.md). AI sessions must also follow [AGENTS.md](./AGENTS.md).
3. Use the [documentation map](./docs/README.md) to find specs, decisions and durable project knowledge.

No application build or test commands exist yet. Developer toolchain setup is tracked in [Setup 6](https://github.com/worldofxobu/wow-offline-viewer/issues/6), and the QA/CI baseline in [Setup 7](https://github.com/worldofxobu/wow-offline-viewer/issues/7).

## Project tracking

- [Issues](https://github.com/worldofxobu/wow-offline-viewer/issues): bugs, feature requests, and implementation tasks.
- [Project](https://github.com/users/worldofxobu/projects/1): the linked planning and progress board.
- [Contributing](./CONTRIBUTING.md): reporting guidelines and the issue workflow.

Use the issue forms to describe a problem or outcome and its acceptance criteria. Link detailed specifications and plans from the corresponding issue.

## Local data

`SavedVariables/` is reserved for local WoW data and is ignored by Git. Do not publish raw SavedVariables files or personal account data in issues or pull requests.
