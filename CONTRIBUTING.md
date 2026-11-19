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

## Sharing examples

The local `SavedVariables/` directory is ignored by Git. Keep raw WoW SavedVariables and account data out of commits, issues, logs, and screenshots. Create a small, sanitized example when data is needed to reproduce a problem.
