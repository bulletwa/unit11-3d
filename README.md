# Unit 11 3D

An interactive 3D walkthrough of Unit 11 (Tower 3, 3BHK), built from the floor plan. It is a single self-contained web page (`index.html`): Three.js is bundled inline, so there is nothing to install and no server-side code.

**Live page:** https://bulletwa.github.io/unit11-3d/

## Features

- **Views:** Walk (first person), 3D (free orbit), Plan (top-down), Entrance.
- **Walk mode:** collision with walls and fixtures, doors that swing open as you push them, running.
- **Interactive items:** doors, taps, commodes, fridge, microwave, cabinets and drawers.
- **Toggles:** ceiling, labels, ceiling lights, accent lights, all doors, sound, reset view.
- **Works on desktop, phone and tablet** (see controls below).

## Controls

| Action | Desktop | Phone / tablet |
|---|---|---|
| Rotate (3D) | Drag | Drag with one finger |
| Zoom (3D) | Scroll | Pinch |
| Pan (3D) | Right-drag or Shift + drag | Drag with two fingers |
| Walk | `1` or **Walk** button | **Walk** button |
| Move (Walk) | `W` `A` `S` `D` / arrows | Joystick, bottom-left |
| Run | `Shift` | Push joystick to the edge, or **Run** button |
| Look (Walk) | Mouse (click the view first) | Drag anywhere else on the view |
| Use (Walk) | `E` | Round **Use** button that appears near something usable |
| Exit Walk | `Esc` | **Exit** button |
| Views | `2` 3D, `3` Plan, `4` Entrance | Top bar buttons |
| Other | `C` ceiling, `N` labels, `L`/`K` lights, `M` sound, `R` reset, `H` help | Bottom bar buttons, **?** for help |

## Run it locally

Open `index.html` in a desktop browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

Note: phones cannot run a `.html` file opened from the Files app. Open the hosted link above in Safari or Chrome instead.

## Documentation

- [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) – how the page is organised and where to change things.
- [docs/TOUCH_CONTROLS.md](docs/TOUCH_CONTROLS.md) – how touch support works and its limits.

## Notes

- Walls and openings follow the Tower 3 plan for Unit 11. The ceiling height (10 ft 10 in) is assumed because the plan does not give one.
- Rendering is capped at a lower pixel ratio and uses no antialiasing on touch devices to keep it smooth on phones.
