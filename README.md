# claude-design-idea-to-ready

A Claude Code skill that takes a UI from a one-line idea to on-brand, shippable design, **in the right order**: brand foundation first, then components, screens, interactions, accessibility, and only then generation with `/design`.

![Five screens from one app, all generated through this pipeline — one brand, because none of them were allowed to leave the tokens.](assets/on-brand-output.png)

Most AI-generated UI looks the same because it is handed zero constraints. This skill front-loads the constraints (design tokens + a `CLAUDE.md` design-rules block) so the model can only produce on-brand output, then runs the generation last and verifies it against the rules.

## Before / after

Same screen, same prompt. The difference is the foundation the model was given before it generated.

| Generic (no constraints) | On-brand (this pipeline) |
|---|---|
| ![Before: generic violet card stack](assets/before.png) | ![After: refactored against the tokens](assets/after.png) |

It works because the brand lives in two files the model reads first:

![The design tokens as a real screen: palette + type scale, the single source of truth](assets/tokens.png)

## The pipeline

0. Idea → brief (one job, who, the one action)
1. **Foundation** — `design/tokens.ts` + a `## Design rules` block in `CLAUDE.md`
2. **Components** — defined against the tokens, before any screen
3. **Screens** — composed from components, one primary action each
4. **Interactions + states** — loading, empty, error, motion
5. **Accessibility** — a pre-generation gate
6. **Generate** with `/design`, reading the tokens
7. **Verify** the output against the design rules, fix, re-run

## Install

**Claude Code (project or user skills):**
```bash
git clone git@github.com-personal:chohra-med/claude_design_skill.git
# then copy into your skills dir, e.g.
cp -r claude_design_skill ~/.claude/skills/claude-design-idea-to-ready
```

Or drop the folder into a UAMOS-style memory bank's `skills/` directory; it composes with the rest and self-triggers on design tasks.

## Files

- `SKILL.md` — the skill (pipeline + triggers)
- `references/foundation-templates.md` — paste-ready tokens + design-rules block
- `references/component-checklist.md` — components + states to define first
- `references/a11y-checklist.md` — the pre-generation accessibility gate
- `references/verify-rules.md` — the post-generation verification checklist

## License

MIT. By [@malik_chohra](https://x.com/malik_chohra) · [Code Meet AI](https://codemeetai.substack.com).
