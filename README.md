# ⚡ KapowFX Starter — Free 2D VFX & Game Feel for Godot 4

![KapowFX effects in action](https://raw.githubusercontent.com/tavryxlabs-lab/kapowfx-starter/main/media/kapowfx_hero.gif)
<sub>The GIF mixes Starter and Full effects — the Starter ones are listed below.</sub>

**Juicy, drop-in 2D effects with zero art files.** Every effect is pure GDScript +
shaders + particles — no textures, no spritesheets, no external dependencies.
Recolor, rescale and retime everything from the Inspector.

**This is the free Starter (MIT):** 6 effects + the complete game-feel toolkit
(screen shake, hitstop, screen flash, damage popups).
**Download:** clone this repo, grab the [latest ZIP](https://github.com/tavryxlabs-lab/kapowfx-starter/archive/refs/heads/main.zip),
or get it on itch.io: [tavryx.itch.io/kapowfx-starter](https://tavryx.itch.io/kapowfx-starter).
The [**Full version**](https://tavryx.itch.io/kapowfx) adds 10 more effects,
5 screen transitions and the interactive gallery.

- **Godot 4.2 – 4.7+** (built and tested on 4.7, Compatibility renderer → works
  on desktop, mobile and web exports)
- **Game feel toolkit**: screen shake, hitstop, screen flash, damage popups
- Resolution-independent (shader/SDF based — crisp at any zoom)
- **Starter: MIT license** — free for any use, including commercial games

---

## Install (60 seconds)

1. Copy the `kapowfx/` folder anywhere into your project (keep it at
   `res://kapowfx/` for zero config).
2. **Project Settings → Globals (Autoload)** → add
   `res://kapowfx/fx.gd` with the name **`Fx`**.
3. Done. Play an effect from any script:

```gdscript
Fx.spawn("impact_spark", global_position)
```

> No autoload? You can also just instance any effect scene directly:
> `res://kapowfx/effects/impact/impact_spark.tscn` — it plays on ready and
> frees itself.

## Quick start — the fun stuff

```gdscript
# One-liners, from anywhere:
Fx.spawn("impact_spark", enemy.global_position, {"size": 1.5})
Fx.spawn("shockwave", pos, {"color_main": Color.CYAN})
Fx.spawn("smoke_pop", pos)

# Game feel:
Fx.shake(8.0)                 # camera shake (finds your Camera2D)
Fx.hitstop(0.06)              # freeze-frame drama
Fx.flash(Color.WHITE, 0.12)   # full-screen flash
Fx.popup("9999", pos, {"crit": true})   # juicy damage number
```

### Spawn options

| Key | Type | Effect |
|---|---|---|
| `size` | float | overall scale multiplier |
| `speed` | float | playback speed (2.0 = twice as fast) |
| `color_main` | Color | primary color |
| `color_accent` | Color | secondary color |
| `rotation` | float | aim directional effects |
| `parent` | Node | spawn under a specific node |

Every effect also exposes these (plus its own extras, e.g. `star_points`)
as Inspector properties on the scene root — tweak without touching any code.

## Effect list

**In this Starter** — `impact_spark`, `shockwave`, `hit_flash`, `hit_burst`,
`smoke_pop`, `pickup_sparkle` + shake / hitstop / flash / popup

**[Full version](https://tavryx.itch.io/kapowfx) adds** — `explosion_ball`,
`slash_arc`, `lightning_strike`, `fire_burst`, `ice_shatter`, `poison_cloud`,
`magic_circle`, `heal_rise`, `coin_burst`, `level_up` + 5 awaitable screen
transitions (`circle`, `wipe`, `diamonds`, `dissolve`, `blinds`) + the
interactive gallery (also playable on the itch page).

## Recipe

```gdscript
# A satisfying hit, Starter only:
func on_enemy_hit(enemy: Node2D, damage: int) -> void:
    Fx.spawn("hit_burst", enemy.global_position)
    Fx.popup(str(damage), enemy.global_position + Vector2(0, -20))
    Fx.hitstop(0.05)
    Fx.shake(5.0)
```

## Performance notes

- Effects are GPU particles + tiny shaders; dozens per second is fine on any
  hardware.
- Everything is one-shot and frees itself (`auto_free`) — no cleanup needed.
- Compatibility renderer friendly: identical look on Forward+, Mobile and Web.

## FAQ

**Does it work in Godot 4.2/4.3/4.4?** Yes — the kit uses stable core APIs
(GPUParticles2D, canvas shaders, Tweens). Built on 4.7.

**C# projects?** Yes — call it through Godot's cross-language scripting:
`GetNode("/root/Fx").Call("spawn", "impact_spark", pos);`

**Can I edit the effects?** Absolutely. Each effect is a small, commented
GDScript file. Duplicate a scene, tweak exported params, or dig into the
particle materials.

## Issues & feedback

Bug reports and requests are welcome in
[GitHub Issues](https://github.com/tavryxlabs-lab/kapowfx-starter/issues) or on
the [itch.io page](https://tavryx.itch.io/kapowfx-starter).

## License

The **Starter** is MIT — free for any use, including commercial games. Credit
appreciated, not required. See [LICENSE.txt](LICENSE.txt).
The **Full version** sold on itch.io uses the KapowFX Asset License.

---

**More polish:** its sibling [**PolishFX**](https://tavryx.itch.io/polishfx)
adds 28 stackable sprite effects in one material (outline, dissolve, glow,
freeze, squash & stretch…) — free 8-effect Lite on
[GitHub](https://github.com/tavryxlabs-lab/polishfx-lite). Made by **Tavryx**.
