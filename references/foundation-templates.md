# Foundation templates (step 1)

The two files that decide 80% of the result. Scaffold these before generating any UI.

## File 1 — `design/tokens.ts`

One source of truth. Names, never raw hex in components. Swap the values for the brand; keep the shape.

```ts
export const tokens = {
  color: {
    bg:      "#0E0E10", // app background
    surface: "#1C1C1F", // cards, elevated panels
    text:    "#FAFAF8", // primary text
    muted:   "#A0A0A8", // secondary text
    accent:  "#3BA9AE", // ONE accent — CTAs + active states only
    border:  "#26262A", // hairlines
  },
  radius: { card: 12, pill: 999 },
  space:  [0, 4, 8, 12, 16, 24, 32, 48], // 8pt scale, no arbitrary gaps
  font:   { display: "Bricolage Grotesque", body: "Inter", mono: "JetBrains Mono" },
};
```

Mobile (React Native): same object, consumed by a `theme` provider or a `useTokens()` hook instead of CSS variables.

## File 2 — `## Design rules` block in `CLAUDE.md`

The rulebook. This is what stops the model reaching for its defaults.

```md
## Design rules — read before generating any UI
- Use ONLY the values in design/tokens.ts. Never invent a hex.
- One accent color. It appears on the primary CTA and active states.
  Never as a fill, never as a gradient.
- Monochrome base: one background, one text color, one muted gray. That is the palette.
- Spacing comes from the 8pt scale. No 13px, no 27px.
- Radius: 12 for cards, 999 for pills and dots.
- One primary action per screen. If two buttons compete, demote one to a text link.
- No drop shadows except a single soft elevation on modals. No glassmorphism.
- Add any product-specific rules here (e.g. "never use the danger color on a success state").
```

## Gate

Do not advance to components (step 2) until both files exist and the user has confirmed the token values. If they are missing, write them first and stop for an OK.
