# Cosmetics

Cosmetics provide visual identity and reward options for players without changing the core relic progression balance.

## Overview

RelicSeasons cosmetics are selectable, permission-based options.

A player can unlock cosmetics through permissions, then manually select the cosmetic they want to use. Having permission does not automatically activate a cosmetic.

This keeps cosmetics controlled and predictable.

## Cosmetic Categories

RelicSeasons can support multiple cosmetic categories.

| Category | What It Controls |
| --- | --- |
| Kill Messages | Message style when a player kills another player. |
| Mob Death Messages | Message style when a player dies to a mob or entity. |
| Environment Death Messages | Message style when a player dies to the environment. |
| Projectile Trails | Particle trail behind supported projectiles. |
| Mob Kill Effects | Particle effect when a player kills a mob. |
| Kill Effects | Particle effect when a player kills another player. |
| Death Effects | Particle effect when the player dies. |
| Auras | Ambient particle effect around the player. |

## Vanilla Option

Each category should have a default or vanilla option.

If a player has not selected a cosmetic, loses permission, or has an invalid selected cosmetic, RelicSeasons should fall back safely instead of breaking the player experience.

This means server owners can remove or change cosmetics without permanently corrupting player selections.

## Permission-Based Unlocks

Cosmetics are unlocked through permissions.

A player must have the required permission for a cosmetic before it can be used.

Permissions may be granted individually or through wildcard nodes, depending on your permission plugin setup.

See [Permissions](../permissions.md) for the available permission structure.

## Selection Persistence

Cosmetic selections are saved.

When a player selects a cosmetic, RelicSeasons remembers that choice so the player does not need to reselect it every time they join.

If the player later loses permission, the selected value may remain stored, but runtime behavior should fall back to vanilla until permission is restored.

## Messages

Message cosmetics control death or kill message styling.

These messages can use configured text and placeholders depending on the message type.

Examples of message categories:

- player kills player
- player dies to a mob
- player dies from environment damage

!!! tip
    Keep message cosmetics readable. Very long death messages can become annoying on active servers.

## Particles

Particle cosmetics control visual effects such as trails, bursts, deaths, and auras.

Examples of particle-based categories:

- projectile trails
- kill effects
- mob kill effects
- death effects
- auras

Particle cosmetics should be tested in real server conditions. Too many high-frequency particles can affect visibility or performance.

## Configuration And Language

Cosmetic behavior and cosmetic text are configured separately.

In general:

- technical cosmetic settings define behavior, permissions, and particle IDs
- language files define visible names, lore, and messages
- menus define how options are displayed to players

This separation makes it easier to translate cosmetics without changing their technical behavior.

See [Translations](../translations.md) for language editing.

## Invalid Cosmetics

A cosmetic should be considered invalid if required configuration or language data is missing.

When this happens, the safest behavior is to avoid applying the cosmetic and fall back to vanilla behavior.

This is useful when server owners are editing files and accidentally remove a name, message, permission, or particle setting.

## Recommended Usage

Cosmetics are best used as rewards.

Good unlock sources include:

- ranks
- crates
- events
- seasonal rewards
- quests
- store perks
- limited-time achievements

!!! warning
    Cosmetics should not create gameplay advantages. Keep them visual and identity-focused.

## Admin And Staff Notes

Staff should test every cosmetic after editing configuration.

Recommended checklist:

1. Select the cosmetic in-game.
2. Trigger the relevant event.
3. Check console for warnings.
4. Confirm the fallback works when permission is removed.
5. Verify the language text looks correct.

For general configuration structure, see [Configuration](../configuration.md).
