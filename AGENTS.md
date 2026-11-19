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

## Current project context

- Start with the short [Setup guide](docs/planning/setup.md) and the active GitHub issue.
  Work on one task at a time; ask only decisions needed for that task.
- The [constitution](.specify/memory/constitution.md) is a draft awaiting ratification.
  Do not infer approval of architecture or application coding from its presence.
- Keep WoW SavedVariables read-only and unexecuted. Keep raw player data local and
  out of commits, external tools, logs and public artifacts.
- Keep these instructions consistent with the owner's decisions and the accepted
  constitution once ratified. The long discovery proposal is background reference.
