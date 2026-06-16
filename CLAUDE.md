# AGTH Dino World — ARK: Survival Ascended Server Config

Private crossplay PvE server hosted on Nitrado. Players: PS5 + Xbox (no PC).
Server name: **AGTH Dino World**

## Repo layout

```
config/
├── Game.ini              # Core gameplay: breeding, XP, harvesting, crop, spoil
└── GameUserSettings.ini  # Server settings, graphics/UI (passwords blanked as "")
```

`GameUserSettings.ini` has multiple sections — edits must land under the correct header:
- `[ServerSettings]` — taming speed, harvest, player/dino stats, structure rules
- `[SessionSettings]` — server name
- `[MessageOfTheDay]` — login message
- `[/Script/ShooterGame.ShooterGameMode]` (in `Game.ini`) — breeding, XP, imprinting, spoil

## Current tuning snapshot

| Category | Key settings |
|---|---|
| Taming | `TamingSpeedMultiplier=5` |
| Breeding | `MatingIntervalMultiplier=0.1`, `EggHatchSpeedMultiplier=10`, `BabyMatureSpeedMultiplier=10` |
| Imprinting | `BabyCuddleIntervalMultiplier=0.1`, `BabyImprintAmountMultiplier=4`, `AllowAnyoneBabyImprintCuddle=true` |
| XP | Kill/harvest/craft/generic/special/explorer/alpha/wild/cave all `2x`; boss kills `5x`; tamed kills `0.25x` |
| Harvesting | `HarvestAmountMultiplier=3` (GameUserSettings), `DinoHarvestingDamageMultiplier=1.5` (Game.ini) |
| Loot quality | Supply crate and fishing loot `2x` |
| Spoilage | `GlobalSpoilingTimeMultiplier=1.75`, item/corpse decomp `2x` |
| Crops | Growth `3x`, decay `2x`, lay egg interval `0.75x` |
| Player QoL | Food/water drain `0.5x`, `bAllowUnlimitedRespecs=true`, `bDisableStructurePlacementCollision=true` |
| Speed leveling | Enabled for ground dinos and flyers |
| Dino health regen | `DinoCharacterHealthRecoveryMultiplier=1.5` |
| Cryopods | Cryo sickness disabled in PvE, fridge requirement disabled |
| Max tamed dinos | 5000 (soft + hard limit) |
| Auto-save | Every 10 minutes |

## Workflow for changes

1. Edit the relevant `.ini` file
2. Commit: `git commit -m "<short description of what changed and why>"`
3. Upload changed file to Nitrado via file manager or FTP (path: `ShooterGame/Saved/Config/WindowsServer/`)
4. Restart the server from the Nitrado dashboard

## Reverting

```bash
git log --oneline                              # find the commit to go back to
git checkout <hash> -- config/Game.ini        # restore a specific file
```

## Secrets / passwords

`ServerAdminPassword` and `ServerPassword` are blanked as `""` in this repo — the repo is public.
Never commit real passwords here.

## What NOT to touch without understanding

- `BabyImprintingStatScaleMultiplier` — controls how much imprint boosts stats (currently `1`, vanilla)
- `OverrideOfficialDifficulty=5` — sets max wild dino level to 150; changing affects loot tiers
- Bunker settings (`LimitBunkersPerTribe`, etc.) — left over from default template, server is PvE so largely inert
- `[Startup]` / `[ScalabilityGroups]` in GameUserSettings — graphics quality, not gameplay
