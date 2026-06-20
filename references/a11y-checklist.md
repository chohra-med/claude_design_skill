# Accessibility checklist (step 5)

Run this as a PRE-generation gate so the model produces accessible UI by default, instead of you retrofitting it after.

## Contrast
- Body text vs its background: at least 4.5:1.
- Large text (>= 24px or 19px bold) and UI/icon affordances: at least 3:1.
- The single accent must pass contrast on whatever it sits on (CTA text on the accent fill).

## Touch / hit targets (mobile especially)
- Interactive targets at least 44x44pt (iOS) / 48x48dp (Android).
- Spacing between adjacent targets so they are not mis-tapped.

## Semantics
- Real roles: buttons are buttons, links are links, headings are headings in order.
- Every input has a programmatic label (not placeholder-only).
- Icon-only controls have an accessible name (aria-label / accessibilityLabel).
- Images that carry meaning have alt text; decorative ones are marked decorative.

## States, not just color
- Never signal state with color alone (error, active, selected): pair with text, icon, or shape.
- Visible focus state on every interactive element.

## Motion
- Respect reduced-motion; keep transitions 200-240ms; nothing that flashes.

## Gate
Fold these into the generation prompt for step 6 so the output is accessible on the first pass. Re-check them in step 7.
