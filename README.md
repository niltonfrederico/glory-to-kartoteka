<!-- markdownlint-disable MD041 MD013 -->

<p align="center">
  <a href="README.pt-br.md">
    <img src="https://img.shields.io/badge/leia%20em-portugu%C3%AAs-6fa86f?style=for-the-badge" alt="Leia em Português">
  </a>
</p>

```
┌──────────────────────────────────────────────────────────────────────────┐
│ ДОКУМЕНТ № .........: 001                                                │
│ TITLE ..............: glory-to-kartoteka                                 │
│                       (Картотека · the card index)                       │
│ CLASSIFICATION .....: OPEN · FOR EVERY VAULT OF THE SUITE                │
│ DIRECTORATE ........: Standards (Стандартизация)                         │
│ APPROVED BY ........: Director Norman                                    │
│ EFFECTIVE DATE .....: 2026-10-25                                         │
└──────────────────────────────────────────────────────────────────────────┘
```

## СВОДКА · TL;DR

The **Obsidian** theme of the Mashinograd / NIRVYTEKH bureau suite: theme name
`Nirvytekh`, built from the tokens of [`glory-to-design`](https://github.com/niltonfrederico/glory-to-design),
the suite's design standard. Warm near-black field, gold for focus, stamp red for
decisions, mono chrome and a sans body; light mode is the paper form. Three optional
snippets dress Kanban, Bases and Dataview in the same grammar.

The spec, with every component drawn, is `glory-to-design/showcase/obsidian.html`
(Standard № 004).

## УСТАНОВКА · Install

```sh
python3 tools/install.py --vault ~/vault          # one vault
python3 tools/install.py --all --dry-run          # every registered vault already on Nirvytekh; look first
```

Or by hand: copy `theme.css` and `manifest.json` into `<vault>/.obsidian/themes/Nirvytekh/`,
and the files in `snippets/` into `<vault>/.obsidian/snippets/`. Then, in Obsidian,
Settings › Appearance › Themes › **Nirvytekh**, and enable the `g2-*` snippets you want.
Pick **Dark** for the bureau or **Light** for paper; leave "adapt to system" off.

Fonts are not embedded. For the full set install PT Sans, PT Serif and JetBrains Mono;
without them the stacks fall back to the system faces.

## СБОРКА · Build

```sh
python3 tools/build.py            # sync tokens from ../glory-to-design, gate on hex, write theme.css
python3 tools/build.py --check    # exit 1 when theme.css is stale
```

`theme.css` is generated: `tokens/tokens.obsidian.css` (the contract `glory-to-design`
emits) followed by `src/theme.css` (the component layer). Edit the second, never the first
or the bundle. A colour is a token or it does not exist.

## АРХИВ · Documents

| Shelf | When to open it |
|---|---|
| [`DESIGN.md`](DESIGN.md) | Theme-level decisions and where the system-level ones are. |
| [`CLAUDE.md`](CLAUDE.md) | Layers, rules of the house, state of the work. |
| `glory-to-design/showcase/obsidian.html` | The spec: every component, the contract map, the Kanban and Bases recipes. |

## ОТКАЗ · Disclaimer

The aesthetic is loosely inspired by *Papers, Please* (© Lucas Pope / 3909 LLC) in
atmosphere only. No code, asset, name or symbol from that game, or from any real state,
appears here.

## ЛИЦЕНЗИЯ · License

[GNU Affero General Public License v3.0](LICENSE), as the rest of the suite.
