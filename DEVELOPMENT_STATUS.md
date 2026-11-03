# Development status — pfUI_VendorTweaks

**Updated:** 2026-11-03  
**Working branch:** `dev`  
**Dev version:** `0.1.35-dev` (in `pfUI_VendorTweaks.toc`)  
**Stable branch/version:** `main` / `0.1.34`, unchanged  
**Target clients:** original-style vanilla 1.12.1 and Turtle WoW-derived 1.12.1 clients

## Latest code commits
- `25e33e938364281bae6b2c7b1ccdfcf5ac1995b5` — bump dev version for cross-client compatibility.
- `eeb21d6d12c4012493956d03f436e7e520e032c2` — normalize item metadata for Turtle WoW and vanilla clients.

## Completed
- Added a central `ReadItemMetadata` adapter for alternate `GetItemInfo` return layouts: eighth/tenth or seventh/ninth positions for stack/icon.
- Updated saved-list icon resolution and item drop handling to use normalized metadata.
- Rejected non-string icon values, including previously cached numeric sell prices, in the metadata cache, list display, and deletion animation.
- Left all buying/selling/deleting rules, purchase limits, and the stable `main` branch unchanged.
- Passed five isolated Lua return-value scenarios (vanilla/SoloCraft shape, Turtle shape with sell value, equipped-item variants, and missing item information).
- Re-fetched `dev` and verified key changes and version; confirmed `main` retains its original code.

## Untested
- Actual in-game execution on SoloCraft and the private Turtle WoW server.
- Saved-variable migration behavior on a real account containing corrupt icon values.
- Edge cases involving uncached items, merchant-only items, and client-specific differences beyond the documented positional change.
- Runtime compilation on the game's original Lua 5.0 interpreter (isolated tests used TeX Lua).

## Deferred
- Promotion from `dev` to `main` pending tests on both clients.
- Any wider BagTweaks-specific API compatibility audit (this change is for **VendorTweaks**).

## Exact next step
Install `dev` version `0.1.35-dev` in the private Turtle WoW client; reopen pfUI → Thirdparty → VendorTweaks and verify the Rune of Teleportation icon in Auto-Buy, plus Auto-Sell/Auto-Delete icons and a previously saved numeric-icon entry. Repeat on SoloCraft with the same dev build, then inspect errors and promote to stable only if both pass.
