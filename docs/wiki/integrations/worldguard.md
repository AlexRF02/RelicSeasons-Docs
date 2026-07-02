# WorldGuard

RelicSeasons includes optional WorldGuard support for servers that want region-based control over relic abilities and protected areas.

WorldGuard is not required to run RelicSeasons. If WorldGuard is not installed, RelicSeasons will continue working normally and region checks will be skipped.

## Requirements

- RelicSeasons installed and enabled.
- WorldGuard installed on the server.
- WorldEdit installed, as required by WorldGuard.
- Regions configured through WorldGuard.

## What The Integration Does

The WorldGuard integration allows server owners to control where relic abilities can be used.

The main idea is simple:

```text
Allowed region -> Relic abilities work normally.
Denied region -> Relic abilities are blocked or limited.
```

This is useful for:

- spawn regions
- PvP arenas
- safe zones
- protected towns
- event areas
- economy hubs
- tutorial zones

## Custom Flag

RelicSeasons can use a custom WorldGuard flag:

```text
relicseasons-abilities
```

When this flag is denied in a region, relic abilities should not be usable there.

Example:

```text
/rg flag spawn relicseasons-abilities deny
```

To allow abilities again:

```text
/rg flag spawn relicseasons-abilities allow
```

To reset the flag to default behavior:

```text
/rg flag spawn relicseasons-abilities
```

!!! note
    The exact behavior also depends on your RelicSeasons WorldGuard configuration.

## Recommended Configuration Flow

1. Install WorldGuard.
2. Start the server once with RelicSeasons.
3. Stop the server.
4. Review the RelicSeasons WorldGuard settings in `config.yml`.
5. Start the server again.
6. Configure your WorldGuard regions.
7. Test one protected region before rolling it out everywhere.

## Suggested Use Cases

### Spawn Protection

For spawn, hubs, and tutorial areas, deny relic abilities:

```text
/rg flag spawn relicseasons-abilities deny
```

This prevents players from using active relic abilities in areas where gameplay should remain controlled.

### PvP Arenas

For PvP arenas, decide based on your server design.

If you want relic abilities to be part of PvP:

```text
/rg flag arena relicseasons-abilities allow
```

If you want pure vanilla-style PvP:

```text
/rg flag arena relicseasons-abilities deny
```

### Safe Towns

For towns, markets, and protected player areas, deny destructive or offensive behavior:

```text
/rg flag town relicseasons-abilities deny
```

## PvP Flag Respect

RelicSeasons may also respect WorldGuard's PvP rules depending on configuration.

If PvP is denied in a region, offensive relic effects against players should be blocked.

This helps prevent cases where a player cannot normally attack another player, but a relic effect would still damage, debuff, move, or otherwise affect them.

!!! tip
    For safe zones, configure both the normal WorldGuard PvP behavior and the RelicSeasons ability flag.

## Block Protection

RelicSeasons can also respect protected regions for block or environment changes.

This matters for abilities or effects that may interact with the world, such as:

- fire
- block changes
- destructive effects
- environmental effects
- future visual or area-based mechanics

If region protection blocks world modification, RelicSeasons should avoid changing protected blocks.

## What Can Be Blocked

Depending on configuration and region flags, WorldGuard integration may affect:

- active relic abilities
- offensive effects against players
- player-targeting relic effects
- block or environment changes caused by relic systems
- ability activation in denied regions

If an ability is blocked before it starts, it should not consume energy or cooldown.

## What Is Not Intended To Be Blocked

The WorldGuard integration is not meant to block every RelicSeasons feature.

These systems are generally not region-restricted by WorldGuard:

- opening menus
- reading the Relic Guide
- PlaceholderAPI values
- cosmetic selections
- death messages
- projectile trail visuals
- aura cosmetics
- Weekly Curse voting menus
- backend progression data
- non-world-changing configuration reloads

## Player Feedback

When an ability is blocked by a protected region, players may receive an actionbar message explaining that relic abilities are disabled there.

This avoids confusion when a player clicks an ability but nothing happens.

## Testing Checklist

After configuring WorldGuard, test the following:

- Use a relic ability outside a protected region.
- Use the same ability inside a region with `relicseasons-abilities deny`.
- Test a PvP effect in a region where PvP is denied.
- Test a PvE effect against mobs if your server allows PvE in protected areas.
- Test that no energy is spent when an ability is blocked before activation.
- Test that cosmetics and menus still work normally.

## Troubleshooting

### Abilities still work in a protected region

Check:

1. WorldGuard is installed and loaded.
2. The player is actually inside the region.
3. The region flag is set correctly.
4. The RelicSeasons WorldGuard integration is enabled in `config.yml`.
5. There is no higher-priority region overriding the flag.

### Abilities are blocked everywhere

Check:

1. Global region flags.
2. Parent regions.
3. Region priority.
4. The RelicSeasons WorldGuard settings.
5. Whether the custom flag was set to `deny` globally.

### PvP effects are blocked but normal abilities work

This may be caused by WorldGuard's PvP flag. If PvP is denied in the region, RelicSeasons may block player-targeting effects even if general abilities are otherwise allowed.

### The flag does not exist

Make sure RelicSeasons and WorldGuard loaded correctly. Then restart the server and check the console for startup messages or errors.
