# FAQ

This page answers common questions server owners may have before installing or configuring RelicSeasons.

## Which server software is supported?

RelicSeasons is designed for modern Paper servers.

The current target is:

- Paper 1.21.x
- Java 21

Other forks may work, but Paper is the recommended and supported platform.

## Are PlaceholderAPI and WorldGuard required?

No.

Both integrations are optional.

RelicSeasons can run without PlaceholderAPI and without WorldGuard. If those plugins are installed, RelicSeasons can hook into them and provide extra functionality.

## Can I customize relics?

Yes.

RelicSeasons is built around configurable relic behavior, progression values, menus, language files, sounds, and balance settings.

You can tune values such as:

- energy behavior
- relic progression
- menu text
- language messages
- secondary fragments
- weekly curse settings
- cosmetic permissions
- ritual requirements

Creating completely new Java-coded relic types is not currently a normal configuration feature, but the included relics are designed to be adjustable.

## How many relic levels are supported?

By default, RelicSeasons uses an enabled progression cap of 9 levels.

The plugin also has a technical hard cap of 20 levels.

That means:

- level 9 is the default active maximum
- levels up to 20 can exist as configured/future progression space
- levels above 20 are not currently supported

!!! note
    A future update may allow server owners to define a larger or more flexible level range, but this is not part of the current supported configuration.

## Can I change the language?

Yes.

RelicSeasons includes language files and supports selecting the active language from configuration.

The default supported languages are:

- English
- Spanish

You can edit language files directly to adapt text to your server.

After editing language files, use:

```text
/rs reload
```

For major language changes or large file restructuring, a full server restart is still safer.

## Can I reload the plugin without restarting the server?

Yes, RelicSeasons includes an admin reload command:

```text
/rs reload
```

This is useful after editing configuration, menus, or language files.

However, for production servers, it is still recommended to restart the server after major updates, dependency changes, jar changes, or large configuration migrations.

## Where is player data stored?

RelicSeasons uses local storage, including SQLite-based data for persistent player systems.

Before updating the plugin, changing major configuration sections, or resetting progression systems, always create a backup of the plugin folder.

Recommended backup targets:

- RelicSeasons plugin folder
- SQLite database files
- configuration files
- language files
- menu files
- relic configuration files

## Why does a player not receive energy?

There are several possible reasons.

Check if:

- the player has selected or owns a relic
- the relic is already at maximum energy for the current level
- the PvE energy cap has been reached
- the action does not qualify for energy gain
- the server has anti-farm protection affecting the event
- the relevant energy system is enabled in configuration

PvE energy and PvP energy are separate systems and can have different rules.

## Why does a relic ability not work?

Common causes include:

- the player has no current relic
- the relic is on cooldown
- the player does not have enough energy
- WorldGuard blocks relic abilities in the region
- the player is in a protected area
- the ability was blocked before activation
- the item used is not the correct relic/core item
- the server configuration disabled or changed the behavior

If WorldGuard is installed, test the same ability outside protected regions.

## Do cosmetics give gameplay advantages?

No.

Cosmetics are intended to be visual and identity-based rewards.

They may include things like:

- kill messages
- death messages
- projectile trails
- kill effects
- death effects
- auras

They should not directly increase relic strength or player power.

## How do I give access to admin commands?

Admin commands should only be given to trusted staff.

The main admin permission is:

```text
relicseasons.admin
```

Some admin subcommands also require more specific permissions, but the admin command first requires `relicseasons.admin`.

For example, giving only a specific sub-permission may not be enough if the player does not also have the main admin permission.

## Why can players not see or use some cosmetics?

Cosmetics are permission-based.

A player must have the required permission for the selected cosmetic.

RelicSeasons also supports category-style wildcard permissions, such as unlocking all cosmetics in a cosmetic category.

If a player loses permission for a selected cosmetic, the selection may remain stored, but the cosmetic should not apply until the permission is restored.

## Can I use RelicSeasons on an existing SMP?

Yes.

RelicSeasons is designed for SMP-style progression and can be added to an existing server.

For existing servers, it is recommended to:

1. Test on a copy of the server first.
2. Configure balance before public release.
3. Review permissions.
4. Check WorldGuard regions if used.
5. Backup before installing on production.

## Should I change the default balance immediately?

Not necessarily.

The default balance is intended to be usable as a starting point.

You can adjust the system later based on your server economy, PvP pacing, progression speed, and player feedback.

For the first public test, it is usually better to make small changes instead of changing every value at once.
