# DESIGN — КАРТОТЕКА

What is decided at the theme level. Principles, the token model, the Obsidian surface
spec and the system-wide decisions are in `glory-to-design/DESIGN.md` and
`glory-to-design/showcase/obsidian.html`; this file does not repeat them.

## Where decisions live

| Question | Where |
|---|---|
| Which colour is which, and why | `glory-to-design/tools/derive_tokens.py` (seeds), `DESIGN.md` → Token model |
| How a g2 token reaches an Obsidian variable | `tokens/tokens.obsidian.css` header, spec §1 |
| What each component looks like and why | spec §2–§9; the section comments in `src/theme.css` |
| Why the theme is in its own repo, body is sans, light is paper, plugins are snippets | `glory-to-design/DESIGN.md` → Decisions, 2026-10-25 |
| What the theme deliberately does not do | spec §10 |

## Theme-level decisions

| Date | Decision | Alternatives rejected | Why |
|---|---|---|---|
| 2026-10-25 | **Theme name stays `Nirvytekh`**; the repo is `glory-to-kartoteka`. | rename the theme to Kartoteka | Seven vaults already select `Nirvytekh` in `appearance.json`; keeping the name makes the upgrade a file copy. The bureau's name on the theme, the card index on the repo. |
| 2026-10-25 | **Tokens are vendored**, synced by `tools/build.py` from the sibling checkout. | `@import` of a file outside the vault (Obsidian cannot); a git submodule | Obsidian loads one `theme.css`; the vault has no build. A committed copy is honest about what shipped. |
| 2026-10-25 | **`theme.css` is generated and committed.** | generate on install only | Obsidian's community theme format wants `theme.css` at the repo root; a fork or a BRAT install must work without Python. |
| 2026-10-25 | **Callout types for the four stamps**: `approved` `rejected` `order` `review`, Cyrillic eyebrow, icon hidden. The standard types (`success`, `failure`/`danger`, `todo`, `warning`) map onto the same four and keep their icon. | only the standard types; a stamp as an SVG badge | A stamp in a note is a word, as in the TUI. The custom types cost one line of markdown and read in any other theme as a plain note. |
| 2026-10-25 | **`--font-interface-theme` is sans**, mono applied per chrome selector. | mono interface (the June theme) | Settings descriptions and dialogs are prose; mono walls are the owner's reading cost. The explorer, tabs, keys and status bar get mono explicitly. |
| 2026-10-25 | **Tags are outline chips; blockquote is a note (sage)**; buttons sentence case; `hr` is a double rule. | the June theme's gold-filled tags, red quote rule, uppercase `mod-cta`; a box-shadow "double rule" | Field quiet, accent as event; red is a decision; no shadows anywhere, so the double rule is a real `border-style: double`. |
| 2026-10-25 | **Fonts are not embedded.** | `@font-face` data URIs | Every vault is on one machine with PT Sans, PT Serif and JetBrains Mono installed. Revisit for a second machine. |

## Rejected for now

- Styling make.md (spaces, stickers): undocumented DOM, and the gold icon set is the vault's.
- A `g2-hunt.css` here: that vocabulary is `the.hunt`'s. Recipe in the spec §7, §8.
- Live-preview parity for every rule: the editor (`.cm-*`) gets headings, code, quotes, tags
  and the active line; the rest is reading view first. Add `.cm-*` rules when a miss is seen.
