# SavedVariables discovery

Related work: [Setup 5](https://github.com/worldofxobu/wow-offline-viewer/issues/1). Product boundary: [first-release scope](../planning/first-release-scope.md).

## Owner-reported provenance

On 2026-11-19, the owner confirmed that the existing local SavedVariables samples come from their WoW: Forever installation. Forever is the first-release target; Classic Era is deferred and Retail has no first-release support commitment.

Exact export date, client build, Altoholic version and DataStore module versions are unresolved. Current installed versions, when inspected, must not be assumed to prove which versions generated older samples.

## Verified local observations

On 2026-11-19, read-only text inspection found the following top-level table assignment names. No Lua was executed, no source files were changed, and no player values were emitted or copied here.

| Local file | Relevant observed assignment names |
| --- | --- |
| `DataStore.lua` | `DataStore_CharacterIDs`, `DataStore_CharacterGUIDs`, `DataStore_RealmNames` (among other tables). |
| `DataStore_Characters.lua` | `DataStore_Characters_Info`, `DataStore_Characters_GuildRanks`, `DataStore_Characters_Options`. |
| `DataStore_Crafts.lua` | `DataStore_Crafts_Characters`, `DataStore_Crafts_RecipeCategories`, `DataStore_Crafts_Reagents`, `DataStore_Crafts_ArcheologyItems`. |
| `Altoholic.lua` | Calendar, sharing, tooltip and UI option tables. |

Verification used .NET read-only text reads and an anchored regular expression for Altoholic/DataStore top-level table assignments. This is a structural inventory, not Lua syntax validation or evidence of the tables' meanings. Git checks confirmed the local sample directory is ignored and has zero tracked files.

## Evidence still needed

- Client/addon version metadata and reliable evidence of the versions that exported the samples.
- Matching addon source revision and decoder behavior: character identity joins, profession membership and recorded recipe representations.
- Required/optional input files and available display metadata; explicit failure behavior for missing or unsupported data.

No joins, packed recipe decoding, recipe completeness or supported version range have been established. Do not infer them from table names. Keep raw data local; shared examples must be synthetic or separately reviewed and sanitized.
