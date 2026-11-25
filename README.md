# Spacing Scale Generator

A small tool for designers and developers who want a consistent spacing system. Pick a base unit and a scale type, see the scale update live, and copy it as CSS variables, a Tailwind config snippet or JSON.

It's a single HTML file: no build step, no sign-up, nothing to install.

## Use it

Download [`index.html`](index.html) and open it in your browser (double-click it, or drag it onto a browser window). It works offline; an internet connection is only needed for the Inter font, and it falls back to your system font without one.

## Features

- **Base unit**: 4px, 8px, or any value from 1 to 64px.
- **Scale types**
  - **Linear**: each step adds one base unit (4, 8, 12, 16…).
  - **Multiplier**: each step is the previous one × a ratio, with presets for 1.25, 1.333, 1.5, 1.618 and 2, or your own.
  - **Custom**: comma-separated multipliers of the base, like `0.5, 1, 1.5, 2, 3, 4`.
- **6 to 12 steps** for linear and multiplier scales.
- **Token names**: numbered (`space-1`), T-shirt sizes (`space-xs`, `space-sm`, `space-md`…), or your own names, with an optional prefix.
- **Live preview**: each token shown as a bar with its name, px value and rem value. The rem root font size is adjustable (16px by default).
- **In use**: two example cards spaced with your scale, with pickers for card padding and gaps, and a "Show spacing" overlay that colours each kind of space.
- **Whole pixels**: every value is rounded to the nearest whole pixel, and values that aren't multiples of 4 are highlighted.
- **Friendly validation**: invalid input gets a plain-language message, and the last valid scale stays on screen until it's fixed.

## Export formats

The Copy button exports the scale in the format chosen in the tabs. With the default 4px linear scale:

**CSS variables**

```css
:root {
  --space-1: 0.25rem; /* 4px */
  --space-2: 0.5rem; /* 8px */
  --space-3: 0.75rem; /* 12px */
  /* … */
}
```

**Tailwind**

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      spacing: {
        'space-1': '0.25rem', // 4px
        'space-2': '0.5rem', // 8px
        // …
      },
    },
  },
};
```

Tip: clear the prefix to get plain keys like `md`, so your classes read `p-md` instead of `p-space-md`.

**JSON**

```json
{
  "space-1": { "px": 4, "rem": 0.25 },
  "space-2": { "px": 8, "rem": 0.5 }
}
```

## Accessibility

- All controls are real form elements with labels, and they work with the keyboard. The format tabs support the arrow keys.
- Errors are linked to their fields and announced to screen readers.
- Values that aren't multiples of 4 are marked with more than colour alone: screen readers announce them and hovering shows a tooltip.
- Respects `prefers-reduced-motion`, and the layout works at phone widths.
