# Relics

Relics are the core identity and progression system of RelicSeasons. Each player owns one main relic, progresses it over time, and uses it as the foundation for energy, rituals, fragments, cosmetics, and other server systems.

## What Relics Do

A relic is more than a simple item. It represents the player's progression path.

Relics can provide:

- a unique gameplay identity
- a main relic item
- an active ability
- progression levels
- energy requirements
- menu information
- ritual interaction
- compatibility with fragments and cosmetics

!!! note
    Exact values, ability numbers, cooldowns, and scaling are controlled by configuration files. This page explains the system from a player and server-owner perspective.

## Default Relic Themes

RelicSeasons includes a default set of relic identities designed around different fantasy themes.

| Relic Theme | General Identity |
| --- | --- |
| Flame | Aggressive fire-themed progression |
| Frost | Slowing, control, and ice-themed gameplay |
| Storm | Lightning, mobility, and burst-style identity |
| Shadow | Stealth, darkness, and assassin-style identity |
| Void Ender | Ender, void, and teleport-style identity |
| Titan | Defensive, heavy, and strength-based identity |
| Druid | Nature, growth, and life-themed identity |
| Blood | Risk, sustain, and blood-themed identity |

The exact behavior of each relic depends on your server configuration.

## First Relic Selection

When first-join relic selection is enabled, new players are offered a limited set of relic choices instead of receiving a random permanent choice automatically.

This helps players understand that their relic is an important long-term decision.

Typical behavior:

1. A new player joins the server.
2. RelicSeasons offers a small selection of relics.
3. The player chooses one relic.
4. The selected relic becomes their current main relic.
5. The player can then use normal RelicSeasons menus and progression systems.

!!! tip
    Server staff can use the admin commands to open, reroll, or assign first relic selection for players when needed.

## Relic Core

The Relic Core is the player's main relic item.

It is used by RelicSeasons to identify the player's relic state and connect the player to the relic system. The plugin protects this item using internal identity data, not only the visible item name or lore.

This means a renamed or copied item should not be treated as a valid Relic Core unless it was created by RelicSeasons.

## Menu Activator

RelicSeasons can give players a menu activator item.

The activator is designed as a quality-of-life item for opening the RelicSeasons menu quickly. When a player is not fully bound to a relic yet, the activator can direct them to the first relic selection flow instead.

!!! note
    The activator is separate from active relic ability usage. Opening the menu should not accidentally trigger an ability.

## Active Abilities

Each relic can have an active ability.

Active abilities are part of the relic identity and are normally used through the appropriate relic interaction or command, depending on server setup.

Important behavior:

- abilities should only work when the player has a valid relic state
- cooldowns and costs are handled by the plugin
- blocked or invalid ability usage should not consume resources
- protected regions may block some ability effects if WorldGuard integration is enabled

See [WorldGuard](../integrations/worldguard.md) for region protection behavior.

## Relic Progression

Relics progress through levels.

By default, RelicSeasons is configured around a public progression range up to level 9, while the technical hard cap is designed up to level 20.

!!! warning
    Levels above the configured hard cap are not supported by default. Extending the system beyond the supported cap may require future plugin support, menu changes, and additional configuration work.

Progression is mainly connected to energy. Players gain, lose, repair, and spend energy through several systems.

For more details, see [Energy System](energy.md).

## Per-Relic Progress

RelicSeasons can preserve progression information per relic.

This is important because a player may interact with systems that change their current relic, such as ritual-based relic change. A server can therefore keep relic identity and progression more controlled than a simple one-time item swap.

## Admin Notes

Server staff can manage relic state through admin commands.

Common staff actions include:

- assign a relic to a player
- set a relic level
- repair or restore a Relic Core
- debug a player's relic state
- manage first relic selection

See [Admin Commands](../commands/admin.md) for the command list.

## Configuration Notes

Relic behavior is configured through the generated RelicSeasons files.

Most servers should start with the default balance and make small changes gradually.

Recommended approach:

1. Test the default setup first.
2. Change one relic value at a time.
3. Reload or restart safely.
4. Check the console for validation warnings.
5. Test the relic in-game before releasing the change to players.

See [Configuration](../configuration.md) for the general configuration guide.
