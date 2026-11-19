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

## Recommendations to review

- Start with enough fields to identify a character, profession and recorded recipe. Exact fields, labels and availability must be checked against the supported data before acceptance.
- Use low-detail Figma wireframes during Setup 5 to explore the browse flow once the data is understood. Refine the first feature's layouts, keyboard behavior and loading/empty/error states alongside its specification in Setup 8, before finalizing its implementation plan.
- Keep durable design requirements and accepted decisions in version-controlled documentation, with links to relevant Figma frames. Figma should not become the only record needed to implement a feature.

These recommendations do not select a UI framework, approve a design or authorize implementation. No Figma board has been created for this work.

## Unresolved decisions and evidence

1. Exact WoW: Forever client build and addon/schema versions; verify the character/profession/recipe relationships against matching addon source. The owner confirms the samples are from Forever; their exact export build and addon versions remain unresolved.
2. Essential display fields and available recipe names/metadata; do not promise information the source cannot supply.
3. Windows version/CPU target, offline expectations and how users refresh source data.

No compatibility, schema decoding or recipe completeness has been verified in this brief. Record technical evidence under [discovery](../README.md#add-documents-when-needed) as it is established; keep raw samples local.

## Before application coding

Follow the [Setup coding gate](setup.md#coding-gate): resolve the relevant scope and source questions, select the stack through documented decisions, establish QA, then prepare and review the first feature's specification, design, plan and small tasks. Owner acceptance of this browsing scope alone does not authorize coding.
