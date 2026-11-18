# Take One plugin catalog

`catalog.json` is the plugin library the Take One app downloads. A plugin listed here appears in every installed copy of the app the next time its plugin library opens. No app build is involved.

## Adding or changing a plugin

1. Edit `catalog.json`: add an entry to `plugins`, or change one.
2. Check the file is still valid JSON.
3. Commit and push to `main`.

Apps pick the change up within about 15 minutes of the push (GitHub caches the file for a few minutes, and the app re-reads it at most every 15).

An entry that is malformed is skipped by the app; the rest of the file still loads. An entry the installed app version cannot play is shown greyed out as needing an update.

## What an entry looks like

A plugin is either a starting sound for one of the app's four built-in panels (`engine`: `eq`, `dynamics`, `reverb`, `delay`), or a patch (`engine`: `patch`) with its own knobs and a signal chain made of the app's blocks: `gain`, `filter`, `shaper`, `delay`, `comp`, `mix`, `width`, `tremolo`. Pure Voice Pro uses `cleanvoice`, a neural engine built into the app; older versions list it as needing the latest Take One.

The full format, with every block's settings, is in the app repository under `Docs/PluginLibrary/README.md`.

## Rules

- Never reuse or rename an `id`: saved projects refer to plugins by it.
- A paid plugin needs its `productID` to exist as a non-consumable in-app purchase in App Store Connect before it is listed here.
- To withdraw a plugin, set `"hidden": true` or delete the entry. Projects that already use it keep playing it.
