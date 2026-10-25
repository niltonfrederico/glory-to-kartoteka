<!-- markdownlint-disable MD041 MD013 -->

<p align="center">
  <a href="README.md">
    <img src="https://img.shields.io/badge/read%20in-english-6fa86f?style=for-the-badge" alt="Read in English">
  </a>
</p>

```
┌──────────────────────────────────────────────────────────────────────────┐
│ ДОКУМЕНТ № .........: 001                                                │
│ TÍTULO .............: glory-to-kartoteka                                 │
│                       (Картотека · o fichário)                           │
│ CLASSIFICAÇÃO ......: ABERTO · PARA TODO VAULT DA SUÍTE                  │
│ DIRETORIA ..........: Padrões (Стандартизация)                           │
│ APROVADO POR .......: Diretor Norman                                     │
│ DATA DE VIGÊNCIA ...: 2026-10-25                                         │
└──────────────────────────────────────────────────────────────────────────┘
```

## СВОДКА · Resumo

O tema **Obsidian** da suíte de bureaus Mashinograd / NIRVYTEKH: nome do tema
`Nirvytekh`, construído a partir dos tokens do [`glory-to-design`](https://github.com/niltonfrederico/glory-to-design),
o padrão de design da suíte. Campo quase-preto quente, dourado para foco, vermelho de
carimbo para decisões, chrome mono e corpo sans; o modo claro é o formulário paper. Três
snippets opcionais vestem Kanban, Bases e Dataview na mesma gramática.

A spec, com todo componente desenhado, é `glory-to-design/showcase/obsidian.html`
(Стандарт № 004).

## УСТАНОВКА · Instalação

```sh
python3 tools/install.py --vault ~/vault          # um vault
python3 tools/install.py --all --dry-run          # todo vault registrado que já usa Nirvytekh; olhe antes
```

Ou à mão: copie `theme.css` e `manifest.json` para `<vault>/.obsidian/themes/Nirvytekh/`,
e os arquivos de `snippets/` para `<vault>/.obsidian/snippets/`. Depois, no Obsidian,
Settings › Appearance › Themes › **Nirvytekh**, e ligue os snippets `g2-*` que quiser.
Escolha **Dark** para o bureau ou **Light** para o paper; deixe "adapt to system" desligado.

As fontes não vêm embutidas. Para o conjunto completo instale PT Sans, PT Serif e
JetBrains Mono; sem elas as stacks caem nas fontes do sistema.

## СБОРКА · Build

```sh
python3 tools/build.py            # sincroniza tokens de ../glory-to-design, barra hex, escreve theme.css
python3 tools/build.py --check    # sai com 1 quando theme.css está desatualizado
```

`theme.css` é gerado: `tokens/tokens.obsidian.css` (o contrato que o `glory-to-design`
emite) seguido de `src/theme.css` (a camada de componentes). Edite o segundo, nunca o
primeiro nem o bundle. Cor é token ou não existe.

## АРХИВ · Documentos

| Prateleira | Quando abrir |
|---|---|
| [`DESIGN.md`](DESIGN.md) | Decisões no nível do tema e onde estão as do sistema. |
| [`CLAUDE.md`](CLAUDE.md) | Camadas, regras da casa, estado do trabalho. |
| `glory-to-design/showcase/obsidian.html` | A spec: todo componente, o mapa do contrato, as receitas de Kanban e Bases. |

## ОТКАЗ · Aviso

A estética é vagamente inspirada em *Papers, Please* (© Lucas Pope / 3909 LLC) apenas
na atmosfera. Nenhum código, asset, nome ou símbolo daquele jogo, nem de qualquer
estado real, aparece aqui.

## ЛИЦЕНЗИЯ · Licença

[GNU Affero General Public License v3.0](LICENSE), como o resto da suíte.
