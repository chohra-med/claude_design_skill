# Verify rules (step 7)

The step everyone skips. Read the generated output back against the foundation. This is the anti-hallucination check, pointed at UI. Two minutes, and it is the difference between "looks right" and "is right."

## Run through every item

- **Tokens only.** No invented hex, rgb, or named CSS colors. Every value traces to `design/tokens.ts`.
- **One accent.** The accent appears on the primary CTA and active states only. No accent fills, no gradients.
- **One primary action per screen.** If two buttons compete, one gets demoted to a text link.
- **Spacing on the 8pt scale.** No 13px, no 27px. Gaps and padding come from the scale.
- **Radius from tokens.** Cards at the card radius, pills/dots at the pill radius. No stray values.
- **No stray shadows / glassmorphism.** Only the single allowed modal elevation.
- **States present.** Loading, empty, and error exist where the screen needs them, not just the happy path.
- **Accessibility held.** Contrast, target sizes, labels, focus states (see a11y-checklist).
- **Product-specific rules.** Any rules added to the `CLAUDE.md` design block are respected.

## On any failure

Name the specific violation, fix it (or re-prompt `/design` with the violation called out), and re-run this list. Do not ship UI that fails a rule just because it "looks fine."
