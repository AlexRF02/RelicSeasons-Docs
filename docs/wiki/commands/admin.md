# Admin Commands

In this page, you will find the administrative commands available in RelicSeasons.

The main admin command is `/relicseasons`.

You can also use the shorter alias `/rs`.

The argument syntax used in commands:

- `<required>` means the argument is required.
- `[optional]` means the argument is optional.

!!! warning
    These commands can modify player relic state, energy, fragments, weekly curses, ritual cooldowns, debug state, or server configuration. They should only be granted to trusted staff.

!!! note
    The admin command checks `relicseasons.admin` before dispatching any subcommand. Subcommand-specific permissions are checked afterwards, but they are not enough on their own unless the sender also has `relicseasons.admin`.

---

## `/relicseasons reload`

**Description:** Reloads RelicSeasons configuration, language messages, runtime state, tasks, menus, relic effects, fragments, rituals and player overlays.

**Permission:** `relicseasons.admin` and `relicseasons.admin.reload`

**Aliases:** `/rs reload`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons reload
/rs reload
```

---

## `/relicseasons debug <player>`

**Description:** Shows detailed debug information for a player's relic, energy, active ability, relic core, weapon overlay, death-energy state, anti-farm state and related runtime systems.

**Permission:** `relicseasons.admin` and `relicseasons.admin.debug`

**Aliases:** `/rs debug <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons debug Steve
/rs debug Alex
```

---

## `/relicseasons core repair <player>`

**Description:** Repairs or restores the target player's locked relic core item.

**Permission:** `relicseasons.admin` and `relicseasons.admin.core`

**Aliases:** `/rs core repair <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons core repair Steve
/rs core repair Alex
```

---

## `/relicseasons debt list <player>`

**Description:** Lists active revenge debt records involving the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.debug`

**Aliases:** `/rs debt list <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons debt list Steve
/rs debt list Alex
```

---

## `/relicseasons antifarm list <player>`

**Description:** Lists active anti-farm records involving the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.debug`

**Aliases:** `/rs antifarm list <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons antifarm list Steve
/rs antifarm list Alex
```

---

## `/relicseasons antifarm clear <player>`

**Description:** Clears active anti-farm records involving the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.debug`

**Aliases:** `/rs antifarm clear <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons antifarm clear Steve
/rs antifarm clear Alex
```

---

## `/relicseasons antifarm clearall`

**Description:** Clears all anti-farm records.

**Permission:** `relicseasons.admin` and `relicseasons.admin.debug`

**Aliases:** `/rs antifarm clearall`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons antifarm clearall
/rs antifarm clearall
```

---

## `/relicseasons energy <set|add|remove> <player> <amount>`

**Description:** Sets, adds or removes current relic energy for the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.energy`

**Aliases:** `/rs energy <set|add|remove> <player> <amount>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons energy set Steve 100
/relicseasons energy add Steve 25
/relicseasons energy remove Steve 10
/rs energy set Alex 50
```

---

## `/relicseasons natural <set|add|remove> <player> <amount>`

**Description:** Sets, adds or removes natural relic energy for the target player. This may affect the player's relic level according to the energy service rules.

**Permission:** `relicseasons.admin` and `relicseasons.admin.energy`

**Aliases:** `/rs natural <set|add|remove> <player> <amount>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons natural set Steve 100
/relicseasons natural add Steve 25
/relicseasons natural remove Steve 10
/rs natural set Alex 50
```

---

## `/relicseasons relic set <player> <relic_id>`

**Description:** Changes the target player's current official relic.

**Permission:** `relicseasons.admin` and `relicseasons.admin.relic`

**Aliases:** `/rs relic set <player> <relic_id>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons relic set Steve void_ender_relic
/rs relic set Alex flame_relic
```

---

## `/relicseasons relic level set <player> <level>`

**Description:** Sets the target player's current relic level.

**Permission:** `relicseasons.admin` and `relicseasons.admin.level`

**Aliases:** `/rs relic level set <player> <level>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons relic level set Steve 5
/rs relic level set Alex 10
```

---

## `/relicseasons curse status`

**Description:** Shows weekly curse status, active curse, rotation data, weighted votes and leveled mob status.

**Permission:** `relicseasons.admin` and either `relicseasons.admin.curse` or `relicseasons.admin.debug`

**Aliases:** `/rs curse status`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons curse status
/rs curse status
```

---

## `/relicseasons curse set <curse_id>`

**Description:** Sets the active weekly curse.

**Permission:** `relicseasons.admin` and either `relicseasons.admin.curse` or `relicseasons.admin.debug`

**Aliases:** `/rs curse set <curse_id>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons curse set void_corruption
/rs curse set broken_sky
```

---

## `/relicseasons curse clear`

**Description:** Clears the active weekly curse.

**Permission:** `relicseasons.admin` and either `relicseasons.admin.curse` or `relicseasons.admin.debug`

**Aliases:** `/rs curse clear`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons curse clear
/rs curse clear
```

---

## `/relicseasons fragments giveitem <player> <relic_id>`

**Description:** Gives a physical secondary relic fragment item to the target player.

**Permission:** `relicseasons.admin` and `relicseasons.fragments.admin`

**Aliases:** `/rs fragments giveitem <player> <relic_id>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons fragments giveitem Steve flame_relic
/rs fragments giveitem Alex void_ender_relic
```

---

## `/relicseasons fragments givepending <player> <relic_id>`

**Description:** Creates a pending secondary relic fragment for the target player.

**Permission:** `relicseasons.admin` and `relicseasons.fragments.admin`

**Aliases:** `/rs fragments givepending <player> <relic_id>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons fragments givepending Steve frost_relic
/rs fragments givepending Alex storm_relic
```

---

## `/relicseasons fragments giveactive <player> <relic_id>`

**Description:** Creates an active secondary relic fragment for the target player, if the player has a free active fragment slot.

**Permission:** `relicseasons.admin` and `relicseasons.fragments.admin`

**Aliases:** `/rs fragments giveactive <player> <relic_id>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons fragments giveactive Steve titan_relic
/rs fragments giveactive Alex shadow_relic
```

---

## `/relicseasons fragments dust <player> <amount>`

**Description:** Adds Relic Dust to the target player.

**Permission:** `relicseasons.admin` and `relicseasons.fragments.admin`

**Aliases:** `/rs fragments dust <player> <amount>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons fragments dust Steve 100
/rs fragments dust Alex 50
```

---

## `/relicseasons fragments clear <player>`

**Description:** Clears active and pending fragments for the target player.

**Permission:** `relicseasons.admin` and `relicseasons.fragments.admin`

**Aliases:** `/rs fragments clear <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons fragments clear Steve
/rs fragments clear Alex
```

---

## `/relicseasons fragments resonance <player> <amount>`

**Description:** Sets resonance for the target player's current relic.

**Permission:** `relicseasons.admin` and `relicseasons.fragments.admin`

**Aliases:** `/rs fragments resonance <player> <amount>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons fragments resonance Steve 25
/rs fragments resonance Alex 100
```

---

## `/relicseasons weeklycurses <resolve|finish|rotate-now>`

**Description:** Immediately resolves the current weekly curse vote and rotates candidates as needed.

**Permission:** `relicseasons.admin`

**Aliases:** `/rs weeklycurses <resolve|finish|rotate-now>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons weeklycurses resolve
/relicseasons weeklycurses finish
/rs weeklycurses rotate-now
```

---

## `/relicseasons selection open <player>`

**Description:** Opens the first relic selection menu for an unbound target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.selection`

**Aliases:** `/rs selection open <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons selection open Steve
/rs selection open Alex
```

---

## `/relicseasons selection reroll <player>`

**Description:** Rerolls first relic selection choices for the target player if the player is still unbound and selection is enabled.

**Permission:** `relicseasons.admin` and `relicseasons.admin.selection`

**Aliases:** `/rs selection reroll <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons selection reroll Steve
/rs selection reroll Alex
```

---

## `/relicseasons selection assign <player> <relic_id>`

**Description:** Assigns a first relic to the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.selection`

**Aliases:** `/rs selection assign <player> <relic_id>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons selection assign Steve void_ender_relic
/rs selection assign Alex flame_relic
```

---

## `/relicseasons activator debug <player>`

**Description:** Shows Menu Activator debug information for the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.activator`

**Aliases:** `/rs activator debug <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons activator debug Steve
/rs activator debug Alex
```

---

## `/relicseasons activator fix <player>`

**Description:** Reconciles or restores the Menu Activator item for the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.activator`

**Aliases:** `/rs activator fix <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons activator fix Steve
/rs activator fix Alex
```

---

## `/relicseasons altar give <player>`

**Description:** Gives a Relic Altar ritual item to the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.altar`

**Aliases:** `/rs altar give <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons altar give Steve
/rs altar give Alex
```

---

## `/relicseasons ritual open <player>`

**Description:** Opens the rituals menu for the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.ritual`

**Aliases:** `/rs ritual open <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons ritual open Steve
/rs ritual open Alex
```

---

## `/relicseasons ritual cooldown reset <player>`

**Description:** Resets the target player's relic change ritual cooldown.

**Permission:** `relicseasons.admin` and `relicseasons.admin.ritual`

**Aliases:** `/rs ritual cooldown reset <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons ritual cooldown reset Steve
/rs ritual cooldown reset Alex
```

---

## `/relicseasons ritual debug <player>`

**Description:** Shows ritual debug information for the target player.

**Permission:** `relicseasons.admin` and `relicseasons.admin.ritual`

**Aliases:** `/rs ritual debug <player>`

**Usable in Console:** Yes

**Examples:**

```text
/relicseasons ritual debug Steve
/rs ritual debug Alex
```

---

## Permission Notes

The `/relicseasons` command and `/rs` alias are admin-only.

The command executor requires `relicseasons.admin` before any subcommand is processed. Most subcommands then also check a more specific permission such as `relicseasons.admin.reload`, `relicseasons.admin.energy`, or `relicseasons.fragments.admin`.

Temporary internal debug commands are intentionally not documented here.
