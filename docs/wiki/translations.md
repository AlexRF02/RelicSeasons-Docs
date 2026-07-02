# Translations

RelicSeasons includes a configurable language system so server owners can adapt plugin text to their community.

The plugin currently ships with ready-to-use English and Spanish language files. You can use one of the included languages as-is, or edit the generated language files to customize menu names, item lore, chat messages, actionbar text, warnings, and other visible text.

## Selecting The Active Language

The active language is selected from the main `config.yml` file.

```yaml
language:
  active: "en_US"
```

To switch language, change the `active` value to the locale you want to use.

Examples:

```yaml
language:
  active: "en_US"
```

```yaml
language:
  active: "es_ES"
```

After changing the active language, reload the plugin or restart the server.

```text
/rs reload
```

!!! note
    `/rs reload` is useful while testing translations or making small text changes. For production servers, a full restart is still recommended after larger configuration changes.

## Language Folder

RelicSeasons language files are stored inside the plugin folder.

A typical structure looks like this:

```text
plugins/RelicSeasons/
├─ config.yml
└─ lang/
   ├─ en_US/
   │  ├─ menus/
   │  │  ├─ relics.yml
   │  │  ├─ main.yml
   │  │  └─ ...
   │  └─ ...
   └─ es_ES/
      ├─ menus/
      │  ├─ relics.yml
      │  ├─ main.yml
      │  └─ ...
      └─ ...
```

Each locale has its own folder. The locale selected in `config.yml` determines which folder RelicSeasons reads from.

## Editing Menu Text

Many menu names and lore lines are configured from language files instead of the menu layout files.

For example, relic menu text can be edited from a language file such as:

```text
lang/en_US/menus/relics.yml
```

The file may contain sections like:

```yaml
relics:
  title: "Your Relics"
  names:
    blood_relic: "Blood Relic"
    titan_relic: "Titan Relic"
  item:
    name: "&a{relic}"
    lore:
      - "&fStatus: {status}"
      - "&fLevel: &b{level}"
      - "&fNatural Energy: &b{natural_energy}/{max_energy}"
```

This means you can customize the visible text without changing the menu layout itself.

!!! tip
    Menu layout files decide where items appear. Language files decide what players read.

## Placeholders

Language files can contain placeholders. Placeholders are dynamic values replaced by RelicSeasons while the plugin is running.

Examples:

```text
{relic}
{level}
{status}
{natural_energy}
{max_energy}
{active_fragments}
{pending_fragments}
```

When translating or editing text, keep placeholders exactly as they are.

Correct:

```yaml
name: "&a{relic}"
```

Incorrect:

```yaml
name: "&a{reliquia}"
```

RelicSeasons only recognizes the original placeholder names. If a placeholder is renamed, removed, or misspelled, the plugin may show incomplete text or fail to render that value.

## Color Codes

RelicSeasons language files may use Minecraft-style color codes with `&`.

Examples:

```yaml
name: "&aBack"
lore:
  - "&7Return to the RelicSeasons Menu."
```

Common examples:

| Code | Meaning |
| --- | --- |
| `&a` | Green |
| `&b` | Aqua |
| `&c` | Red |
| `&e` | Yellow |
| `&f` | White |
| `&7` | Gray |
| `&8` | Dark gray |

You can change colors if you want your server to use a different visual style.

## Reloading Translations

For small text edits, you can usually reload RelicSeasons without restarting the whole server.

Recommended testing flow:

1. Edit the language file.
2. Save the file.
3. Run `/rs reload`.
4. Close and reopen the affected menu.
5. Check the result in-game.

```text
/rs reload
```

!!! warning
    Players who already have a menu open may still see the old text until they close and reopen it.

## Switching Language While The Server Is Online

You can change the active language in `config.yml` and then run:

```text
/rs reload
```

This can be useful during setup, testing, or translation review.

However, changing the entire active language while players are online is not always recommended on a production server.

Reasons:

- Some players may have menus open while the reload happens.
- Existing items, cached menu views, or temporary messages may not visually update until reopened or refreshed.
- Staff may confuse players if part of the server changes language during gameplay.
- Large config edits are safer to apply during maintenance.

For live servers, the safest flow is:

1. Announce a short maintenance window.
2. Stop the server.
3. Change `language.active` in `config.yml`.
4. Review the target language files.
5. Start the server again.
6. Check menus, commands, and messages in-game.

## Creating A Custom Translation

You can create your own language variant by copying an existing locale folder.

Example:

```text
lang/en_US/ → lang/custom/
```

Then set:

```yaml
language:
  active: "custom"
```

When creating a custom translation:

- Keep the same file names.
- Keep the same YAML structure.
- Keep all existing keys.
- Keep placeholders unchanged.
- Only edit the visible text.

!!! warning
    Removing keys or changing section names may cause missing messages or fallback behavior.

## YAML Safety Tips

Language files use YAML, so formatting matters.

Recommended rules:

- Keep indentation consistent.
- Use spaces, not tabs.
- Put text with `:` inside quotes.
- Keep list items with `-`.
- Do not remove required sections.
- Make backups before large edits.

Good:

```yaml
lore:
  - "&7Return to the RelicSeasons Menu."
  - "&eClick to go back."
```

Bad:

```yaml
lore:
- "&7Broken indentation"
```

## What Can Be Translated?

Depending on the installed version, language files may control text for systems such as:

- Main menus
- Relic menus
- Relic progression menus
- First relic selection
- Secondary fragments
- Weekly curses
- Ritual altar menus
- Cosmetics
- Player feedback messages
- Error messages
- Admin messages

## What Should Not Be Changed?

Some values are identifiers, not visible text.

Do not translate internal IDs such as:

```text
blood_relic
flame_relic
void_ender_relic
weekly_curse_id
cosmetic_id
```

Visible names can be translated, but internal IDs should stay unchanged.

Example:

```yaml
names:
  blood_relic: "Blood Relic"
```

You can change `"Blood Relic"`, but you should not rename `blood_relic`.

## Troubleshooting

### Text did not change after editing

Run:

```text
/rs reload
```

Then close and reopen the affected menu.

### The plugin shows missing or broken text

Check that:

- The active language in `config.yml` matches an existing folder.
- The YAML file has valid indentation.
- The key still exists.
- The placeholder names were not changed.

### A menu still uses the old language

Close the menu and open it again. If the issue continues, restart the server.

### The server console shows YAML errors

Review the edited file and check for:

- broken indentation
- missing quotes
- tabs instead of spaces
- invalid characters
- unfinished lists

## Best Practices

- Edit translations on a test server first.
- Keep a backup of the original language folder.
- Translate one file at a time.
- Reload and test after each important change.
- Keep placeholders unchanged.
- Restart the server after major language or config changes.
