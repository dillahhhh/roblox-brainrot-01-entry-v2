# BRAINROT NUSANTARA

[![make.fun · roblox-brainrot-01](https://make.fun/badge/roblox-brainrot-01.svg)](https://make.fun/bounty/roblox-brainrot-01?utm_source=github&utm_medium=readme&utm_campaign=roblox-brainrot-01)
[![rank](https://make.fun/badge/roblox-brainrot-01/dillahhhh/roblox-brainrot-01-entry/rank.svg)](https://make.fun/bounty/roblox-brainrot-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=roblox-brainrot-01)
[![reward](https://make.fun/badge/roblox-brainrot-01/dillahhhh/roblox-brainrot-01-entry/reward.svg)](https://make.fun/bounty/roblox-brainrot-01?utm_source=github&utm_medium=readme&utm_campaign=roblox-brainrot-01)

A 3D brainrot game for the [roblox-brainrot-01 bounty](https://make.fun/bounty/roblox-brainrot-01) on make.fun: a Steal-a-Brainrot loop in an Indonesian night market (pasar malam) at dusk.

Brainrots parade across a central conveyor bridge — Tung Tung Sahur beating his kentongan, Es Teh Manis sloshing, Bajaj Biru spinning its wheels, Kuntilanak floating — you buy one, carry it home, and place it on your base where it earns $/s. Climb 6 rarity tiers (Common → Brainrot God) across 12 original characters, with Gold (x2), Diamond (x5) and Rainbow (x10) mutations.

The signature twist is **Pasar Tumpah**: every 3 minutes a flood wave sweeps the plaza, reroutes the conveyor, and washes unsecured brainrots away as loot crates in a scramble zone. What is already placed on your base is safe; everything on the conveyor or in your arms can wash away — and anyone brave enough to leave base after the wave can grab the crates.

## Status

Foundation (17 Nov 2026): Rojo project, plaza + 8 bases, catalog of 12 characters, conveyor spawn/walk/despawn, one movement system + one base animation system, single-source state (`BrainrotData`). Economy (buy/carry/earn/rebirth), Pasar Tumpah event, steal/lock/slap and the HUD come next.

## Layout

- `main.ts` (Node 22, standard library only) hands the game in: it copies `game.rbxl`, `src/`, `screenshots/` and `PLAY.json` to `/output`, leaving out every name that starts with a dot, and writes `/output/dossier.json` with `vendor/makefun-roblox.ts`, the kit's copy, unchanged.
- `game.rbxl` is the place Rojo builds from `src/` and `default.project.json`: `rojo build default.project.json --output game.rbxl`. Never run it over a place saved from Studio.
- `src/shared/` — `Config` (all tuning) and `BrainrotCatalog` (12 characters, tiers, mutations).
- `src/server/` — `Main.server.luau` + `services/`: `BrainrotData` (state in one place), `ConveyorService` (spawn/walk/models/animation), `BaseService` (8 cloned bases + slots), `EconomyService` / `StealService` / `EventService` (stubs for the next phases).
- `src/client/` — `Main.client.luau` + `controllers/`: `HudController`, `InteractController`, `EffectsController` (stubs for the next phases).
- `screenshots/` holds 3–4 captures of the game running in Studio; one of them is the game's first thumbnail on Roblox.
- `PLAY.json` names the published place (filled in once the experience is published on Roblox).

Run it as the grader does, writing `out/` in place of `/output`:

    mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts

The rules are on the bounty's page (https://make.fun/bounty/roblox-brainrot-01) and in the kit's RULES.txt, which gives every command in order (Before you submit, then Enter).
