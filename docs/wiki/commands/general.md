# General Commands

In this page, you will find the general player commands available in RelicSeasons.

Simply type `/relic` in-game to open the RelicSeasons player menu.

The argument syntax used in commands:

- `<required>` means the argument is required.
- `[optional]` means the argument is optional.

!!! tip
    You can use the **Tab** key to automatically complete available arguments when a command supports tab completion.

!!! note
    The `/relic` command is player-only and currently does not register a custom tab completer.

---

## `/relic`

**Description:** Opens the main RelicSeasons player menu. If the menu cannot be opened, the command falls back to showing the player's current relic information and HUD.

**Permission:** `relicseasons.command.relic`

**Aliases:** `/relics`

**Usable in Console:** No

**Examples:**

```text
/relic
/relics
```

---

## `/relic active`

**Description:** Activates the player's current relic active ability.

**Permission:** `relicseasons.command.relic`

**Aliases:** `/relics active`

**Usable in Console:** No

**Examples:**

```text
/relic active
/relics active
```

---

## `/relic fragments`

**Description:** Opens the player's secondary relic fragments menu.

**Permission:** `relicseasons.command.relic`

**Aliases:** `/relics fragments`

**Usable in Console:** No

**Examples:**

```text
/relic fragments
/relics fragments
```

---

## Permission Notes

The public `/relic` command is protected by `relicseasons.command.relic`.

In the current plugin configuration, this permission is intended to be available to normal players by default unless the server's permission setup overrides it.

Console execution is not supported for player-only commands.
