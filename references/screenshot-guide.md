# Guia de Captura de Screenshots

Estratégias para capturar screenshots de diferentes fontes via Playwright e embutir nos slides do carrossel.

---

## Fluxo geral

1. Navegar até a URL via `browser_navigate`
2. Lidar com popups/overlays (fechar login walls, cookie banners, etc.)
3. Identificar o elemento a capturar (nem sempre é a página toda)
4. Capturar screenshot do elemento específico via `browser_take_screenshot` com `ref` e `element`
5. Salvar localmente
6. Embutir no HTML do slide como `<img>` com estilo padronizado

---

## Por fonte

### Twitter/X

**Desafio:** Login wall frequente, layout muda com/sem login.

**Estratégia:**
1. Navegar para a URL do tweet
2. Fechar popup de login se aparecer (buscar botão "Close" ou "X")
3. Fazer snapshot da página
4. Localizar o elemento do tweet (geralmente um `article`)
5. Capturar screenshot do tweet isolado

**Dica:** Se o login wall for intransponível, usar serviço alternativo ou pedir screenshot manual ao usuário.

---

### Instagram Post

**Desafio:** Popup "Log in to see more" bloqueia a visualização.

**Estratégia:**
1. Navegar para a URL do post
2. Fechar popup de login (buscar botão "Close")
3. Capturar screenshot da imagem do post (não da página toda)
4. Se for carrossel, navegar pelos slides e capturar o desejado

---

### Instagram Reel

**Desafio:** Conteúdo de vídeo, não imagem estática.

**Estratégia:**
1. Navegar para a URL do Reel
2. Fechar popup de login
3. Capturar thumbnail/frame do vídeo
4. Extrair texto da legenda do Reel para usar no conteúdo textual do carrossel
5. A legenda vira matéria-prima para os slides

---

### Notícia / Artigo

**Desafio:** Layouts variados, paywalls, banners de cookie.

**Estratégia:**
1. Navegar para a URL
2. Fechar cookie banners (buscar botões "Accept", "Aceitar", "OK", "Close")
3. Capturar manchete + imagem principal (geralmente o topo da página)
4. Usar `fullPage: false` para pegar só o viewport
5. Se precisar de trecho específico, fazer snapshot e identificar o elemento

**Recorte sugerido:** Capturar viewport do topo (manchete + lead + imagem hero).

---

### GitHub Repository

**Desafio:** READMEs longos, precisa capturar seção específica.

**Estratégia:**
1. Navegar para a URL do repo ou README
2. Fazer snapshot da página
3. Identificar a seção relevante (ex: "What You Can Build", "Features", "Installation")
4. Capturar screenshot apenas dessa seção
5. Se a seção for muito longa, capturar só o início

---

### YouTube

**Desafio:** Ads, popups de consent.

**Estratégia:**
1. Navegar para a URL do vídeo
2. Fechar popups de consent/cookies
3. Capturar thumbnail do vídeo + título
4. Alternativamente, capturar apenas a thumbnail em tamanho maior via URL direta:
   `https://img.youtube.com/vi/[VIDEO_ID]/maxresdefault.jpg`

---

### LinkedIn Post

**Desafio:** Login wall agressivo.

**Estratégia:**
1. Tentar navegar para a URL
2. Se bloqueado por login, informar o usuário e pedir screenshot manual
3. Se acessível, capturar o corpo do post

**Nota:** LinkedIn é a fonte mais difícil de capturar automaticamente. Priorizar fallback manual.

---

### URL Genérica

**Estratégia:**
1. Navegar para a URL
2. Fechar popups/banners se houver
3. Perguntar ao usuário o que capturar (viewport, elemento específico, seção)
4. Capturar conforme solicitado

---

## Estilo dos screenshots no slide

Todos os screenshots embutidos nos slides devem seguir este padrão CSS:

```css
.screenshot {
  max-width: 85%;
  max-height: 45%;
  border-radius: 12px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
  object-fit: contain;
}

/* Para dois screenshots lado a lado (layout dual-screenshot) */
.screenshot-dual {
  max-width: 42%;
  max-height: 40%;
  border-radius: 10px;
  box-shadow: 0 6px 24px rgba(0, 0, 0, 0.35);
  object-fit: contain;
}
```

### Posicionamento

- **Slide com texto + screenshot:** screenshot na metade inferior, centralizado
- **Slide dual-screenshot:** dois screenshots lado a lado na metade inferior
- **Screenshot como elemento principal:** pode ocupar até 60% do slide

### Embutir no HTML

Os screenshots capturados devem ser convertidos para base64 e embutidos diretamente no HTML como data URI, ou referenciados como arquivo local:

```html
<!-- Via arquivo local -->
<img class="screenshot" src="./screenshots/tweet_captura.png" alt="Screenshot">

<!-- Via base64 (mais portátil) -->
<img class="screenshot" src="data:image/png;base64,..." alt="Screenshot">
```

Preferir arquivo local para não inflar o HTML. Converter para base64 apenas se necessário.

---

## Fallback manual

Quando a captura automática falhar:

1. Informar o usuário: "Não consegui capturar [URL]. O site bloqueia acesso automatizado."
2. Pedir: "Pode tirar um screenshot e me passar o caminho do arquivo?"
3. Aceitar: png, jpg, jpeg, webp
4. Aplicar o mesmo estilo (border-radius, shadow) ao embutir
