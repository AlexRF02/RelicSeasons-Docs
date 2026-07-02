# Energy System

Energy is the main progression resource behind RelicSeasons. It controls how relics grow, how progression is paced, and how certain systems reward or punish player activity.

## Overview

Relic energy is designed to make progression feel active without allowing unlimited farming.

Players can gain energy through gameplay, lose energy through configured penalties, and use rituals or progression systems to stabilize their relic state.

!!! note
    Exact values are configurable. This page explains the concepts so server owners understand what each energy value represents.

## Main Energy Concepts

RelicSeasons uses several energy concepts internally.

| Concept | Meaning |
| --- | --- |
| Current Energy | The player's current visible relic energy. This is the value players usually notice changing during gameplay. |
| Natural Energy | The player's more stable progression value used by some progression and ritual systems. |
| Max Energy | The maximum energy a relic can hold at the current level. |
| Base Energy | The minimum or restored energy target for the current level, depending on the ritual/progression context. |

These values work together to prevent progression from feeling completely random. Players can still lose or gain energy, but the system has enough structure to support repair, progression, and level-based scaling.

## Current Energy

Current energy is the practical value players interact with most often.

It may change when:

- the player kills mobs
- the player kills another player
- the player dies
- an admin modifies energy
- rituals repair or modify relic state
- configured systems apply rewards or penalties

Current energy should never exceed the configured maximum energy for the player's current relic level.

## Natural Energy

Natural energy represents a more stable part of relic progression.

It is used by systems that need to understand the player's progression foundation rather than only the current momentary value.

For example, rituals and level-related systems may use natural energy to decide what a player's relic should be restored to, what their progression baseline is, or how a relic profile should behave after certain operations.

!!! tip
    As a server owner, treat natural energy as a progression baseline. Do not edit it casually unless you understand how your progression setup works.

## Max Energy

Max energy is the energy cap for the player's current relic level.

A low-level relic has a lower energy capacity than a high-level relic. This creates a sense of growth as players progress.

If a player is already at max energy, normal energy gains should not increase the value further.

## Base Energy

Base energy is the intended safe or restored energy point for a level.

This is especially important for repair-like behavior. A relic may be repaired back toward a base value without necessarily filling it to the maximum possible energy.

That distinction allows RelicSeasons to support different progression states:

- below base
- at base
- above base
- near maximum
- at maximum

## PvE Energy

PvE energy rewards players for fighting configured mobs.

The default design focuses on normal gameplay rather than exploit farming. Server owners can configure what counts as valid PvE energy gain.

Common options include:

- hostile mob energy gain
- passive mob behavior
- spawned mob filters
- daily or rolling caps
- anti-farm protections
- actionbar feedback when energy is gained

!!! warning
    Be careful when increasing PvE energy too much. High PvE rewards can make progression too fast and may reduce the value of rituals, PvP energy, and long-term server pacing.

## PvP Energy

PvP energy is used to reward or transfer energy when players fight.

This can make relic progression matter in player conflict while still respecting anti-farm systems and configured protections.

PvP energy should be tuned carefully. Too much reward can encourage abuse. Too little reward may make PvP feel disconnected from relic progression.

## Death And Environment Loss

RelicSeasons can apply energy changes when a player dies.

Depending on your configuration, death-related energy behavior may interact with:

- PvP kills
- environmental deaths
- revenge debt systems
- anti-farm tracking
- player progression state

The goal is to make energy meaningful without making death permanently destructive.

## Anti-Farm Protection

Anti-farm logic helps prevent players from repeatedly using the same targets or situations to gain energy unfairly.

This is especially important for PvP energy and any system where repeated player interaction could be abused.

## Energy Feedback

When a player gains energy, RelicSeasons can show feedback such as actionbar messages.

Feedback should generally appear only when energy actually changes. If the player is capped, blocked, or invalid for a gain, the plugin should avoid misleading messages.

## Admin Energy Management

Staff can modify energy through admin commands.

Typical actions include:

- set current energy
- add current energy
- remove current energy
- set natural energy
- add natural energy
- remove natural energy

See [Admin Commands](../commands/admin.md) for exact command syntax.

!!! warning
    Editing natural energy can affect progression more deeply than editing current energy. Use it carefully on production servers.

## Configuration Notes

Most energy values are configured from the main configuration and relic progression files.

Recommended tuning flow:

1. Start with the default balance.
2. Test progression with real gameplay.
3. Adjust PvE gains slowly.
4. Adjust PvP gains only after testing abuse cases.
5. Keep caps enabled.
6. Avoid changing multiple energy systems at the same time.

For the general configuration guide, see [Configuration](../configuration.md).
