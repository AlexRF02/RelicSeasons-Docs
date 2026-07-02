# Fragments

Fragments are secondary relic progression items. They allow players to interact with additional relic-themed bonuses without replacing their main relic identity.

## Overview

A player has one main relic, but fragments can add temporary or secondary progression layers.

Fragments are designed to create more build variety while keeping the main relic system controlled.

## Fragment States

Fragments can exist in different states.

| State | Meaning |
| --- | --- |
| Pending | The fragment has been obtained but is not currently active. |
| Active | The fragment is currently applied to the player. |
| Expired or Removed | The fragment is no longer active or has been cleared by a system/admin action. |

Pending and active states help prevent confusion. Players can receive fragments, review them, and then manage them through the appropriate menu.

## Pending Fragments

Pending fragments are fragments waiting to be activated.

A pending fragment may appear after a reward, admin action, or configured system interaction.

Players can review pending fragments before activating them. This is useful because an active fragment slot may be limited.

## Active Fragments

Active fragments are currently affecting the player.

Depending on your configuration, active fragments may:

- provide a benefit
- apply a weakness
- last for a limited duration
- use active fragment slots
- interact with relic identity

RelicSeasons is designed to prevent duplicate active fragments of the same relic type when that would break balance.

## Fragment Slots

Servers can control how many active fragments a player may use.

The default permission setup can grant additional fragment access through permission nodes.

For example, a server may allow normal players to use one slot and grant extra slots to ranks or special groups.

See [Permissions](../permissions.md) for the available permission nodes.

## Fragment Duration

Fragments may have a configured duration.

A duration-based fragment should expire naturally after its configured time. This allows server owners to create powerful secondary effects without making every reward permanent.

## Relic Dust

Relic Dust is a fragment-related resource.

It can be used by fragment systems depending on your configuration and menu setup. Server owners can use dust as a way to connect fragments to economy, rewards, or long-term progression.

!!! note
    The exact dust usage depends on your server configuration and enabled fragment features.

## Resonance

Resonance is connected to advanced relic progression and ritual behavior.

It can be used by systems that require a special progression condition instead of only energy or level requirements.

For example, a ritual may require resonance before allowing a special type of ascension.

See [Rituals](rituals.md) for altar-based progression.

## Fragment Menus

Players can manage fragments through RelicSeasons menus.

Typical menu actions may include:

- view active fragments
- view pending fragments
- activate a pending fragment
- review gains and weaknesses
- check remaining duration
- inspect fragment-related resources

## Admin Fragment Management

Staff can manage fragments through admin commands.

Common actions include:

- give a physical fragment item
- create a pending fragment
- create an active fragment
- add dust
- clear fragments
- set resonance

See [Admin Commands](../commands/admin.md) for exact command syntax.

## Configuration Notes

Fragments are balance-sensitive.

Recommended approach:

1. Keep default values for the first test period.
2. Avoid giving too many active slots.
3. Make strong fragments temporary.
4. Use weaknesses to balance powerful gains.
5. Test fragment stacking with every relic.
6. Watch for PvP abuse if fragments affect combat.

For general configuration structure, see [Configuration](../configuration.md).
