# SavedVariables discovery

Related work: [Setup 5](https://github.com/worldofxobu/wow-offline-viewer/issues/1). Product boundary: [first-release scope](../planning/first-release-scope.md).

## Owner-reported provenance

On 2026-11-19, the owner confirmed that the existing local SavedVariables samples come from their WoW: Forever installation. Forever is the first-release target; Classic Era is deferred and Retail has no first-release support commitment.

The sample export date and generating client/addon versions remain unresolved. The installed versions below do not prove which versions generated older samples.

## Verified installed metadata

Read on 2026-11-19 from the owner-identified local Forever installation, without launching the game or loading addon code:

| Component | Installed metadata | Evidence relative to the installation |
| --- | --- | --- |
| WoW: Forever | `1.60.1.70959` | `Wow.exe` file/product version; parent `.build.info` product `wowf` agrees. |
| Altoholic | `1.60.005`, interface `16001` | `Interface/AddOns/Altoholic/Altoholic.toc`. |
| DataStore | `2026.10.14`, includes interface `16001` | `Interface/AddOns/DataStore/DataStore.toc`. |
| DataStore_Characters | `2026.10.14`, includes interface `16001` | `Interface/AddOns/DataStore_Characters/DataStore_Characters.toc`. |
| DataStore_Crafts | `2026.10.14`, includes interface `16001` | `Interface/AddOns/DataStore_Crafts/DataStore_Crafts.toc`. |

These are a candidate compatibility baseline, not a tested support range. The TOCs' SavedVariables declarations match the observed sample root names. That agreement alone does not establish identical export versions or complete compatibility.

## Verified local observations

On 2026-11-19, read-only text inspection found the following top-level table assignment names. No Lua was executed, no source files were changed, and no player values were emitted or copied here.

| Local file | Relevant observed assignment names |
| --- | --- |
| `DataStore.lua` | `DataStore_CharacterIDs`, `DataStore_CharacterGUIDs`, `DataStore_RealmNames` (among other tables). |
| `DataStore_Characters.lua` | `DataStore_Characters_Info`, `DataStore_Characters_GuildRanks`, `DataStore_Characters_Options`. |
| `DataStore_Crafts.lua` | `DataStore_Crafts_Characters`, `DataStore_Crafts_RecipeCategories`, `DataStore_Crafts_Reagents`, `DataStore_Crafts_ArcheologyItems`. |
| `Altoholic.lua` | Calendar, sharing, tooltip and UI option tables. |

Verification used .NET read-only text reads and an anchored regular expression for Altoholic/DataStore top-level table assignments. This is a structural inventory, not Lua syntax validation or evidence of the tables' meanings. Git checks confirmed the local sample directory is ignored and has zero tracked files.

## Relationships established from installed addon source

The following describe the inspected source snapshot, not an executed import of the samples:

1. `DataStore/DataStore.lua:149` builds an account/realm/character key. Its character accessors map that key through `DataStore_CharacterIDs.Set` to an integer ID, and back through `List`. Keep identity separate from display names.
2. `DataStore/API/Core.lua:77` dispatches character methods by indexing each registered character table with that same ID. This links `DataStore_Characters_Info[id]` and `DataStore_Crafts_Characters[id]`.
3. `DataStore_Crafts/API/Common.lua:76` exposes the craft character's `Professions` table. `Indices[name]` identifies a profession entry; `Ranks[index]` packs current rank in the low 16 bits and maximum rank above it.
4. The Forever TOC loads `DataStore_Crafts_Retail.lua`. `AddonFactory/Core/Tools.lua:131` classifies interface `16001` as Forever and mainline. Do not choose a legacy decoder from a filename or the word Classic alone.
5. The mainline recipe path stores category-indexed `profession.Crafts` entries. `DataStore_Crafts_Retail.lua:830` decodes difficulty from bits 0–1, learned status from bit 2, recipe rank from bits 3–4, total ranks from bits 5–6 and recipe ID from bits 7 upward. This source-derived layout still needs synthetic contract tests and validation against the intended sample family before implementation claims.

### Display metadata limitation

`DataStore_Characters/DataStore_Characters.lua:157` reads the saved character name and extracts level/class/race IDs from `BaseInfo`; localized class/race names are resolved through game APIs. Professions save a `Name` value. `Altoholic_Characters/Frames/Recipes.lua:96` resolves recipe names through `C_Spell.GetSpellName`, rather than a saved recipe-name dictionary in the inspected recipe representation.

Consequently, an offline viewer needs an agreed metadata source or explicit missing-name behavior. Whether another local table supplies enough metadata remains unverified. Recorded recipes may include entries marked unlearned; this does not establish a complete missing-recipe catalog.

The owner prefers local metadata when feasible and permitted. [Local metadata options](local-metadata-options.md) record the investigation of in-game API snapshots and client archives, including texture and permission limits. Neither route is approved.

### Reproducible source identity

Paths below are relative to `Interface/AddOns/`. SHA-256 fingerprints identify the installed source inspected on 2026-11-19; they are not upstream commit IDs. No addon source or assets were copied into this repository. The inspected `DataStore/License.txt` states all rights reserved; source inspection does not establish redistribution permission.

| Source | SHA-256 |
| --- | --- |
| `AddonFactory/Core/Tools.lua` | `aaa764279a1ea246695867477c43a2ef44252e68d0b39c3dbe35783e2a21fb98` |
| `DataStore/DataStore.lua` | `2017f3036d7a1819fa16ca3b166d646be9e3bf963e0b441a6c68d2abeb8c6184` |
| `DataStore/API/Core.lua` | `454f8d74744c7befd4453f361d82ab08ede48a3faf40dc9559468138d5fe8eb1` |
| `DataStore_Characters/DataStore_Characters.lua` | `9860c953024bcd85fb6f831fc084a2b9792e8ab66db396b171d695a3ad92f7c8` |
| `DataStore_Crafts/API/Common.lua` | `1179544e5076adb6c0b46a2df040e8faab604cea835f58c47cd4063ba71f0a9e` |
| `DataStore_Crafts/DataStore_Crafts_Retail.lua` | `45183f0b72cc3fe862347f81752e615b7be31ed77c3d79b73a60f13e0e43701f` |
| `DataStore_Crafts/DataStore_Crafts.toc` | `23284967b4c6205dee58e25108e268ee82c9978d234cbd9c3c5b0d1a88ecca36` |

## Evidence still needed

- Reliable evidence of the versions that exported the samples, and confirmation that their nested structure matches this source snapshot.
- Candidate minimum input set: `DataStore.lua`, `DataStore_Characters.lua` and `DataStore_Crafts.lua`. Validate required/optional tables and cross-file IDs; do not require UI options merely because Altoholic produces them.
- A metadata source with suitable availability and licensing, and explicit missing-name behavior.
- Supported format detection and behavior for missing, stale, partially updated or unsupported data; synthetic fixtures and contract tests belong to the reviewed feature work.

No application importer or decoder has been implemented or tested. Recipe completeness and the supported version range remain unverified. Keep raw data local; shared examples must be synthetic or separately reviewed and sanitized.
