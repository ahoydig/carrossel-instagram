# Configuração de Fontes

As fontes **Nofex** e **Crankdat** foram criadas por [@flavioahoy](https://instagram.com/flavioahoy). Incluídas nesta skill como fontes padrão para headlines e accent.

## Fontes locais

| Uso | Família | Arquivo | Caminho sistema |
|-----|---------|---------|-----------------|
| Headlines | Nofex | Nofex.ttf | ~/Library/Fonts/ |
| Headlines (variação) | Nofex Outline | Nofex-Outline.ttf | ~/Library/Fonts/ |
| Accent/Destaques | Crankdat Regular | Crankdat-Regular.ttf | ~/Library/Fonts/ |
| Accent/Destaques Bold | Crankdat Bold | Crankdat-Bold.ttf | ~/Library/Fonts/ |

## Fonte universal (Google Fonts)

| Uso | Família | Import |
|-----|---------|--------|
| Body | Inter | `@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');` |

## Fallback para outros usuários

Quando as fontes locais não estiverem instaladas:

| Uso | Fallback Google Fonts | Import |
|-----|----------------------|--------|
| Headlines | Bebas Neue | `@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');` |
| Accent | Space Grotesk | `@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;700&display=swap');` |

## Setup antes da primeira geração

### 1. Verificar fontes locais

```bash
ls ~/Library/Fonts/Nofex.ttf 2>/dev/null && echo "LOCAL" || echo "FALLBACK"
```

### 2. Se LOCAL: copiar fontes para diretório de trabalho

```bash
mkdir -p ./fonts
cp ~/Library/Fonts/Nofex.ttf ./fonts/
cp ~/Library/Fonts/Nofex-Outline.ttf ./fonts/
cp ~/Library/Fonts/Crankdat-Regular.ttf ./fonts/
cp ~/Library/Fonts/Crankdat-Bold.ttf ./fonts/
```

### 3. CSS para modo LOCAL

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

@font-face {
  font-family: 'Nofex';
  src: url('./fonts/Nofex.ttf') format('truetype');
}
@font-face {
  font-family: 'Nofex Outline';
  src: url('./fonts/Nofex-Outline.ttf') format('truetype');
}
@font-face {
  font-family: 'Crankdat';
  src: url('./fonts/Crankdat-Regular.ttf') format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: 'Crankdat';
  src: url('./fonts/Crankdat-Bold.ttf') format('truetype');
  font-weight: bold;
}
```

### 4. CSS para modo FALLBACK

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Bebas+Neue&family=Space+Grotesk:wght@400;700&display=swap');
```

### 5. Font-family declarations

```css
/* Modo LOCAL */
--font-headline: 'Nofex', 'Bebas Neue', sans-serif;
--font-headline-outline: 'Nofex Outline', 'Bebas Neue', sans-serif;
--font-accent: 'Crankdat', 'Space Grotesk', sans-serif;
--font-body: 'Inter', sans-serif;

/* Modo FALLBACK (mesma declaration, o browser resolve) */
--font-headline: 'Nofex', 'Bebas Neue', sans-serif;
--font-headline-outline: 'Nofex Outline', 'Bebas Neue', sans-serif;
--font-accent: 'Crankdat', 'Space Grotesk', sans-serif;
--font-body: 'Inter', sans-serif;
```

As declarations são as mesmas. A diferença é se os @font-face das fontes locais estão presentes ou não. Se não estiverem, o browser cai automaticamente no fallback.

## Tamanhos recomendados

| Elemento | Formato 3:4 (1080x1440) | Formato 4:5 (1080x1350) | Formato 1:1 (1080x1080) |
|----------|------------------------|------------------------|------------------------|
| Headline principal (capa) | 72-96px | 68-88px | 60-80px |
| Headline slides internos | 56-72px | 52-68px | 48-60px |
| Subtítulo | 28-36px | 26-34px | 24-30px |
| Body text | 22-28px | 20-26px | 18-24px |
| Label/accent (Crankdat) | 14-18px | 13-17px | 12-16px |
| @handle | 16-20px | 15-19px | 14-18px |

Estes são ranges. Ajustar conforme quantidade de texto no slide.
