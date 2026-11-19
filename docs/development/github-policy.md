# GitHub review and quality policy

**Status: proposed for owner review in [Setup 4](https://github.com/worldofxobu/wow-offline-viewer/issues/5).**

The owner confirmed a solo-maintainer setup on 2026-11-19. The policy below is prepared for review; the [settings payload](github-settings-proposal.json) has not been applied.

## Work and review

- Keep `main` releasable. Use descriptive, short-lived branches such as `docs/github-policy`, `feat/character-browse` or `fix/recipe-id`; follow the installed Spec Kit integration's feature naming where applicable. Check the active feature context separately from the Git branch name.
- Each PR has one purpose, linked issue/spec/task references, acceptance criteria and verification evidence. Use the [PR template](../../.github/PULL_REQUEST_TEMPLATE.md); split unrelated changes before review.
- The owner reviews the diff, checks the recorded evidence and accepts the result. A second human reviewer, CODEOWNERS approval and approval of the last push by another person are not required for the solo model.
- Use squash merge with a meaningful commit title consistent with repository history. Agents may commit and push automatically, but require explicit owner authorization to merge; accepting a document or issue alone is not merge authorization.
- Resolve review conversations before merging. Do not force-push or delete `main`. Keep hooks and signing requirements intact.
- When new people join, review this policy before changing approval requirements.

**Ready:** outcome and acceptance criteria are clear; dependencies are satisfied; significant uncertainties are resolved or explicitly deferred; required verification is identified.

**In Review:** the coherent change and affected docs are prepared, relevant checks have run, limitations are recorded, and the PR or decision is ready for owner review.

**Done:** acceptance criteria and verification are met, affected docs are current, and the owner accepts the result. Record integration separately: a pushed branch or accepted issue does not mean its PR has merged.

## Proposed GitHub enforcement

| Setting | Proposed value |
| --- | --- |
| Merge methods | Squash only. |
| Changes to `main` | Require a pull request, including for administrators. |
| Required approving reviewers | Zero, to support the solo maintainer. |
| Extra review requirements | No CODEOWNERS or last-pusher-independent approval. |
| History | Linear history. |
| Review discussions | Resolve conversations before merging. |
| Force pushes / deletion of `main` | Disallowed. |
| Required status checks | None yet; add only verified checks in Setup 7. |

GitHub's [branch-protection API](https://docs.github.com/en/rest/branches/branch-protection#update-branch-protection) supports zero required approving reviewers. Owner acceptance and agent merge authorization remain workflow requirements; zero approvals does not enforce those through a GitHub review vote. Repository merge flags are documented in the [repository API](https://docs.github.com/en/rest/repos/repos#update-a-repository).

The payload targets only this repository's merge methods and protection of `main`. It does not merge PR #9, change visibility or access, turn on auto-merge, or change branch-deletion-on-merge settings.

## Checks to establish in Setup 7

| Change | Required verification to implement with the selected toolchain |
| --- | --- |
| Documentation / configuration | Formatting, local links, configuration validity and repository hygiene. |
| Application behavior | Windows build/static analysis and relevant unit/integration tests; regression tests for bug fixes. |
| Imported-data handling | Parser/schema contracts, malformed/unsupported input, source read-only guarantees and safe failure paths. |
| UI journeys | Relevant browse/error states and keyboard/accessibility checks; add automation where supported. |
| Dependencies / workflows | Security and license review, reproducible versions, minimal workflow permissions and reviewed action pins. |

Setup 7 must select stable check names, prove they run and fail correctly, and then connect them to branch protection. Required checks must report a result for every relevant PR, including documentation-only changes when applicable. Do not add nonexistent check names or replace missing tests with dummy successes. Keep raw samples and secrets out of CI inputs and artifacts.

## Verified baseline before application

Inspected on 2026-11-19: public repository, `main` default branch, authenticated account has admin access; all three merge methods enabled; auto-merge and automatic head-branch deletion disabled; no rulesets, no protection on `main`, and zero Actions workflows. This is the before-state, not a claim that the proposed settings are active.

After owner approval, apply the reviewed payload, read back the settings and record verification in the issue. Template and documentation changes become available on the default branch when their PR is merged.
