# Configuration

RelicSeasons is designed to work out of the box with a balanced default setup. Most servers can install the plugin, review the generated files, and start testing without changing every value immediately.

This page explains how the main configuration files are organized, what the most important values mean, and which settings should be changed carefully.

!!! tip
    For a first test server, keep the default configuration and only change language, permissions, menu visuals, and small balance values after you understand how your players interact with the plugin.

## Configuration Files

RelicSeasons generates its files inside the plugin folder:

```text
plugins/RelicSeasons/
├─ config.yml
├─ relics/
├─ menus/
├─ lang/
├─ cosmetics.yml
├─ weekly-curses.yml
└─ relicseasons.db
```

The exact file list can change depending on the installed version and which systems have already generated their defaults.

### `config.yml`

`config.yml` contains global plugin behavior:

- language selection
- storage settings
- first relic selection
- energy and progression caps
- PvP/PvE energy rules
- weekly curse rotation
- item protection
- Menu Activator settings
- WorldGuard integration settings
- debug flags

This is the main file server owners should review first.

### `relics/`

Relic files control the balance of each official relic. These files are used for values such as passive stats, active ability values, weaknesses, scaling, durations, radius, damage, cooldown-like values, and other relic-specific tuning.

Do not confuse these files with the wiki page about the Relics feature. The configuration files are only for tuning values. The actual relic systems are built into the plugin.

### `menus/`

Menu files control inventory layouts, slots, materials, sounds, and menu-specific options.

Visible text such as names, lore, and titles is handled by language files, not directly inside modern menu files.

### `lang/`

Language files control player-facing text. RelicSeasons currently includes English and Spanish language support, and server owners can edit the generated files to match their server style.

See the Translations page for a deeper explanation.

## Recommended Editing Flow

For safe production changes:

1. Stop the server.
2. Back up `plugins/RelicSeasons/`.
3. Edit the desired file.
4. Start the server.
5. Check console warnings.
6. Test the affected feature in-game.

During testing, many text and menu changes can be checked with:

```text
/rs reload
```

!!! warning
    Reloading is useful while configuring, but full restarts are safer for production balance changes, storage changes, integration changes, and major progression edits.

## Configuration Safety

The `config_safety` section controls how RelicSeasons handles missing or outdated keys.

Common defaults include:

```yaml
config_safety:
  auto_add_missing_keys: true
  backup_before_auto_update: true
  auto_fix_invalid_values: false
  warn_unknown_keys: true
```

Recommended behavior:

- Keep automatic backups enabled.
- Keep missing-key repair enabled.
- Do not rely on automatic fixes for balance mistakes.
- Read console warnings after updates.

Unknown keys usually mean that a value was renamed, removed, misspelled, or copied from an older version.

## Language Selection

The active language is selected in `config.yml`:

```yaml
language:
  active: "en_US"
```

For Spanish:

```yaml
language:
  active: "es_ES"
```

After changing the active language, restart the server or use:

```text
/rs reload
```

Changing language with reload is useful for testing, but a full restart is recommended before production use because players may already have menus open, temporary messages active, or cached UI state from the previous language.

## Storage

By default, RelicSeasons uses SQLite:

```yaml
storage:
  type: sqlite
  sqlite-file: relicseasons.db
```

SQLite is simple and recommended for most single-server SMP setups.

!!! warning
    Do not manually edit the database while the server is running. Stop the server first and always keep a backup.

## First Join Selection

The first join selection system controls how new players choose their first relic.

Example values:

```yaml
first_join_selection:
  enabled: true
  mode: RANDOM_CHOICES
  choices: 3
  save_choices_until_selected: true
  open_on_first_join: true
  close_behavior: KEEP_UNBOUND
```

Default behavior:

- new players receive a random set of relic choices
- choices are saved until the player selects one
- closing the menu does not force a relic
- using `/relic` can reopen the selection if the player is still unbound

This is recommended for normal SMP gameplay because it gives players an important first decision without overwhelming them with every relic immediately.

## Progression Limits

RelicSeasons currently has two important progression caps:

```yaml
progression:
  hard_max_level: 20
  enabled_max_level: 9
```

### Enabled Max Level

`enabled_max_level` is the active progression cap. By default, official relic progression is enabled up to level `9`.

This means players are expected to progress through the balanced public range of the plugin without immediately using every technical level that exists in the configuration.

### Hard Max Level

`hard_max_level` is the technical upper limit currently supported by the plugin configuration and menu logic.

The generated configuration contains energy entries up to level `20`, but levels above the enabled cap should be treated as advanced or future-ready configuration.

!!! warning
    Do not configure progression above level `20` in the current version. Higher custom level counts are planned for a future update, but they are not currently supported as a normal public configuration path.

## Energy Basics

Energy is one of the most important systems in RelicSeasons. The configuration uses several related values, and changing them without understanding the difference can make progression too fast, too slow, or unstable.

### Current Energy

Current Energy is the player's active usable energy value. It is the value most directly affected by gameplay events such as energy gain, energy loss, PvP transfer, PvE rewards, ability costs, and regeneration.

### Natural Energy

Natural Energy represents the player's underlying progression state for their relic. It is used by progression displays and long-term relic progression logic.

In simple terms:

- Current Energy is the active value players feel moment to moment.
- Natural Energy is the progression value that represents where the relic sits in its level band.

### Maximum Energy

Each level has a configured maximum energy value:

```yaml
energy:
  natural_energy_by_level:
    1:
      max: 100
      default_on_unlock: 50
    2:
      max: 200
      default_on_unlock: 150
```

`max` is the maximum energy for that level.

A player at level `2` with default values has a level band that can reach `200` energy.

### Base Energy / Default On Unlock

`default_on_unlock` is the base energy value assigned when a level is unlocked.

With the default level `2` values:

```yaml
2:
  max: 200
  default_on_unlock: 150
```

A player who reaches level `2` starts from a base of `150` energy and can progress toward `200` within that level band.

This is important because many progression and loss systems are designed around the idea that each level has a stable base value and a maximum value.

### Energy Band Size

The default setup uses a clean progression band:

```yaml
energy:
  energy-band-size: 100.0
```

The generated level table follows this structure:

```text
Level 1:  50 / 100
Level 2: 150 / 200
Level 3: 250 / 300
...
Level 9: 850 / 900
```

This makes progression easy to read and easy to balance.

## PvP Energy Loss And Transfer

The `death_energy.pvp` section controls what happens when a player dies to another player.

Important values include:

```yaml
death_energy:
  pvp:
    enabled: true
    percent: 10.0
    minimum_loss: 5
    victim_loses_energy: true
    killer_absorbs_energy: true
    allow_level_downgrade: true
```

With default-style settings:

- the victim can lose relic energy
- the killer can absorb part of that energy
- minimum loss prevents tiny transfers from feeling meaningless
- level downgrade can happen if energy loss drops the player below a level threshold

!!! warning
    PvP energy values strongly affect server economy and player behavior. Test them before running a public season.

## PvE Energy Loss

The `death_energy.pve` section controls energy loss from non-player deaths, such as mobs, lava, fall damage, explosions, drowning, and similar causes.

Example:

```yaml
death_energy:
  pve:
    enabled: true
    percent: 5.0
    minimum_loss: 2
```

This keeps relic energy meaningful even outside PvP.

If your server is casual, reduce PvE penalties. If your server is competitive or survival-heavy, keep them closer to default.

## PvE Energy Gain

The `energy_pve` section controls energy gained from killing mobs.

Example:

```yaml
energy_pve:
  enabled: true
  hostile_mob_kill:
    enabled: true
    energy_gain: 2
  passive_mob_kill:
    enabled: false
    energy_gain: 2
```

Default behavior:

- hostile mobs can give energy
- passive mobs are disabled by default
- spawn filters prevent easy farming from artificial sources
- a rolling cap limits how much energy a player can gain from PvE in a time window

Example cap:

```yaml
cap:
  enabled: true
  max_energy: 24
  window_hours: 24
```

This means PvE can help progression, but it should not replace the rest of the gameplay loop.

## Anti-Farm Protection

Anti-farm settings reduce repeated abuse between the same players.

Example:

```yaml
anti_farm:
  enabled: true
  same_pair_cooldown_minutes: 30
```

This is especially important on PvP servers where players might otherwise trade kills to move energy around.

## Revenge Debt

Revenge Debt is a recovery mechanic linked to PvP energy loss.

Example:

```yaml
revenge_debt:
  enabled: true
  expires_after_minutes: 30
  recovery_mode: EXACT_STOLEN_AMOUNT
```

This helps create counterplay after PvP deaths without turning energy loss into a permanent one-way punishment.

## Weekly Curses

The `weekly_curses` section controls the global curse rotation.

Example:

```yaml
weekly_curses:
  enabled: true
  rotation:
    enabled: true
    interval_days: 7
    change_day: MONDAY
    change_time: "00:00"
    candidate_count: 3
```

This page only covers the configuration overview. The full gameplay explanation belongs in the Weekly Curses feature page.

## Activation And Weapon Overlay

The `activation` section controls how relic abilities are triggered and how weapon overlays behave.

Example:

```yaml
activation:
  prevent_activation_when_interacting_with_blocks: true
  weapon_overlay:
    enabled: true
    allow_activation_from_weapon: true
```

The default setup keeps relic abilities on weapons/tools and keeps the Menu Activator separate from ability activation.

Recommended default:

- keep weapon overlay enabled
- keep Menu Activator for opening the menu
- do not use the Menu Activator as an ability trigger

## Menu Activator And Protected Items

The `items` section controls protected plugin items such as the Menu Activator.

Example:

```yaml
items:
  lock_to_slot: true
  menu_activator:
    enabled: true
    slot: 8
    material: NETHER_STAR
```

The Menu Activator is a SkyBlock-style menu item. Right-clicking it opens the RelicSeasons menu.

It does not activate relic abilities.

!!! note
    If the Menu Activator and old physical Relic Core items use the same enabled slot, the Menu Activator takes priority.

## Physical Relic Cores

Physical Relic Core items are disabled by default:

```yaml
items:
  relic_cores:
    enabled: false
```

Most servers should keep this disabled unless they are using an advanced setup or a future system that explicitly requires physical core items.

## WorldGuard

RelicSeasons can optionally respect WorldGuard regions.

Example:

```yaml
worldguard:
  enabled: true
  protection:
    respect_pvp_flag: true
    block_player_effects_when_pvp_denied: true
    protect_block_changes: true
```

Use the WorldGuard page for detailed setup information.

## Debug Settings

Debug flags are disabled by default:

```yaml
debug:
  verbose-startup: false
  energy_transfer: false
  cosmetics_death: false
```

Only enable debug options when testing or when support asks for extra logs.

Leaving debug enabled on a production server can create unnecessary console noise.

## Balance Recommendations

RelicSeasons defaults are intended to be playable and balanced for a modern SMP environment.

Before changing major values, test the default configuration with real gameplay:

- first relic selection
- PvE energy gain
- PvP death energy
- relic ability impact
- weekly curse rotation
- ritual progression
- cosmetics and menu flow

Small changes are safer than large rewrites.

Recommended approach:

1. Start with defaults.
2. Run a short test season or closed beta.
3. Adjust energy gain/loss first.
4. Adjust relic-specific values second.
5. Adjust progression caps last.

## What Not To Change Randomly

Be careful with:

- storage type or database file names
- progression caps
- level tables
- Menu Activator slot logic
- item identity materials after players already received items
- WorldGuard protection behavior on live PvP servers
- large PvP energy loss percentages
- artificial mob farming filters

These values can affect player data, balance, or anti-abuse systems.

## Future Custom Level Support

RelicSeasons currently includes a technical progression structure up to level `20`, with the public default enabled up to level `9`.

A future update is planned to make custom level counts more flexible for server owners who want longer or shorter progression paths.

Until then, treat levels above `20` as unsupported.
