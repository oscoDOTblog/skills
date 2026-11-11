---
name: sao-ux-web
description: SAO main-menu inspired web theme. Use when styling a dashboard or launcher with an Aincrad menu look: amber accents, light panels on charcoal, HP-bar statuses, angular cuts, dial switchers.
---

# SAO UX for Web

Theme language derived from the SAO main-menu screenshot
(`config/refs/maxresdefault-3842694262.jpg`): amber-orange selection color,
white menu cards with dark text on a charcoal backdrop, slim side rail,
circular dial controls, condensed uppercase type. All CSS-only, no copied
artwork or external fonts.

## Palette

```css
--sao-bg: #2f2f33;          /* page backdrop (charcoal, flat) */
--sao-rail: #f5a800;       /* left edge rail */
--sao-rail-deep: #c07f00;
--sao-panel: #f4f4f5;      /* cards, header, device cells */
--sao-panel-2: #e3e3e7;
--sao-ink: #232529;        /* text on light panels */
--sao-muted: #5f636b;      /* secondary text on light */
--sao-line: #c6c9d0;       /* borders on light */
--sao-amber: #f5a800;      /* accent: selections, active states */
--sao-amber-deep: #b87a00; /* accent hover / text on light */
--sao-amber-ink: #ffffff;  /* text on amber fills */
--sao-dark-panel: #1e2024; /* controls sitting on the dark page */
--sao-dark-line: #4a4e57;
--sao-page-muted: #a9afb9; /* secondary text on the dark page */
--sao-page-faint: #7c828c;
```

Status colors (chosen to read on light panels):

```css
--sao-green: #0b8a4e;      /* online  */
--sao-amber-text: #a86a00; /* timeout  */
--sao-red: #d7263d;        /* offline  */
--sao-gray: #7a7f88;       /* unknown  */
```

Type: `--font-hud: "Arial Narrow", "HelveticaNeue-CondensedBold",
"Franklin Gothic Medium", "Segoe UI", system-ui, sans-serif` for headings,
names, buttons, and status labels. Always uppercase with
`letter-spacing: 0.1–0.14em` (loading states up to `0.3em`).

## Motifs

- **Amber means selected/active.** Filled amber pills, amber top edges on
  light panels, amber diamonds (`◆`) before titles. Never cyan.
- **Light panels on charcoal.** Cards, device cells, and the header are
  near-white gradients; the page stays flat charcoal with a soft amber
  radial glow at the top.
- **Side rail.** A slim fixed amber gradient bar on the left viewport edge
  echoes the menu's side band.
- **Angular cuts, one round exception.** Panels and buttons use small
  `clip-path` corner cuts (8–22px). The only round shapes are the dial-style
  option groups (`border-radius: 9999px`) and HP bar dots are never used.
- **HP-bar status.** Skewed (`skewX(-16deg)`) track on a light `#d4d6db`
  groove; fill width encodes vitality: online 100% green, timeout 55%
  amber, offline 12% red, unknown 20% gray. Text label beside it carries
  the exact state so color is never the only signal.
- **Loading reads "Link Start…"** in spaced amber capitals with a gentle
  pulse (disabled under `prefers-reduced-motion`, like all animation).

## Component rules

- **Header:** light panel, dark title with amber diamond, 3px amber top
  edge, large corner cut. Primary action is a filled amber clipped button.
- **Cards:** light gradient, ink name in HUD font, muted tabular port.
  Offline cards dim to ~45% opacity. Hover/focus shows an amber
  `drop-shadow` glow only (no glow at rest, no borders on clipped edges).
- **Device cells:** light panel with amber top edge and amber diamond
  before the name; host line muted.
- **Switcher groups:** dark rounded-full strip, dark-line border; active
  option is a filled amber pill with white text.
- **Focus mode:** all groups stacked one after another with large cards,
  no dropdown picker. Filters apply across every group.
- **Focus visibility:** clipped elements can't show outlines (clip-path
  trims them), so give them a `drop-shadow` amber glow instead.
  Unclipped controls keep a 3px amber outline with 2px offset.

## Constraints

- Touch targets stay 44–48px minimum (tablet + Quest Browser).
- No external images, icon packs, or webfonts; glyphs like `◆` are fine.
- All launch URLs are `https://`; `tcp` services get no URL.
- Status is HTTP 2xx–4xx when the service answers HTTP(S), else a
  ping-like TCP port check (open port reads online — covers TLS-only and
  self-signed services); timeouts and 5xx still read as-is.
- Keep per-component cut sizes varied and glow restrained so the theme
  reads as crafted, not stamped.
