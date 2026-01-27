# The Great Plain Plan — Project Context

## Project Type
2D roguelike / strategy / physics-inspired arcade game.

## Platforms
- Primary: PC (Steam)
- Planned: Steam Deck, Consoles (PlayStation, Xbox)

## Core Fantasy
Optimize each hero launch by combining team composition, numeric modifiers, and in-flight decisions to reach increasingly distant checkpoints on a board-like map.

## High-Level Core Loop
1. Press Start
2. Main Menu
3. Play
4. Select Map
5. Select Heroes (team-based)
6. Launch hero
//Launchers are an abstract system (slingshot/catapult metaphor), not physical weapons.
They exist to modify the initial launch parameters of the hero and are defined purely by stats and passives.//
8. Mid-air decisions (skills, resources)
9. Land on board tile
10. Apply tile effects
11. Repeat until checkpoint reached or run fails

---

## Main Menu Structure

### Main Menu Options
- Play
- Profile
- Options
- Language
- Exit

### Play Flow
- Play → Select Map → Select Heroes (team-based)

### Profile
- Create / Select profile
- Required for online features (post-MVP)
- Local profiles supported in MVP

### Options
- Graphics
- Sound
- Controller

### Language
- Change game language

### Exit
- Confirmation popup:
  - "Are you sure?"
  - Options: Yes / No
  - Yes → Close game
  - No → Return to menu

---

## Run Structure
- Start position: Tile 0
- Distance conversion: 1000m = 1 tile
- <1000m = remains on Tile 0
- Checkpoints: 10 / 20 / 30 / 40
- Each hero can be launched once per checkpoint
- Limited number of launches per run

## Fail Conditions
- Failure to reach next checkpoint
- No remaining heroes
- Both conditions combined

## Gameplay vs Meta
- Launch & flight = real-time gameplay
- Board map = strategic/meta layer
- Board is not real-time gameplay

## Roguelike Principles
- Procedural / semi-random runs
- Permanent unlocks via progression only
- No external meta shops (no Burrito-style stores)

## Physics Philosophy
- Deterministic pseudophysics
- No Rigidbody-based simulation
- Hard caps on:
  - Max speed
  - Max height
  - Max flight duration

## Multiplayer (Post-MVP)

Multiplayer is competitive, asynchronous-synchronous hybrid.

### Online Multiplayer (Shadow Mode)
- Players play the same map and run simultaneously.
- Each player sees a "shadow" (ghost) of the other player’s hero during flight.
- Shadows are non-interactive and purely informational.
- No direct interference during flight.

### Turn & Decision Priority
- The player who lands first on a tile:
  - Resolves the tile interaction first
  - Makes decisions while the other player waits
- Second player resolves their interaction after the first finishes.

### Auctions & Competition
- Auctions occur:
  - Before the run (heroes, items)
  - Between launches (items, modifiers)
- Players bid using shared or comparable currencies.
- Auctions are turn-based and blocking (both players must resolve).

### Win Condition
- Player who reaches farther tiles faster gains advantage.
- Progression comparison is distance-based, not score-based.

### Hot Seat Mode
- Turn-based on a single device.
- Players alternate:
  - Launch
  - Tile resolution
  - Auctions
- Identical ruleset to online multiplayer without networking.

### MVP Status
- Multiplayer is NOT part of MVP.
- Architecture and systems must remain deterministic and replayable.
- No system should assume single-player-only state ownership.

Status: NOT part of MVP, but architecture should not block it.

## Workflow Rules
- GitHub repository is the single source of truth
- Chat is only an interface
- Every new chat starts with:
  - Repo link
  - Short project snapshot (10–15 lines)
