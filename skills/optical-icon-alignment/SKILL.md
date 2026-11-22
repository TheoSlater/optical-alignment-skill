---
name: optical-icon-alignment
description: Center icons optically, not mathematically. Use when placing, centering, or aligning icons inside buttons, badges, avatars, circles, or toolbars, or when an icon "looks off-center" even though its box is centered.
metadata:
  version: "0.1.0"
---

# Optical icon alignment

Always center icons based on their **weight and size**, and align by **optical** center, not mathematical (bounding-box) center.

## Rules

1. **Start from the container's true center.** Use flex/grid centering or `50%` offsets, then measure.
2. **Judge the icon's visual mass, not its box.** Heavy, filled, or asymmetric shapes (a pencil's diagonal, a trash can's flat top with a narrow body) carry weight to one side. Their bounding box can be centered while they still look off.
3. **Nudge in small steps.** Use `0.25px` to `0.5px`. Never move more than `1px` without a reason.
4. **Nudge, don't re-layout.** Apply the offset with `transform: translate(x, y)` (or a margin) on the icon only. Keep the container and its padding unchanged.
5. **Check at 1x and 2x.** Half-pixel nudges can blur on low-DPI screens. If the result is soft, round to the nearest whole pixel.
6. **Use the same nudge for the same icon everywhere.** Record it once (for example, a token or icon-level prop) so every instance matches.

## Procedure

1. Center the icon mathematically in its container.
2. Look at it at actual size. Ask: does it look centered, or does it sit high, low, left, or right?
3. Nudge `x` and `y` in `0.25px` steps until it looks centered. Stop at the first point it looks right.
4. Confirm the nudge is the smallest that works. Prefer `0` on an axis that already looks centered.
5. Apply the nudge as a named constant or per-icon offset, not an inline magic number.

## Reporting

Report each icon's nudge in this format:

```
Icon        Container   nudge x    nudge y
pencil      circle      +0.50 px   -0.50 px
trash       circle       0.00 px   -0.25 px
```

## Example

A 24px outline icon in a 48px circle:

- **Pencil-in-square:** centered by box, but the pencil's diagonal pulls the eye up-right. Nudge `x +0.5`, `y -0.5`.
- **Trash can:** symmetric in x, but the heavy base and flat lid sit low. Nudge `x 0`, `y -0.25`.
