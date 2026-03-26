# Configuração de Fontes

A skill usa 3 slots de fonte. No Gate 1, pergunte ao usuário quais fontes ele quer usar e sugira combinações.

## Slots

| Slot | Função | Exemplo |
|------|--------|---------|
| **Headline** | Títulos grandes, bold, display | Bebas Neue, Oswald, Anton |
| **Accent** | Comentários com personalidade, handwritten ou quirky | Space Grotesk, Caveat, Permanent Marker |
| **Body** | Texto corrido, legível | Inter (fixo, Google Fonts) |

## Combinações sugeridas

Apresente 2-3 combinações ao usuário no Gate 1. Todas são do Google Fonts (gratuitas, sem instalação).

### 1. Bold + Handwritten (versátil)
```
Headline: Bebas Neue
Accent:   Caveat
Body:     Inter
```
Melhor para: a maioria dos carrosséis. Clean, impactante, com toque humano.

### 2. Industrial + Grotesk (tech/moderno)
```
Headline: Oswald
Accent:   Space Grotesk
Body:     Inter
```
Melhor para: tech, IA, automação, SaaS.

### 3. Impact + Playful (viral/energia)
```
Headline: Anton
Accent:   Permanent Marker
Body:     Inter
```
Melhor para: conteúdo viral, polêmica, hot takes, energia.

### 4. Serif + Mono (editorial/premium)
```
Headline: Playfair Display
Accent:   JetBrains Mono
Body:     Inter
```
Melhor para: storytelling, estudo de caso, conteúdo premium.

### 5. Condensed + Rounded (clean/minimal)
```
Headline: Barlow Condensed
Accent:   Nunito
Body:     Inter
```
Melhor para: tutorial, educativo, comparativo.

## Fontes locais do usuário

Se o usuário tiver fontes próprias (.ttf ou .otf), usar essas como prioridade:

### 1. Verificar se existem
```bash
ls ~/Library/Fonts/NomeDaFonte.ttf 2>/dev/null && echo "LOCAL" || echo "GOOGLE FONTS"
```

### 2. Copiar pro diretório de trabalho
```bash
mkdir -p ./fonts
cp ~/Library/Fonts/FonteHeadline.ttf ./fonts/
cp ~/Library/Fonts/FonteAccent.ttf ./fonts/
```

### 3. CSS para fontes locais
```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

@font-face {
  font-family: 'HeadlineFont';
  src: url('./fonts/FonteHeadline.ttf') format('truetype');
}
@font-face {
  font-family: 'AccentFont';
  src: url('./fonts/FonteAccent.ttf') format('truetype');
}
```

### 4. CSS para Google Fonts (sem fontes locais)
```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Bebas+Neue&family=Caveat:wght@400;700&display=swap');
```

Ajustar o import conforme a combinação escolhida.

### 5. Font-family declarations
```css
--font-headline: 'HeadlineFont', 'Bebas Neue', sans-serif;
--font-accent: 'AccentFont', 'Caveat', cursive;
--font-body: 'Inter', sans-serif;
```

O primeiro valor é a fonte local (se existir), o segundo é o fallback do Google Fonts.

## Tamanhos recomendados

| Elemento | Formato 3:4 (1080x1440) | Formato 4:5 (1080x1350) | Formato 1:1 (1080x1080) |
|----------|------------------------|------------------------|------------------------|
| Headline principal (capa) | 72-96px | 68-88px | 60-80px |
| Headline slides internos | 56-72px | 52-68px | 48-60px |
| Subtítulo | 28-36px | 26-34px | 24-30px |
| Body text | 22-28px | 20-26px | 18-24px |
| Accent comment | 14-18px | 13-17px | 12-16px |
| @handle | 16-20px | 15-19px | 14-18px |

Estes são ranges. Ajustar conforme quantidade de texto no slide.
