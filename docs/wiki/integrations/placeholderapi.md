# PlaceholderAPI

RelicSeasons includes optional PlaceholderAPI support for servers that want to display relic data in scoreboards, tab lists, holograms, menus, chat plugins, or other compatible plugins.

PlaceholderAPI is not required to run RelicSeasons. If PlaceholderAPI is not installed, RelicSeasons will simply skip the integration.

## Requirements

- RelicSeasons installed and enabled.
- PlaceholderAPI installed on the server.
- A plugin that can display PlaceholderAPI placeholders, such as a scoreboard, tab list, hologram, chat, menu, or HUD plugin.

!!! note
    RelicSeasons registers its placeholders automatically when PlaceholderAPI is detected. You do not need to manually download a separate expansion.

## Identifier

The PlaceholderAPI identifier is:

```text
relicseasons
```

That means all placeholders use this format:

```text
%relicseasons_placeholder_name%
```

## Available Placeholders

| Placeholder | Description |
| --- | --- |
| `%relicseasons_relic_name%` | Shows the player's current relic name. |
| `%relicseasons_relic_level%` | Shows the player's current relic level. |
| `%relicseasons_relic_energy%` | Shows the player's current relic energy. |
| `%relicseasons_relic_max_energy%` | Shows the maximum energy available for the player's current relic level. |
| `%relicseasons_relic_resonance%` | Shows the player's current relic resonance. |
| `%relicseasons_pve_energy_used%` | Shows how much PvE energy the player has used in the current PvE energy window. |
| `%relicseasons_pve_energy_remaining%` | Shows how much PvE energy the player can still gain during the current PvE energy window. |
| `%relicseasons_pve_energy_cap%` | Shows the configured PvE energy cap. |
| `%relicseasons_pve_energy_time_left%` | Shows the remaining time before the player's PvE energy window resets. |
| `%relicseasons_weekly_curse_name%` | Shows the currently active weekly curse name. |
| `%relicseasons_weekly_curse_time_left%` | Shows the remaining time before the current weekly curse rotates or expires. |
| `%relicseasons_fragment_active_name%` | Shows the player's active secondary fragment name, if one is active. |
| `%relicseasons_fragment_pending_count%` | Shows how many pending fragments the player currently has. |

## Example Usage

A scoreboard could display:

```text
Relic: %relicseasons_relic_name%
Level: %relicseasons_relic_level%
Energy: %relicseasons_relic_energy%/%relicseasons_relic_max_energy%
Resonance: %relicseasons_relic_resonance%
```

A weekly curse line could display:

```text
Curse: %relicseasons_weekly_curse_name%
Time Left: %relicseasons_weekly_curse_time_left%
```

A PvE energy line could display:

```text
PvE Energy: %relicseasons_pve_energy_remaining%/%relicseasons_pve_energy_cap%
Reset: %relicseasons_pve_energy_time_left%
```

## Player Placeholders

Most RelicSeasons placeholders are player-based. They need a player context to return personal relic data.

For example, these placeholders depend on the player:

```text
%relicseasons_relic_name%
%relicseasons_relic_level%
%relicseasons_relic_energy%
%relicseasons_fragment_pending_count%
```

If a plugin tries to parse them without a player, the result may be empty, `None`, `0`, or another safe fallback depending on the placeholder.

## Safe Fallbacks

RelicSeasons placeholders are designed to fail safely.

If a player has no relic yet, a value is not loaded, or a system is disabled, placeholders should return a safe value instead of causing errors.

Common fallback-style values include:

- `None`
- `0`
- `Ready`
- the configured cap value
- an empty or neutral value depending on the placeholder

## Reloading

If you edit RelicSeasons configuration, language files, or display names, you can reload the plugin with:

```text
/rs reload
```

After reloading, compatible plugins should start receiving the updated values.

!!! tip
    If a scoreboard or tab plugin caches text heavily, reload that plugin too after changing PlaceholderAPI-based lines.

## Performance Notes

RelicSeasons placeholders are intended for frequent display use. They should rely on runtime state and caches instead of querying SQLite every time a placeholder is requested.

This makes them suitable for scoreboards and other frequently refreshed displays.

## Troubleshooting

### The placeholder appears as plain text

Example:

```text
%relicseasons_relic_name%
```

This usually means PlaceholderAPI is not installed, the display plugin is not parsing PlaceholderAPI placeholders, or RelicSeasons did not register its integration.

Check that:

1. PlaceholderAPI is installed.
2. RelicSeasons loaded without errors.
3. Your scoreboard/tab/menu plugin supports PlaceholderAPI.
4. The placeholder is typed exactly as documented.

### The placeholder returns `None` or `0`

This usually means the player has no relic data yet, the player has not selected a relic, or the related system is not active for that player.

### Values do not update after editing files

Run:

```text
/rs reload
```

If the display plugin also caches text, reload that plugin too.
