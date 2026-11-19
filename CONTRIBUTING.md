# Contributing

The project is currently in setup. Begin with the [Setup guide](./docs/planning/setup.md); its working method was accepted on 2026-11-19. App development begins after the Setup coding gate is met.

Use [GitHub Issues](https://github.com/worldofxobu/wow-offline-viewer/issues) to report bugs, propose features, and track work. Search for an existing issue first, then choose the bug report, feature request, or task form.

## Tracking work

- Keep each issue focused on one outcome and include acceptance criteria.
- Use `bug`, `enhancement`, or `documentation` labels as appropriate. Add `good first issue` or `help wanted` when the task is ready for contributors.
- Add accepted issues to the repository's linked GitHub project. Set a priority and move work through its status columns as it progresses.
- Assign issues when someone takes responsibility. Record dependencies and link relevant specifications, plans, or task entries.
- Reference the issue from a pull request with `Closes #<number>` when the pull request completes it. Close issues after their acceptance criteria are met.

The repository is initialized with Spec Kit. Keep detailed design and implementation plans in the repository and link them from the corresponding GitHub issues; use GitHub for ownership, discussion, priority, and progress.

## Working on an issue

1. Read the issue's acceptance criteria and dependencies, the [constitution](./.specify/memory/constitution.md), and relevant specs/ADRs from the [documentation map](./docs/README.md). Record uncertainties explicitly.
2. Inspect `git status --short` and `git branch --show-current`. Work on a focused branch; keep unrelated changes intact.
3. Make a small change, update affected docs and run relevant checks. Behavioral specs must explicitly request automated tests; bug fixes need regression tests. For documentation, check links, formatting and `git diff --check`.
4. Record checks run, results and limitations in the issue/PR. Use a focused PR into `main` for review and integration. Repository settings, merge strategy and required-check enforcement are handled in [Setup 4](https://github.com/worldofxobu/wow-offline-viewer/issues/5).

Agents have standing authorization to commit and push completed, verified batches under [AGENTS.md](./AGENTS.md#automatically-commit-and-push-completed-batches). This publishes the working branch; it does not merge it or approve pending decisions.

To find current work without chat history:

```powershell
gh project item-list 1 --owner worldofxobu --format json
gh issue view 4 --repo worldofxobu/wow-offline-viewer
```

Use project status and dependencies to identify ready work; replace `4` with the chosen issue number. If GitHub is unavailable, report that limitation rather than guessing status. Keep durable knowledge in the repository, using the documentation map; do not maintain a second project-status checklist in docs.

## Sharing examples

The local `SavedVariables/` directory is ignored by Git. Read source files without writing to or executing them. Keep raw WoW SavedVariables and account data out of commits, issues, logs, screenshots, CI artifacts and external tools.

Prefer small synthetic fixtures. If a sanitized fixture is necessary, review nested strings and identifiers for account names, characters, realms, guilds, GUIDs, mail and local paths. Record provenance, permission/license where applicable, represented schema and expected outcome before sharing it. Ignoring a directory does not make its contents safe to upload.

Create `tests/fixtures/` with its provenance notes when actual approved fixtures are introduced; do not copy the local sample directory into tests. Fixture checks and automated data-safety checks will be established with the QA baseline.
