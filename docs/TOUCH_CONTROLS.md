# Touch controls

Walk mode was written for a keyboard and mouse, so touch devices get an extra layer. It switches on when `matchMedia('(pointer:coarse)')` is true (the `TOUCH` constant), which also adds the `touch` class to `<body>`.

## What replaces what

| Desktop input | Touch replacement | Implementation |
|---|---|---|
| `W A S D` / arrows | Joystick (`#joy`) | Writes `KeyW/KeyA/KeyS/KeyD` into the same `down` set that `stepWalk()` reads, so movement code is unchanged |
| `Shift` (run) | **Run** button, or joystick pushed to the edge | Adds `ShiftLeft` to `down` |
| Mouse look / pointer lock | Drag on the canvas | `pointerdown/move/up` on `#c` with `pointerType !== 'mouse'`, updating `yaw` and `pitch` |
| `E` (use) | Round **Use** button (`#useBtn`) | Shown by `updatePrompt()` when `focusDoor` is set; calls `focusDoor.use()` |
| `Esc` (exit) | **Exit** button (`#exitBtn`) | Calls `stopWalk()` |

## Other touch changes

- Pointer lock is skipped on touch (`tryLock()` returns early), and the "click the view" hint is hidden.
- The help panel shows touch wording (`.tc` items) instead of keyboard wording (`.kb` items).
- Layout: `100dvh` canvas, `viewport-fit=cover`, safe-area padding, 36-42 px tap targets, a horizontally scrolling bottom bar.
- Performance: pixel ratio capped at 1.5 and antialiasing off on touch devices.

## Limits

- Tested only in a desktop browser emulating a phone viewport, with synthetic pointer events. Please test on a real phone and tablet.
- Detection is by primary pointer. A laptop with a touch screen counts as a desktop; an iPad with a trackpad may still count as touch.
- Gyroscope look and tap-on-object interaction are not implemented.
