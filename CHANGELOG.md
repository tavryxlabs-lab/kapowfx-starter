# KapowFX Starter — Changelog

## 1.0.1 — 2026-10-29
- **The Starter is now MIT licensed** (free for any use, including commercial
  games). The Full version keeps the KapowFX Asset License.
- Now also on GitHub: https://github.com/tavryxlabs-lab/kapowfx-starter
- Packaging: ZIP paths now use `/` (portable across extractors) and leftover
  `.uid` files of Full-only effects were removed. No code changes.

## 1.0.0 — 2026-08

Initial release.

- 6 one-shot effects: `impact_spark`, `shockwave`, `hit_flash`, `hit_burst`,
  `smoke_pop`, `pickup_sparkle` — 100% procedural, zero art files.
- Game feel toolkit: `Fx.shake()`, `Fx.hitstop()`, `Fx.flash()`, `Fx.popup()`.
- Tested on Godot 4.7 (Compatibility renderer), desktop + web exports.
- The Full version adds 10 more effects, 5 screen transitions with an
  `await` API and the interactive gallery demo.
