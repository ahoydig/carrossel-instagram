# Carrossel Instagram — Skill para Claude Code

por [@flavioahoy](https://instagram.com/flavioahoy)

Skill que gera carrosseis profissionais para Instagram via HTML renderizado como imagem (Playwright). Pipeline de 4 gates com aprovacao em cada etapa.

## O que faz

- Transforma qualquer input (URL, tweet, ideia, repo) em carrossel pronto pra postar
- 9 templates pre-definidos com classificacao viral
- 10 paletas de cores testadas
- 8 efeitos tipograficos pra headlines
- Captura screenshots automaticamente de qualquer site
- Renderiza HTML como PNG via Playwright
- Formatos: 3:4, 4:5 e 1:1

## Pipeline

```
BRIEFING & PESQUISA → CONTEUDO TEXTUAL → DIRECAO VISUAL → GERACAO FINAL
```

Cada gate exige aprovacao antes de avancar. Voce controla tudo.

## Templates disponiveis

| # | Template | Classificacao |
|---|----------|--------------|
| 1 | Revelacao | VIRAL |
| 2 | Tutorial / How-to | Educativo |
| 3 | Estudo de Caso | Autoridade |
| 4 | Listicle | VIRAL |
| 5 | Quente / Trends | VIRAL |
| 6 | Comparativo | Educativo |
| 7 | Storytelling | Engajamento |
| 8 | Polemica / Hot Take | VIRAL |
| 9 | Ferramenta / Stack | VIRAL |

## Instalacao

### 1. Copie a skill

```bash
git clone https://github.com/ahoydig/carrossel-instagram.git ~/.claude/skills/carrossel-instagram
```

Ou copie a pasta manualmente:

```bash
cp -r carrossel-instagram ~/.claude/skills/carrossel-instagram
```

### 2. Fontes (opcional)

A skill usa as fontes **Nofex** e **Crankdat**, criadas por [@flavioahoy](https://instagram.com/flavioahoy). Se voce tiver essas fontes, instale em `~/Library/Fonts/`.

Se nao tiver, a skill usa fallbacks automaticos do Google Fonts:
- Nofex → Bebas Neue
- Crankdat → Space Grotesk

### 3. Playwright

A skill usa Playwright MCP para renderizar os slides. Certifique-se de que o MCP de Playwright esta configurado no seu Claude Code.

### 4. Use

No Claude Code, diga algo como:

```
cria um carrossel sobre [seu tema]
```

A skill assume o controle e te guia pelo pipeline.

## Estrutura

```
carrossel-instagram/
├── SKILL.md                          # Definicao principal da skill
└── references/
    ├── fonts-config.md               # Configuracao de fontes e fallbacks
    ├── headline-effects.md           # 8 efeitos tipograficos CSS
    ├── palettes.md                   # 10 paletas de cores testadas
    ├── screenshot-guide.md           # Guia de captura de screenshots
    └── templates.md                  # 9 templates de carrossel
```

## Como funciona por dentro

1. **Gate 1 — Briefing:** Coleta tema, objetivo, template, formato e @handle. Pesquisa referencias se receber URL.
2. **Gate 2 — Conteudo:** Gera textos pra cada slide com tom conversacional. Aplica humanizacao anti-IA.
3. **Gate 3 — Visual:** Propoe paletas, efeito tipografico e layouts. Gera preview do slide 1.
4. **Gate 4 — Geracao:** Captura screenshots, gera HTML de cada slide, renderiza como PNG via Playwright.

## Principios de design

- **Flexbox centralizado** — elementos principais no fluxo, nunca `position: absolute`
- **Background rico** — gradiente + textura + logo real com blur (nunca gradiente liso)
- **Screenshots reais** — sempre buscar de fontes reais, nunca criar SVGs genericos
- **Crankdat comments** — frases curtas com personalidade, rotacionadas, sem parenteses
- **Portugues natural** — tom de amigo que descobriu algo bom, nunca guru ou professor

## Licenca

MIT
