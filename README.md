# AGTH Dino World — ARK: Survival Ascended Server Config

Nitrado crossplay server config for **AGTH Dino World** (PS5 + Xbox co-op).  
Tracked with Git so tweaks are easy to review, revert, and share.

## Structure

```
config/
├── Game.ini            # Core gameplay multipliers, breeding, XP, etc.
└── GameUserSettings.ini  # (add when needed)
```

## Quick reference — current tuning philosophy

| Category | Setting | Notes |
|---|---|---|
| **Breeding** | Mating interval `0.1x`, hatch `10x`, mature `10x` | Fast breeding loop |
| **Imprinting** | Cuddle interval `0.1x`, imprint amount `4x` | Easy 100% imprint |
| **XP** | Most kills/harvest/craft at `2x`, Boss kills `5x` | Accelerated progression |
| **Harvesting** | Dino harvesting damage `1.5x` | Slightly boosted yields |
| **Spoilage** | Spoiling time `1.75x`, decomp `2x` | More breathing room |
| **Crops** | Growth `3x`, decay `2x` | Fast farms |
| **Structure** | Collision placement disabled, unlimited respecs | QoL |
| **Speed leveling** | Enabled for both ground and flyers | |

## How to apply changes

1. Edit the relevant `.ini` file locally
2. Commit with a descriptive message, e.g. `git commit -m "increase BabyMatureSpeedMultiplier to 15"`
3. Upload the updated file to Nitrado via the file manager or FTP
4. Restart the server

## Reverting a change

```bash
# See recent commits
git log --oneline

# Revert a specific file to a previous commit
git checkout <commit-hash> -- config/Game.ini
```
