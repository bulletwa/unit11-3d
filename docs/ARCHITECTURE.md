# Architecture

`index.html` is one file with three `<script>` blocks, in this order:

1. **Three.js** (minified, bundled inline).
2. **OrbitControls** (adapted copy) – drives the free 3D, Plan and Entrance views, including one-finger rotate and two-finger pinch/pan.
3. **App script** – the scene and all behaviour.

## App script outline

| Area | What it does |
|---|---|
| Renderer setup | Creates the WebGL renderer; caps pixel ratio; detects touch (`TOUCH`) |
| Scene build | Walls (`wallDefs`, `buildWall`), floors, openings, furniture and fixtures from the plan |
| Interactives | `doorList`, `sliderList`, `interactives`, `fixtureList`; each has `use()` and `label()` |
| Views | `setView()`, `enterView()`, camera presets for 3D / Plan / Entrance |
| Walk mode | `startWalk()`, `stopWalk()`, `stepWalk()`, `blocked()` (wall and furniture colliders), `applyLook()` |
| Door physics | Spring-damper hinges, push-to-open, doors that will not close on you |
| Prompt | `updatePrompt()` picks the nearest usable object in front of you (`focusDoor`) |
| Lighting | Baked lighting ("Preparing lighting…" on load), ceiling and accent light sets |
| Audio | Web Audio sounds for doors, taps etc. (`ensureAudio()`, `toggleMute()`) |
| Touch controls | `initTouchControls()` – see [TOUCH_CONTROLS.md](TOUCH_CONTROLS.md) |
| Render loop | Renders on demand: `wake()` restarts it on any input or animation |

## Editing tips

- Plan geometry lives in the scene-build section; units are feet (25 px per foot on the source plan).
- Keep the file self-contained: avoid external scripts so the page works offline and on any static host.
- After changes, test: desktop keyboard + mouse, a phone-sized viewport with touch, and the dark colour scheme.

## Hosting

Static hosting only. GitHub Pages serves `index.html` from the `main` branch root.
