# Permissions

This page lists the permission nodes used by RelicSeasons.

Use your permissions plugin, such as LuckPerms, to assign these nodes to players, groups, or staff roles.

!!! tip
    Only grant admin permissions to trusted staff. Some admin commands can modify player relics, energy, fragments, weekly curses, ritual state, or plugin configuration.

## Player Permissions

These permissions are intended for normal players or ranked groups.

| Permission | Description |
| --- | --- |
| `relicseasons.command.relic` | Allows players to use `/relic` and `/relics`. |
| `relicseasons.weekly_curses.vote` | Allows players to vote in the Weekly Curse system. |
| `relicseasons.weekly_curses.vote.weight.5` | Gives the player a vote weight of 5 when voting for Weekly Curses. |
| `relicseasons.weekly_curses.vote.weight.10` | Gives the player a vote weight of 10 when voting for Weekly Curses. |
| `relicseasons.fragments.use` | Allows players to use Secondary Fragment features. |
| `relicseasons.fragments.slots.2` | Allows players to use two active Secondary Fragment slots, if enabled by configuration. |
| `relicseasons.fragments.duration.48h` | Gives players access to the 48-hour Secondary Fragment duration, if enabled by configuration. |

## Admin Permissions

The main admin permission is:

```text
relicseasons.admin
```

RelicSeasons checks `relicseasons.admin` before processing `/relicseasons` or `/rs` subcommands. Specific admin permissions are checked afterwards, but they are not enough by themselves without `relicseasons.admin`.

| Permission | Description |
| --- | --- |
| `relicseasons.admin` | Main staff permission for RelicSeasons admin commands and admin access. |
| `relicseasons.admin.reload` | Allows reloading RelicSeasons. |
| `relicseasons.admin.debug` | Allows debug-related admin commands. |
| `relicseasons.admin.core` | Allows relic core repair or restore admin actions. |
| `relicseasons.admin.energy` | Allows current and natural energy admin actions. |
| `relicseasons.admin.level` | Allows relic level admin actions. |
| `relicseasons.admin.relic` | Allows changing a player's relic. |
| `relicseasons.admin.selection` | Allows first relic selection admin actions. |
| `relicseasons.admin.activator` | Allows Menu Activator debug or repair admin actions. |
| `relicseasons.admin.altar` | Allows Relic Altar admin actions. |
| `relicseasons.admin.altar.break` | Allows protected Relic Altar break interactions, depending on configuration. |
| `relicseasons.admin.ritual` | Allows ritual-related admin actions. |
| `relicseasons.admin.curse` | Allows Weekly Curse admin actions. |
| `relicseasons.fragments.admin` | Allows Secondary Fragment admin actions. |

!!! note
    The admin item in the main menu uses `items.admin.permission` from `menus/main.yml`. If that value is not configured, it falls back to `relicseasons.admin`.

## Cosmetic Permissions

Cosmetics are unlocked by permission. Granting a cosmetic permission makes it available to the player, but it does not force-enable it. Players still select cosmetics manually from the cosmetics menu.

### Global Cosmetic Permission

| Permission | Description |
| --- | --- |
| `relicseasons.cosmetics.*` | Unlocks all cosmetic categories and cosmetics. |

### Category Wildcards

| Permission | Description |
| --- | --- |
| `relicseasons.cosmetics.kill_message.*` | Unlocks all player kill messages. |
| `relicseasons.cosmetics.mob_death_message.*` | Unlocks all mob death messages. |
| `relicseasons.cosmetics.environment_death_message.*` | Unlocks all environment death messages. |
| `relicseasons.cosmetics.projectile_trail.*` | Unlocks all projectile trails. |
| `relicseasons.cosmetics.mob_kill_effect.*` | Unlocks all mob kill effects. |
| `relicseasons.cosmetics.kill_effect.*` | Unlocks all player kill effects. |
| `relicseasons.cosmetics.death_effect.*` | Unlocks all death effects. |
| `relicseasons.cosmetics.aura.*` | Unlocks all auras. |

### Cosmetic IDs

Relic-themed cosmetic IDs:

```text
blood
flame
frost
storm
shadow
void
titan
druid
```

Additional visual cosmetic IDs:

```text
hearts
music
magic
end_rod
crit
witch
soul
firework
cloud
ink
```

Additional message cosmetic IDs:

```text
butcher
assassin
hunter
executioner
duelist
reaper
royal
toxic
clean_hit
humiliation
```

### Examples

```text
relicseasons.cosmetics.kill_message.blood
relicseasons.cosmetics.kill_effect.firework
relicseasons.cosmetics.projectile_trail.end_rod
relicseasons.cosmetics.aura.shadow
```

## LuckPerms Examples

Give normal players access to the main command:

```text
/lp group default permission set relicseasons.command.relic true
```

Give a VIP group access to all projectile trails:

```text
/lp group vip permission set relicseasons.cosmetics.projectile_trail.* true
```

Give a staff group access to RelicSeasons admin commands:

```text
/lp group admin permission set relicseasons.admin true
/lp group admin permission set relicseasons.admin.reload true
/lp group admin permission set relicseasons.admin.debug true
```

## Notes

- `/relic` and `/relics` use `relicseasons.command.relic`.
- `/relicseasons` and `/rs` require `relicseasons.admin` before subcommand-specific permissions are checked.
- Cosmetic permissions may be declared by configuration instead of `plugin.yml`.
- Debug-only or deprecated internal permissions are not listed here as public permissions.
