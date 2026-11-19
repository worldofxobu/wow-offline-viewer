# Repository agent instructions

## Use the requested command or workflow

- When the user requests a named command, skill or workflow, invoke it through the
  supported host/integration mechanism with the user's input. Do not substitute
  ad hoc scripts, a partial reenactment or manually prepared lookalike outputs.
- Establish the actual invocation mechanism before changing that workflow's outputs.
  If it is unavailable, stop the affected work, explain the limitation and ask the
  user to trigger it or explicitly authorize an alternative. Do not silently work around it.
- Follow the complete workflow, including its scope, prerequisites, scripts, hooks,
  review gates and validation. Reading its instructions alone does not demonstrate
  that the requested workflow was invoked or completed.
- Report what actually happened. Distinguish invoking a command, following an
  instruction-based skill, running helper scripts and manually editing files.
  Never claim a command ran or tests passed without execution evidence.
- Do not invent a shell command, wrapper or successful invocation to satisfy this rule.
  For example, do not replace a requested Spec Kit constitution run with a hand-written
  constitution and describe it as a completed command.

## Automatically commit and push completed batches

- The owner grants standing authorization to commit and push completed, in-scope
  batches of work. Do not ask for fresh authorization after every batch.
- A batch is one coherent task or reviewable change with its applicable verification
  completed. Saving a batch does not imply owner approval of pending decisions or reviews.
- After relevant checks pass, use the commit and sync workflows to create a meaningful
  commit and push the working branch. Follow GitHub Flow and configure upstream when needed.
- Stage only changes belonging to the batch. Preserve unrelated or user-staged work;
  if ownership or scope is unclear, stop and explain before committing it.
- Verify the working tree and upstream ahead/behind state afterward. Report the commit,
  branch, verification results and any remaining changes. Do not create empty commits.
- If checks fail or sensitive data, an ambiguous remote, conflicts or authentication
  prevent publication, report the blocker instead of claiming completion.
- This authorization does not permit merging PRs, force-pushing, changing branch protections,
  or bypassing hooks, signing or tool-approval requirements. Follow the user's specific
  instructions if they request a batch remain uncommitted or unpushed.

## Current project context

- Start with the short [Setup guide](docs/planning/setup.md) and the active GitHub issue.
  Work on one task at a time; ask only decisions needed for that task.
- Read the issue's acceptance criteria, the [contribution guide](CONTRIBUTING.md), and any
  relevant feature spec, tasks and ADRs before editing. Find current work in the project;
  do not infer its status from chat history or a stale local note.
- Inspect the current Git branch and working tree before changes; preserve unrelated work.
  Distinguish verified facts, assumptions, recommendations and unresolved decisions.
- Follow the [constitution](.specify/memory/constitution.md), ratified as v1.0.0 on 2026-11-19.
  Its ratification does not approve an application architecture or authorize feature coding.
- Keep WoW SavedVariables read-only and unexecuted. Keep raw player data local and
  out of commits, external tools, logs and public artifacts.
- Keep these instructions consistent with the owner's decisions and the ratified
  constitution. The long discovery proposal is background reference.
- Follow the [documentation map](docs/README.md). Record lasting findings and accepted
  decisions in repository documents, link them from issues, and update affected docs with the work.
- Review [ADR guidance](docs/architecture/decisions/README.md) before proposing significant
  architectural changes. Keep feature test requirements explicit and follow the constitution.
