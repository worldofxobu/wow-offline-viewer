# Local WoW metadata options

Related work: [Setup 5](https://github.com/worldofxobu/wow-offline-viewer/issues/1). Checked on 2026-11-19. Status: research and recommendations; no metadata architecture approved or implemented.

## Owner preference

Prefer the user's local WoW installation for item/recipe information and textures when technically feasible and permitted by the applicable terms. This does not decide offline-from-first-launch behavior or authorize a companion addon, client archive extractor or asset redistribution.

## Verified facts

- The owner's Forever installation and addon versions are recorded in [source discovery](savedvariables.md). Its shared `Data` directory contains `data`, `indices` and `config` directories. No archive contents were extracted or decoded for this research.
- The installed Altoholic recipe UI uses `C_Spell.GetSpellName`, `C_Item.GetItemInfo` and `C_Item.GetItemIconByID`. These calls explain where its display metadata comes from; they do not expose a desktop API.
- [WowLua's author description](https://www.curseforge.com/wow/addons/wowlua) identifies it as an in-game scripting environment. It is not an independent offline WoW runtime or an external API service. Forever compatibility was not established; it is not installed in the inspected addon directory.
- [CascLib](https://github.com/ladislav-zezula/CascLib) provides an MIT-licensed reader for Blizzard CASC storage. [wow.export](https://github.com/Kruithne/wow.export) documents local-client extraction, DB2 viewing and texture conversion. These establish that local extraction is technically possible in general, not that either tool supports this exact Forever build or that Blizzard authorizes our proposed use.

## Two routes to evaluate

| Route | Potential use | Limits and evidence still needed |
| --- | --- | --- |
| In-game addon exports a metadata snapshot through SavedVariables | Resolve relevant recipe/item names and icon references through the game's exposed APIs while the user plays; later read the snapshot offline. | A separate component requiring specification and approval. Verify Forever APIs, missing/asynchronous data, locale, coverage and export lifecycle. The desktop viewer would keep imported files read-only. |
| Desktop reads installed client archives | Potentially obtain metadata tables and texture files without running the game. | Resolve permission first. Then verify exact-build formats, locale, file-ID mappings, missing local content, image conversion, dependencies and strictly local read-only operation. A reader capable of online fetching must not silently introduce a network requirement. |

**Textures need a separate decision.** An exported icon file ID or path is a reference, not image pixels the desktop app can render directly. The first route can supply those references; obtaining actual image bytes still needs a permitted source and suitable decoding. SavedVariables serialization is not an export of WoW's rendered texture system. Do not infer image availability from a successful name lookup.

**Local does not automatically mean offline from first launch.** The addon route needs an earlier game session to collect data. Completeness of uncached API responses and a partial local installation are unverified. Later offline browsing of a captured snapshot is a plausible design, not a tested guarantee.

## Terms and permission findings

Blizzard's [UI Add-On Development Policy](https://eu.forums.blizzard.com/en/wow/t/wow-user-interface-add-on-development-policy/1642) provides a policy framework for addons, requires compliance with the ToU/EULA, and reserves Blizzard's ability to disable addon functionality. This supports investigating an ordinary addon using exposed APIs; it is not approval of this particular export workflow or an external archive reader.

The published [Blizzard EULA](https://www.blizzard.com/en-us/legal/08b946df-660a-40e4-a072-1fbde65173b1/blizzard-end-user-license-agreement) includes restrictions on unauthorized data collection/mining, with an allowance at Blizzard's discretion for certain third-party user interfaces. We have not established authorization for a standalone metadata/texture extractor. Owning an installation, using read-only access and using an MIT-licensed library do not by themselves resolve that permission question or rights to distribute extracted content.

Verification limit: the addon-policy page was retrieved in full. Direct EULA retrieval returned HTTP 403; the data-mining clause was reviewed through indexed excerpts from Blizzard's own legal page. The user's applicable agreement/region, any newer terms and permissions for this exact design still need confirmation. This is a permission gap, not a finding that all local readers are prohibited.

## Recommendation and next evidence

Investigate an API-based metadata snapshot first for names and identifiers, while treating actual texture sourcing as separate work. Keep direct archive reading as a candidate pending permission and exact-build evidence. Neither route is selected yet.

Before selecting a route:

1. Confirm the first-release offline experience: whether a prior in-game metadata capture is acceptable and how incomplete metadata should appear.
2. Establish permission for the concrete access/export/display design, distinguishing personal local use from redistribution. If published terms do not resolve it, prepare a precise clarification request for the owner; no external message has been sent.
3. After the research/design gate permits a bounded validation task, verify a small representative set of names and icons for the intended build and locale. Do not install tools, write an addon or build a prototype merely to complete this discovery note.

No game process was controlled, no addon code was executed, no client archive was extracted, and no raw player data was shared. Application build, importer and metadata tests were not run because none were implemented for this research.
