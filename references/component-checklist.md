# Component checklist (step 2)

Define the parts before the screens. A screen built from undefined components forces the model to invent a button six different ways. A screen built from defined components is just arrangement.

## For the brief, list the components needed, then define each one

Typical primitives (only build what the brief actually uses):

- **Button** — variants: primary, secondary, text/link, destructive. States: default, hover/press, focus, disabled, loading.
- **Input / field** — states: default, focus, filled, error, disabled. Include label + helper/error text slots.
- **Card / surface** — padding from the 8pt scale, radius from tokens, one elevation max.
- **List row** — leading icon/avatar slot, title + subtitle, trailing action/chevron; pressed + selected states.
- **Stepper / progress** — prefer no visible number where it raises drop-off; show advancement instead.
- **Chip / tag / badge** — single accent only on active.
- **Modal / sheet** — the only place a soft elevation shadow is allowed.

## For every component, pin down

1. Which tokens it uses (color, spacing, radius) — by name, never raw values.
2. Its variants (what changes between them).
3. Its full state set: default, hover/press, focus, disabled, loading, error, empty where relevant.
4. One primary action rule: a screen using these still gets exactly one primary button.

## Gate

Do not compose screens (step 3) until each needed component has its variants + states defined against the tokens.
