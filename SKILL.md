---
name: carrossel-instagram
description: >
  Gera carrosséis profissionais para Instagram via HTML-to-Image (Playwright).
  Suporta formatos 3:4, 4:5 e 1:1. Captura screenshots automaticamente de URLs.
  Templates pré-definidos com classificação viral. Efeitos tipográficos customizáveis.
  Use quando o usuário mencionar: carrossel, carousel, criar post, post instagram,
  slides, conteúdo instagram, carrossel viral, post viral, criar carrossel,
  montar carrossel, gerar carrossel, instagram post, fazer um post.
---

# Carrossel Instagram

Gera carrosséis profissionais para Instagram via HTML renderizado como imagem (Playwright).

## Pipeline: 4 Gates

```
BRIEFING & PESQUISA → CONTEÚDO TEXTUAL → DIREÇÃO VISUAL → GERAÇÃO FINAL
```

Cada gate exige aprovação explícita do usuário antes de prosseguir. Nunca pule um gate.

---

## Gate 1: Briefing & Pesquisa

### Inputs aceitos

| Input | Ação |
|-------|------|
| URL de notícia | Abrir via Playwright, ler conteúdo, extrair pontos-chave |
| Post de Instagram | Abrir, analisar design/conteúdo, remodelar com identidade do usuário |
| Reel de Instagram | Abrir, capturar thumbnail, extrair legenda, converter em carrossel |
| Tweet/Thread | Capturar e transformar em conteúdo |
| Repo GitHub / doc | Analisar e transformar em conteúdo educativo |
| Link YouTube | Capturar thumbnail + título |
| Ideia solta / tema | Pesquisar sobre o tema, buscar referências, propor ângulos |

### Coleta obrigatória

Não avance sem: **Objetivo**, **Template** (ler `references/templates.md`), **Formato** (3:4, 4:5 ou 1:1), **@handle**, **Fontes** (ler `references/fonts-config.md` e sugerir combinações).

### Regras de conteúdo

- Zero jargão que o público não entende. Se precisa explicar o que é, não serve pro slide.
- Tom equilibrado ao comparar ferramentas. Nunca massacrar um produto pra vender outro.
- Pessoas reais com nome completo. Capturar perfil: Instagram > X > LinkedIn > GitHub.

### Gate: Apresentar resumo do briefing. Aguardar aprovação.

---

## Gate 2: Conteúdo Textual

Gerar para cada slide: título, corpo, mapa de screenshots, caption e 5 hashtags.

### Regras de copy

- **Aplicar skill `humanizer`** em toda copy. Eliminar padrões de IA.
- **Cenários concretos > features.** Mostrar o que o leitor faria, não o que a ferramenta faz.
- **Tom: amigo que descobriu algo bom.** Não guru, não professor.
- **Português conversacional brasileiro real.** Frases completas com sujeito, verbo e complemento. Nunca encurtar pra caber no slide.
- **Arco narrativo coeso.** Cada slide tem uma função na história.

Apresentar TUDO de uma vez para o usuário ver o fluxo narrativo completo.

### Gate: Usuário aprova ou ajusta textos.

---

## Gate 3: Direção Visual

Ler `references/palettes.md` e `references/headline-effects.md`.

Propor: 2-3 paletas, efeito tipográfico, mapa de layouts, preview do slide 1.

### Gate: Usuário aprova paleta, efeito e estilo.

---

## Gate 4: Geração Final

1. Capturar screenshots (ler `references/screenshot-guide.md`)
2. Gerar HTML de cada slide
3. Renderizar como PNG via Playwright
4. Apresentar ao usuário
5. Após aprovação, criar `roteiro.md` com textos, caption, hashtags e caminhos dos PNGs

### Gate: Usuário aprova ou pede ajuste em slides específicos.

---

## Regra #1: Referências visuais SEMPRE reais

**SEMPRE buscar referências visuais reais ANTES de criar qualquer coisa.** Esta é a regra mais importante da skill. Ordem de prioridade:

1. **Abrir o app/site real via Playwright** e capturar screenshot direto da tela
2. **Google Imagens** — buscar "[nome] logo/screenshot/icon" via Playwright, navegar até a fonte e baixar com `curl`
3. **Google Play Store / App Store** — navegar até a página do app e capturar o ícone
4. **Repositórios de ícones** — simpleicons.org, brandlogos.net, wikimedia commons
5. **ÚLTIMO RECURSO: criar mockup em HTML** — só quando todas as opções acima falharem

**NUNCA:**
- Criar SVGs genéricos inline (círculos, estrelas, formas geométricas)
- Usar favicons (16-32px, ficam pixelados)
- Inventar ícones que não se parecem com a marca real
- Usar emojis como substituto de ícones reais

---

## Regra #2: Layout flexbox centralizado (NUNCA violar)

O conteúdo dos slides DEVE usar flexbox. NUNCA usar `position: absolute` para headline, body text, screenshots ou visuais.

**Position absolute permitido APENAS para:** accent comments, @handle, background blur, badges decorativos.

### Estrutura obrigatória do body

```css
body {
  width: 1080px;    /* ou 1350, 1080 conforme formato */
  height: 1440px;   /* ou 1350, 1080 conforme formato */
  padding: 80px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 70px;         /* 100px na capa, 70px nos slides de conteúdo */
  position: relative; /* pra elementos absolute como accent comments e handle */
  overflow: hidden;
}
```

**Os blocos principais (headline-group, body-text, screenshot) ficam NO FLUXO do flex.** Isso garante centralização vertical e horizontal automática.

---

## Regra #3: Alinhamento

- **Headlines:** SEMPRE `text-align: center`
- **Cards, logos, screenshots:** SEMPRE `justify-content: center` (centralizados)
- **@handle:** SEMPRE centralizado (`position: absolute; bottom: 50px; left: 0; right: 0; text-align: center`)
- **Subtítulo na capa:** centralizado
- **Body text em slides de conteúdo:** `text-align: left` (exceto capa e CTA = centralizado)

---

## Design dos slides

### Background

NUNCA gradiente liso sozinho. Usar gradiente + textura/glows + logo real com blur.

Logo como background: buscar a LOGO REAL (ver Regra #1), aplicar `opacity: 0.08-0.12; filter: blur(3-5px);`, tamanho 900-1100px, centralizada, rotação leve (-5° a -10°).

### Headlines

Fonte headline (escolhida no Gate 1) com efeito tipográfico aprovado no Gate 3. Tamanho 70-96px. Efeitos disponíveis em `references/headline-effects.md`.

### Accent Comments

Comentários com personalidade espalhados pelo slide (fonte accent escolhida no Gate 1):
- **30-36px** (slides normais), **48px+** (CTA)
- **Sem parênteses.** "de graça", não "(de graça)"
- **Posições criativas:** rotações -3° a +8°, variar entre slides
- **1-2 por slide**
- Cor: accent com opacidade 0.6 ou branco com opacidade 0.5

### Screenshots

- border-radius 16px, box-shadow forte, GRANDES (30-35% da altura do slide)
- Centralizados no flex
- Crescem progressivamente ao longo do carrossel (curva texto→visual)
- 1 screenshot grande > grid de vários pequenos

### Fontes

Ler `references/fonts-config.md`. A skill usa 3 slots de fonte:

- **Headline:** fonte bold/display pra títulos (definida no Gate 1)
- **Accent:** fonte com personalidade pra comentários (definida no Gate 1)
- **Body:** Inter (Google Fonts, sempre disponível)

Se o usuário tiver fontes locais (.ttf/.otf), copiar pro diretório de trabalho:
```bash
mkdir -p ./fonts && cp ~/Library/Fonts/{FonteHeadline.ttf,FonteAccent.ttf} ./fonts/
```

Se não tiver, usar combinações do Google Fonts. Veja sugestões em `references/fonts-config.md`.

---

## Renderização

1. Salvar HTML no diretório de trabalho
2. Servir via `python3 -m http.server [porta]` (verificar porta livre)
3. Abrir via Playwright com viewport do formato (3:4 = 1080x1440)
4. Aguardar 3 segundos para fontes carregarem
5. Capturar screenshot como PNG
6. **Para overlays transparentes:** usar `browser_run_code` com `page.screenshot({ path: 'file.png', omitBackground: true, type: 'png' })`
7. **FECHAR O BROWSER** após cada slide

### Composição de vídeo em slides

Quando um slide precisa ter vídeo rodando (ex: vídeo oficial embedado na capa):
1. Renderizar o background como PNG separado (gradiente + logo blur)
2. Renderizar overlay de texto como PNG com `omitBackground: true` (headline, accent comments, handle)
3. Usar ffmpeg pra compor: `background + vídeo posicionado + overlay transparente`

---

## Auto-review (verificar antes de mostrar ao usuário)

1. **Layout flex?** Elementos principais no fluxo do flex, NÃO position absolute?
2. **Centralizado?** Headlines, screenshots, cards e handle centralizados?
3. **Logos reais?** Capturados de fontes reais, não SVGs genéricos?
4. **Background rico?** Gradiente + textura + logo blur, não gradiente liso?
5. **Accent comments OK?** Sem parênteses, 30px+, posições criativas rotacionadas?
6. **Português natural?** Ler em voz alta. Se soar robótico, reescrever.
7. **Densidade?** ~65% preenchido em slides de conteúdo. CTA = mínimo.

Se qualquer resposta for "não", corrigir ANTES de apresentar.

---

## Reference Files

| Arquivo | Quando ler |
|---------|-----------|
| `references/templates.md` | Gate 1 — templates |
| `references/palettes.md` | Gate 3 — paletas |
| `references/headline-effects.md` | Gate 3 — efeitos |
| `references/screenshot-guide.md` | Gate 4 — captura |
| `references/fonts-config.md` | Antes da geração |

## Troubleshooting

| Problema | Solução |
|----------|---------|
| Fonte não carrega | Copiar .ttf pro diretório fonts/ |
| Screenshot branco/transparente errado | Usar `omitBackground: true` no `browser_run_code` |
| Servidor HTTP ocupado | Tentar outra porta |
| Vídeo composto fica branco | Verificar que bg.png tem o gradiente (não transparente) |
| Elementos grudados no topo | Verificar `justify-content: center` no body (NÃO flex-start) |
