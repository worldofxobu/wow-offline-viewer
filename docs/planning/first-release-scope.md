# First-release scope

Related work: [Setup 5](https://github.com/worldofxobu/wow-offline-viewer/issues/1).

Status: browsing scope and edition priorities accepted by the owner on 2026-11-19; exact source compatibility and release details remain unresolved. This is a discovery brief, not a feature specification or implementation plan.

## Accepted scope

- Windows desktop viewer using Altoholic/DataStore SavedVariables.
- Browse characters → a character's professions → recipes recorded in the source data.
- Defer a complete catalog of missing/unlearned recipes.
- Target WoW: Forever first. Defer Classic Era to later work; Retail is a low priority with no first-release support commitment.
- Treat imported files as untrusted, read-only data; never execute them or publish raw player data.
- Continue with requirements, source discovery and design. The owner explicitly confirmed that application coding is too early.

Approval evidence: the owner answered “of course yes” to the proposed browse flow and deferred catalog, while emphasizing that features and design must be developed before coding.

Edition priority evidence: “Def should support Wow: Forever first we can work on classic era later, and don't care much for retail.” This establishes product priority; it does not verify a client build, addon version or the origin of the local samples.

The owner subsequently confirmed that the existing local SavedVariables samples are from their WoW: Forever installation. [Source discovery](../discovery/savedvariables.md) distinguishes that owner-reported provenance from structural observations and unresolved compatibility evidence.

Conditional owner preference: use local WoW data for display metadata where feasible and permitted, rather than defaulting to online lookup. [Local metadata research](../discovery/local-metadata-options.md) separates in-game API export from archive reading. No mechanism or offline guarantee is accepted yet.

## Recommendations to review

- Start with enough fields to identify a character, profession and recorded recipe. Exact fields, labels and availability must be checked against the supported data before acceptance.
- Use low-detail Figma wireframes during Setup 5 to explore the browse flow once the data is understood. Refine the first feature's layouts, keyboard behavior and loading/empty/error states alongside its specification in Setup 8, before finalizing its implementation plan.
- Keep durable design requirements and accepted decisions in version-controlled documentation, with links to relevant Figma frames. Figma should not become the only record needed to implement a feature.

These recommendations do not select a UI framework, approve a design or authorize implementation. No Figma board has been created for this work.

Candidate essential fields for owner review:

| Browse level | Proposed fields |
| --- | --- |
| Character | Name, realm and level; retain account context for identity. |
| Profession | Name and current/maximum rank when recorded. |
| Recorded recipe | Name when available, recipe ID and recorded learned/unlearned status. |

Recipe-name availability needs a metadata decision: the inspected addon resolves names through WoW's game API. A complete catalog is still deferred even if some unlearned recipes are present in the saved data.

## Unresolved decisions and evidence

1. Confirm the intended compatibility baseline against the samples. Installed client `1.60.1.70959`, Altoholic `1.60.005` and relevant DataStore modules `2026.10.14` are verified locally; their source establishes candidate relationships. The samples' exact generating versions and a tested supported range remain unresolved.
2. Essential display fields and available recipe names/metadata; do not promise information the source cannot supply.
3. Windows version/CPU target, offline expectations and how users refresh source data.

The [source discovery record](../discovery/savedvariables.md) holds metadata, source-derived mappings and verification limits. No application import, compatibility tests or recipe-completeness checks have run; keep raw samples local.

## Before application coding

Follow the [Setup coding gate](setup.md#coding-gate): resolve the relevant scope and source questions, select the stack through documented decisions, establish QA, then prepare and review the first feature's specification, design, plan and small tasks. Owner acceptance of this browsing scope alone does not authorize coding.
