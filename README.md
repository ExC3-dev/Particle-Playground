
# Particle-Playground

**Particle-Playground** — an interactive, browser-based particle sandbox.  
This single-file demo (HTML/CSS/JS) includes particles, black holes (BHs), fields, debug visualizations (arrows, heatmap/trails), full export/import of scene & UI state, and many tunable physics and visual options.

---

## Demo

### If you want to check this oput you can go to:
####
    projects.exc3.dev/Particles

---

## Features

- Realtime particle simulation with configurable:
  - count, radius, jitter, friction, momentum, max speed
  - particle–particle interactions (repel / equilibrium)
  - lines and triangle fills connecting particles
- Black holes (BHs):
  - place, move, erase
  - attract (black) or repel (white) polarity
  - wormholes (paired BHs): entrance (attract) + exit (repel)
  - BHs can absorb particles and grow (optional)
  - BH–BH interaction respects polarity (repel vs attract)
- Fields:
  - Wind (directional), Vortex (spin), Radial (push/pull)
  - place and erase fields on canvas, configure radius & strength
  - Wind direction: 0 = down, 90 = right, 180 = up, 270 = left
- Mouse actions:
  - Attract / Repel / Move with radius and strength
  - Hover mode, “equal effect” toggle, left-click/right-click behavior
- Debug visuals:
  - Velocity arrows per-particle with arrow length scaled by speed
  - Heatmap: accumulative heat buffer showing where particles spend time (cold→hot colors configurable)
  - Two-color speed map option (map speed to colors via hex values)
  - Trails via alpha decay on an offscreen canvas
- Full Export/Import:
  - Save complete scene + UI state to JSON and restore later
  - Exports every single setting, fields, black holes, particles, debug colors, and engine state
  - Filename format: `particle-config-<ISO-timestamp>.json`
- Many UI controls and keyboard shortcut (`C` toggles Settings)

---

## Controls & UI

- Settings ▾ — opens settings panel
- Export — save full configuration to JSON
- Import — load previously exported JSON
- Settings Tabs: General, Mouse, Physics, Visuals, Black Holes, Fields, Debug

---

## Export / Import format

Exported JSON contains:
- `meta` — versioning and timestamp
- `engine` — internal engine state (dimensions, unique id)
- `particles` — full array of particle objects (id, x, y, vx, vy, r, etc.)
- `blackholes` — BH objects (id, x, y, r, strength, polarity, mass, vx, vy, destroy, opaque, _emit)
- `wormPairs` — wormhole pairs linking BH IDs
- `fields` — field objects (id, type, x, y, radius, strength, dir)
- `ui` — every UI control value (colors, toggles, values)
- `debug` — heatmap colors, trail settings, arrow scale, etc.

---

## Heatmap & Trails

- Heatmap uses an offscreen canvas that acts as a persistent “heat buffer”.
- Each particle stamps intensity proportional to its speed onto this buffer.
- The buffer slowly decays (fade) every frame so the map shows recent particle activity (trail-like).
- The heatmap is colorized by interpolating between `cold` and `hot` hex colors (configurable).
- You can also choose a speed-color mapping (map two hex colors to “slow” and “fast”).
- Adjust heat decay, stamp size, and reference speed in the Debug tab to tune the look.

---

> [!WARNING]
> This engine specificaly was made to not to have limits,
> Furthermore do not be reckless. Things will crash!
