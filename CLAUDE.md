# glory-to-kartoteka

> КАРТОТЕКА · НИРВЫТЕХ — the **Obsidian** theme of the Mashinograd / NIRVYTEKH bureau
> suite (`glory-to-*`). The vault is the bureau's card index.

## What it is

An Obsidian theme (`theme.css` + `manifest.json`, name **Nirvytekh**) plus three CSS
snippets, built from the tokens of `glory-to-design`. It is the fourth surface of that
design system (GUI, TUI, WATCH, OBSIDIAN); the **spec lives there**, in
`showcase/obsidian.html`, and so do the principles and dated decisions (`DESIGN.md`).
This repo is the product: the theme a vault installs.

Replaces the June 2026 `Nirvytekh` theme that lived in `zoloto-durakov/_code/nirvytekh/`
and was copied by hand into every vault. Same name, new source.

## Layers (do not re-derive)

| Path | What | Edit? |
|---|---|---|
| `tokens/tokens.obsidian.css` | Vendored copy of the contract `glory-to-design` generates: g2 tokens on `.theme-dark` / `.theme-light`, Obsidian's CSS variables mapped onto them, accent as HSL, every token as RGB, the extended palette folded onto the bureau's hues. | **Never.** `tools/build.py` syncs it from `../glory-to-design` when that repo is beside this one. A colour changes in `glory-to-design/tools/derive_tokens.py`. |
| `src/theme.css` | The component layer: mono chrome, headings, callouts as stamped notices, ledgers, chips, properties as document header, window chrome, menus, modals, notices. Tokens only. | Yes. This is the theme. |
| `theme.css` | `tokens/tokens.obsidian.css` + `src/theme.css`, bundled. What Obsidian loads. | **Never.** `python3 tools/build.py` writes it; commit the result. |
| `manifest.json` | Obsidian theme manifest. | Version bump on release. |
| `snippets/g2-kanban.css` · `g2-bases.css` · `g2-dataview.css` | One defensive snippet per plugin. Installed next to the theme, enabled per vault. | Yes. Tokens only. |
| `tools/build.py` | Sync tokens, gate on hex, bundle; `--showcase` refreshes the spec page's copy in `glory-to-design`; `--check` is the CI-style gate. | |
| `tools/install.py` | Copies theme + snippets into `--vault PATH` or `--all` (every registered vault already on Nirvytekh; `--include-others` lifts the filter). Never edits `appearance.json`. Keeps the previous `theme.css` as `theme.css.prev` once. | |
| `DESIGN.md` | What is decided at the theme level and where the system-level decisions are. | Before changing a component. |

## Rules of the house

- **A colour is a token or it does not exist.** `tools/build.py` exits 1 on a hex outside
  `tokens/`. The seeds live in `glory-to-design`; this repo never mixes a colour.
- **Contract first, selectors second.** Anything Obsidian exposes as a variable is set in the
  generated contract, not here. A selector in `src/theme.css` exists only where the contract
  has no slot (uppercase on a ledger key, the frame on a callout, the stamp eyebrow).
- **Plugin DOM never enters `theme.css`.** Kanban, Bases, Dataview: one snippet each. A plugin
  that changes its markup breaks one snippet, not the vault. A fourth plugin gets a fourth file.
- **Body is never mono.** `--font-text-theme` follows the system: PT Sans on the bureau,
  PT Serif on paper (`.theme-light`). Mono is the chrome and the code.
- **`.theme-light` is paper.** The user picks it in Settings › Appearance; "adapt to system"
  is out of canon. Never repaint light as dark.
- **Lane and value vocabularies belong to the vault.** `g2-kanban` exposes `--g2-lane`;
  `g2-bases` colours the canon's English decision words. A vault with other words maps them
  in its own snippet, with tokens, not here.
- **Gate before done.** `python3 tools/build.py --check` green, then `--all --dry-run` of the
  installer to see what a deploy would touch. A real deploy needs Obsidian closed and the
  owner's word.
- **Bureau voice in public artifacts is project convention** (this is a `glory-to-*` repo):
  READMEs carry the document header and Cyrillic labels. Code identifiers, commit messages
  and file names stay plain technical English. Commits are conventional.

## State on 2026-10-25

- Theme, snippets, build and installer written in a `glory-to-design` session and moved here
  the same day (the owner wanted the product in its own repo, as `glory-to-direktiva` is for
  Super Productivity). **Not yet installed in any vault; not yet rendered in a real Obsidian.**
  The page in `glory-to-design` was validated structurally (every `--g2-*` and contract
  variable defined, tags and braces balanced), not visually.
- Selectors for the editor, headings, callouts, tables, tags, nav, tabs, status bar are the
  June theme's (confirmed in a real Obsidian then). Selectors for menus, prompt, settings,
  notices, Bases, Kanban, Dataview are from knowledge, not measurement: expect misses on
  the first reload and fix them in `src/theme.css` or the snippet, never in `theme.css`.
- Obsidian's vault registry (`~/.config/obsidian/obsidian.json`) listed eight vaults, seven on
  the June Nirvytekh; `zoloto-durakov` is outside the registry and takes `--vault`.
- `the.hunt/.obsidian/snippets/hunt-style.css` still has raw hex for lanes and verdicts; the
  rewrite recipe is in the spec, §7 and §8.

## Open to the owner

The owner said he would organize this repo himself. Layout above is the hand-off state,
not a decision: move things, rename, add docs. Keep the three invariants (tokens vendored,
`theme.css` generated, snippets apart) or update `tools/build.py` with them.
