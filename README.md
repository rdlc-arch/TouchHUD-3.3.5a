Claude (Anthropic) generated

# TouchHUD

**A touch- and PC-friendly action bar HUD for World of Warcraft 3.3.5a (WotLK).**

TouchHUD makes the game playable on a touchscreen (Android emulators such as GameHub,
handhelds like the Legion Go / Steam Deck) while staying usable with mouse and keyboard.
Every button sits on a normal Blizzard action slot, so your spells are in the same place
with or without the addon, on PC or on phone.

- Version: 2.2
- Game: WoW 3.3.5a (Interface 30300), tested on Warmane
- License: MIT (see `LICENSE`)

---

## Features

- **K1-K12**: 12 big buttons for the number row (1 … 0, -, =), arranged in an arc around an
  on-screen joystick. They are the main action bar, so keys 1-= keep working, and they page
  with stances, forms, stealth and vehicles like the default bar. Each one can be hidden or
  placed on its own.
- **Flyouts (expandable buttons)**: tap once and a row of up to 8 buttons opens. It stays
  open until you tap again. Use them for buffs, food, mounts and so on. Four action flyouts,
  plus a fifth that holds your **stances / forms / auras / presences**. Any flyout can be set
  to **always open**.
- **Extra bar**: up to 12 buttons on the Bottom Left bar. Bind keys or extra mouse buttons
  in the normal *Key Bindings* menu ("Bottom Left Action Button 1-12").
- **Shaman totems**: Call of the Elements / Ancestors / Spirits plus Totemic Recall. Tap a
  Call to cast it; tap its **+** tab to open its 4 totem slots; tap a slot to pick the totem
  (a flyout inside a flyout).
- **Pet bar** that only shows while you have a pet.
- **Menu drawer**: one button that opens Blizzard's micro menu (character, spellbook,
  talents…) and bags. It can open in any direction.
- **ESC / ENTER pads** for touch.
- **Hide Blizzard bars**: main bar, Bottom Left, Bottom Right, Right, Right 2.
- **Move mode** with a grid overlay, snap-to-grid and "line up with other buttons".
- **Layouts**: keep several (for example "PC" and "Touch") and switch with one tap.
- **Export / import**: copy a layout to another device as one text string.
- Settings window with big touch-friendly controls; every part can be turned on/off,
  resized, moved and (for flyouts / extra bar) renamed.

## Install

1. Download and unzip.
2. Put the `TouchHUD` folder in `World of Warcraft\Interface\AddOns\`
   (the result must be `Interface\AddOns\TouchHUD\TouchHUD.toc`).
3. Start the game, enable TouchHUD on the character screen.

**Upgrading:** delete the old `TouchHUD` folder first, then copy the new one in.
Your settings are kept.

## First steps

1. Type `/thud` (or open **MENU > Setup**) to open the settings.
2. **General > Move**: green boxes move whole groups, blue boxes move single buttons.
   Put the **JOYSTICK CENTRE** box on your emulator's virtual joystick.
3. **General > Edit spells**: drag spells, items and macros from your spellbook or bags onto
   the buttons (all flyouts open while editing).
4. Tap **DONE** at the top of the screen.

## What to know

### Where your spells live (fixed slot map)

Every TouchHUD button owns exactly one Blizzard action slot. Nothing is shared and nothing
shifts, so a PC **without** TouchHUD shows the same spells on the default bars (turn on all
four extra bars in *Interface > ActionBars* there).

| TouchHUD | Blizzard bar | Slots |
|---|---|---|
| K1-K12 | Main bar (keys 1 … =) | 1-12 |
| Extra bar X1-X12 | Bottom Left | 61-72 |
| Flyout 1 | Bottom Right 1-8 | 49-56 |
| Flyout 2 | Bottom Right 9-12 + Right Bar 2 1-4 | 57-60, 37-40 |
| Flyout 3 | Right Bar 2 5-12 | 41-48 |
| Flyout 4 | Right Bar 1-8 | 25-32 |
| Flyout 5 | Stances / forms / auras / presences | (none) |
| Totems | Blizzard totem slots | 133-144 |

Right Bar 9-12 (slots 33-36) are left free.

### Settings are per device, spells are per character

- **Spells on buttons** are saved by the server, per character. They are the same on every
  device.
- **TouchHUD settings** (positions, sizes, options) are saved on each device in
  `WTF\Account\<ACCOUNT>\SavedVariables\TouchHUD.lua`. To copy a layout to another device,
  use **Layouts > Export**, then **Import** on the other device (or copy that file).
- All characters on one device share the active layout.

### Commands

| Command | Does |
|---|---|
| `/thud` | Open settings |
| `/thud move` / `edit` / `lock` | Move mode / spell edit mode / normal play |
| `/thud layout <name>` | Switch layout |
| `/thud resetbuttons` | Button positions back to default |
| `/thud reset` | Reset the current layout (reloads UI) |

*Esc > Key Bindings > TouchHUD* has bindings for: open settings, Move mode, each flyout,
and the menu drawer.

### Upgrading from 2.0 / 2.1

2.2 gives flyouts fixed slots. Your old flyout spells stay in their old slots until you
open **Settings > Flyouts** and press **Move my old flyout spells**. It only swaps slots and
never deletes anything. **Do it once per character, on one device only.** Spells are
server-side, so a second run on another device would shuffle them again; use **Not needed**
there instead.

## Known limits

- **Combat lockdown.** Moving, resizing, changing settings and switching layouts only work out
  of combat (WoW blocks changes to action buttons in combat). Changes made in combat apply
  when combat ends.
- **Totems can only be swapped out of combat.** Casting Calls and Recall works anywhere.
- **The ESC pad can't cancel a cast or clear your target.** WoW only allows that from a real
  key press or a macro. Put `/stopcasting` or `/cleartarget` on a button if you need it on touch.
- **Some changes need a UI reload:** hiding the Blizzard main bar, and turning the TouchHUD pet
  bar or totem bar on/off. The addon asks you when it's needed.
- **Don't run it alongside other action bar addons** (Bartender, Dominos, ElvUI action bars…).
  They fight over the same Blizzard bars, micro menu and key bindings.
- **Key routing.** With *"Keys 1..= and extra-bar keys press TouchHUD buttons"* on, those keys
  click the TouchHUD buttons directly. If another addon or a key setup misbehaves, turn it off
  (General tab); the keys then fall back to Blizzard's normal handling.
- **Hidden Blizzard bars still react to their keybinds.** This is by design, so keys keep
  working, but keep it in mind.
- **Flyout 2 spans two Blizzard bars** (Bottom Right 9-12 + Right Bar 2 1-4) because the slots
  are allocated in order.
- **Exports don't contain spells**, only the layout. Spells live on the server.
- **Copy / paste of export strings** uses Ctrl+C / Ctrl+V. On Android emulators this depends on
  the emulator's keyboard; copying the SavedVariables file is the fallback.
- **Grid snapping** is measured from the screen centre. Hold **Shift** while dropping for free
  placement (PC only). On touch, set *Snapping* to *Off* for pixel-exact placement.
- **The interface is English only.**
- **Testing.** TouchHUD was tested in game on Warmane (shaman and touch play on Android).
  Some of the newest options (layouts, extra bar, hide Blizzard bars, the 2.2 slot move) have
  had less real-world testing, and not every class or vehicle fight has been tried. Please
  report problems with the Lua error text (`/console scriptErrors 1` shows them).

## Credits

- **Author:** Radu
- Built with the help of **Claude (Anthropic)** as an AI coding assistant.
- Inspired by mobile MMO / ARPG touch layouts, **Bartender4** (Nevcairiel) and **Dominos**
  (Tuller) for the general action-bar approach, and **DragonUI** for the export/import layout
  string. **No code from these addons is included.**
- Uses Blizzard's standard UI templates and API.

## License

MIT. See `LICENSE`. You may use, modify and share it; keep the copyright notice.
