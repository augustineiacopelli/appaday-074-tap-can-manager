# AppADay 074 — Tap & Can Manager

A keezer board for a home taproom. Track what is pouring and what is cold in one screen: kegs on tap organized across as many keezers as you run, and a can inventory alongside. Every keg is tracked by real volume, so variable pour sizes and weighing a keg on a scale both work off one honest number.

**Category:** U (Utility) · **AI-powered:** no
**Live:** https://augustineiacopelli.github.io/appaday-074-tap-can-manager/

## What it does

The board is split into **On Tap** and **Cans**.

- **Keezers and taps.** On Tap is grouped by keezer. Each keezer is a set of tap handles with its own name and tap count, so a two-keezer setup with six and four taps renders as two tap walls. Filled taps show the keg with a tap-number badge; empty taps show a slot you tap to fill, with the tap number already assigned.
- **Volume, not guesses.** A keg stores its full capacity and remaining volume in ounces. Pour it down with the 4, 12, 16, 20, or 32 oz buttons; the selected size becomes that keg's sticky default and the readout recalculates how many more pours of that size are left. A plus button puts one back for corrections.
- **Estimate from weight.** Editing a keg exposes a weigh helper: enter the total weight on a scale and it subtracts the empty-keg tare and an optional coupler weight, divides by beer density (8.42 lb/gal by default), and writes the remaining gallons back. Keg-type presets (half barrel, quarter slim, sixth-barrel sixtel, corny/homebrew, custom) auto-fill capacity and tare. A guard flags a reading below the empty-keg weight instead of going negative.
- **Near-empty warnings.** Each keg turns amber as a heads-up and red when it drops below your threshold, with the remaining volume, the card, and the sight glass all shifting color, and a status tag. A kicked keg is dimmed with a ribbon.
- **Cans.** A separate cold inventory: name, style, ABV, color, and a count you crack down one at a time, going to an out state at zero.

Settings (the gear) holds the establishment name, the house pour size, the near-empty threshold, and the full keezer manager for adding, renaming, re-tapping, and removing keezers.

## Design

A warm keezer-board aesthetic where the color comes from the beer itself. Deep espresso-and-brass surfaces stay quiet so the ten-swatch SRM palette, from straw through stout, carries the visual weight. Each keg has a vertical sight-glass that drains as you pour, capped with a cream foam line. Fraunces sets the establishment wordmark and beer names, Inter carries the UI, and Space Mono handles the spec data. The signature element is the liquid itself: the board reads like a real tap list, lit by what is in the vessels.

## Technical

- Single-file vanilla HTML, CSS, and JavaScript. No frameworks, no build step.
- Google Fonts (Fraunces, Inter, Space Mono) via CDN; no other external dependencies.
- All state persists to `localStorage`, wrapped in try/catch.
- The style field suggests the full BJCP 2021 style guidelines (116 styles), shown by number and name and ordered by category, with names transliterated to ASCII.
- Fill visuals are pure CSS and HTML rather than canvas; the UI re-renders from state on every change; all user text is escaped before injection.
- Delete uses a two-tap confirm rather than a native dialog.
- Responsive from a 375px phone up through desktop, with a landscape-and-short-height layout that compacts the masthead and sight glasses; keyboard focus visible; reduced motion respected.

## How to use

1. Open the app. It seeds a couple of keezers, kegs, and cans so the board is never empty.
2. Open the gear to set your bar name, house pour size, and your keezers and tap counts.
3. Tap an empty slot to add a keg, set its style, color, keg type, and level (type it in or weigh it), then pour it down as you drink it.

---

Part of [AppADay](https://augustineiacopelli.github.io/appaday/) — one app, every day.
