# Rituals

Rituals are altar-based progression actions. They allow players to repair, ascend, or change relic progression through a physical in-world interaction.

## Overview

The Ritual system is designed to make important relic actions feel intentional.

Instead of being only a command or menu button, rituals require players to interact with a Relic Altar. This makes progression feel more immersive and gives servers a clear place for relic upgrades.

## Relic Altar

Rituals are performed through a physical Relic Altar.

A normal block is not automatically treated as a valid altar. RelicSeasons uses internal identity and registered altar data to know whether a clicked block is a real altar.

This helps prevent players from copying or faking altar behavior.

## Opening The Ritual Menu

Players open the ritual menu by interacting with a valid Relic Altar.

The normal RelicSeasons menu may show ritual information, but real ritual execution is designed to require an altar-backed session.

!!! note
    This prevents players from bypassing the altar requirement through a normal menu path.

## Ritual Actions

RelicSeasons can support several ritual actions.

| Ritual | Purpose |
| --- | --- |
| Repair | Restore relic energy toward the configured base value. |
| Ascension | Progress the relic to a higher level when requirements are met. |
| Resonant Ascension | Perform an advanced ascension using resonance-based requirements. |
| Change Relic | Change the player's current relic through an altar-based flow. |
| Status | Review ritual or relic-related information. |

The exact requirements and costs depend on your configuration.

## Repair Ritual

Repair is used when a relic is below its intended base energy for the current level.

It is not necessarily a full refill to maximum energy. This distinction matters because base energy and max energy are different concepts.

See [Energy System](energy.md) for the difference between current, natural, base, and max energy.

## Ascension Ritual

Ascension is used to progress a relic to a higher level.

A normal ascension usually requires the player to meet configured progression requirements such as energy or other costs.

After ascension, the player's relic state is updated according to the ritual rules.

## Resonant Ascension

Resonant Ascension is an advanced progression ritual.

It may require resonance instead of only normal energy or dust. This gives servers a separate path for special progression milestones.

## Change Relic

The Change Relic ritual allows a player to switch their current relic through the altar system.

This is designed to be more controlled than a simple command-based change. It helps protect progression balance while still allowing servers to support relic changes.

!!! warning
    Relic changing can affect player identity and progression balance. Configure its requirements carefully.

## Channeling

Rituals may use a short channeling period.

During channeling, the plugin can show countdown feedback and then apply the ritual after the final validation.

This protects the system from cases where a player starts a ritual and then their state changes before completion.

## Safety And Validation

Rituals should validate important conditions before applying results.

Examples:

- player still has the required relic state
- altar interaction is valid
- requirements are still met
- costs can still be consumed
- the target action is still allowed
- the player is not already running another ritual

This makes rituals safer for live servers.

## Altar Protection

Relic Altars can have break protection.

Server owners should decide who can place, break, or manage altar blocks. Administrative altar permissions should only be granted to trusted staff.

See [Permissions](../permissions.md) for permission nodes.

## Admin Ritual Tools

Staff can manage ritual-related state through admin commands.

Common actions include:

- give a Relic Altar item
- open a ritual menu for a player
- reset ritual cooldowns
- debug ritual state

See [Admin Commands](../commands/admin.md) for exact command syntax.

## Configuration Notes

Rituals are powerful progression tools.

Recommended setup:

1. Keep costs meaningful.
2. Do not make relic changing too cheap.
3. Test ascension pacing before release.
4. Use cooldowns if relic changing is available.
5. Place altars in intentional server locations.
6. Keep altar admin permissions restricted.

For general configuration structure, see [Configuration](../configuration.md).
