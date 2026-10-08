# Wheelchair lift – interactive model

An interactive 3D view of a scissor-lift mechanism (baseplate, two armrests, four scissor arms and ten pins).

- **Drag** to rotate, **scroll** to zoom, **right-drag** or **Shift-drag** to pan, **double-click** to reset the view.
- Use the bar at the bottom to scrub between fully retracted and fully extended, or press play (or Space) to cycle.
- **Add wheelchair** flies a wheelchair in from below (a different colour every time) and drops the lift onto its seat.
  Everything above keeps working with the wheelchair attached. **Remove wheelchair** pops it off and lets it fall away.
- On a touch screen: one finger rotates, pinch zooms, two fingers pan.

## Files

- `index.html` – the whole viewer (plain WebGL 2, no libraries or build step).
- `lift.bin` – the part meshes and colours, converted from the Fusion 3MF export. Millimetres, Z up.
- `chair.bin` – the wheelchair mesh, converted from its STL and already scaled and placed so its seat sits under the lift.
  The wheelchair is drawn 13.3 times larger than the STL (so the lift appears at 7.5 % of its Fusion size next to it);
  at that size the lift clears the armrests by about 6 mm on each side through its whole travel.

The motion is computed in the page from the same geometry as the Fusion joints: the arms pivot on the fixed holes,
the sliding pins travel along the slots, and the arm angle runs from 22° (retracted) to 74° (extended).

## Running locally

The page loads `lift.bin` with `fetch`, so open it through a local server rather than as a file:

```
python -m http.server
```

then visit http://localhost:8000.
