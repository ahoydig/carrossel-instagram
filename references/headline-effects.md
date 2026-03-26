# Efeitos Tipográficos — Headlines

Catálogo de efeitos CSS para aplicar na fonte headline dos slides. O efeito é escolhido no Gate 3 com base no mood/paleta do carrossel. As cores devem ser adaptadas à paleta aprovada. Substituir `var(--font-headline)` pela fonte escolhida no Gate 1.

---

## 1. Gradiente

Texto com degradê de cores. Versátil, funciona com qualquer paleta.

```css
.headline {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  background: linear-gradient(135deg, [COR_1], [COR_2]);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(0 0 30px [COR_1]33);
}
```

**Melhor para:** Energia, resultado, destaque
**Combina com:** Quente/Energia, Sunset/Warm, Ruby/Bold

---

## 2. Dupla Camada (Fill + Outline)

Headline preenchida + variação outline sobrepostas. Efeito premium e sofisticado. Funciona melhor com fontes que tenham versão outline disponível.

```css
.headline-container { position: relative; }

.headline-fill {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  background: linear-gradient(180deg, [COR_1], [COR_2]);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.headline-outline {
  font-family: var(--font-headline-outline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  position: absolute;
  top: 0;
  left: 0;
  color: rgba(255, 255, 255, 0.15);
}
```

**HTML:**
```html
<div class="headline-container">
  <div class="headline-fill">TITULO</div>
  <div class="headline-outline">TITULO</div>
</div>
```

**Melhor para:** Premium, tech, sofisticado
**Combina com:** Tech/Dark, Navy/Profissional, Deep Purple

---

## 3. Metálico

Gradiente multi-stop simulando reflexo metálico.

```css
.headline {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  background: linear-gradient(180deg, #e8e8e8, #888888, #e8e8e8, #666666, #cccccc);
  background-size: 100% 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.8));
}
```

**Melhor para:** Autoridade, profissional, tech
**Combina com:** Charcoal/Editorial, Navy/Profissional

---

## 4. Neon Glow

Texto com brilho neon via text-shadow múltiplo.

```css
.headline {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  color: [COR_NEON];
  text-shadow:
    0 0 10px [COR_NEON],
    0 0 20px [COR_NEON],
    0 0 40px [COR_NEON],
    0 0 80px [COR_NEON]44;
}
```

**Melhor para:** Disruptivo, moderno, tech, chamativo
**Combina com:** Tech/Dark, Deep Purple, Midnight/Impacto

---

## 5. Fogo / Lava

Gradiente vertical de quente para escuro.

```css
.headline {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  background: linear-gradient(180deg, #FFD700, #FF6B00, #FF2200, #CC0000);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(0 0 20px rgba(255, 68, 0, 0.5));
}
```

**Nota:** As cores deste efeito podem ser adaptadas. Ex: tons de azul (gelo→deep blue) ou verde (lime→forest).

**Melhor para:** Impacto, urgência, motivação
**Combina com:** Ruby/Bold, Quente/Energia, Charcoal/Editorial

---

## 6. Clean + Shadow

Cor sólida com sombra offset que dá profundidade. O mais versátil.

```css
.headline {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  color: #FFFFFF;
  text-shadow:
    3px 3px 0px rgba(0, 0, 0, 0.3),
    6px 6px 0px rgba(0, 0, 0, 0.15);
}
```

**Melhor para:** Versátil, limpo, editorial — funciona com qualquer paleta
**Combina com:** Todas as paletas

---

## 7. Outline Glow

Usa a versão outline da fonte headline com brilho. Efeito futurista e clean. Se a fonte não tiver versão outline, usar `-webkit-text-stroke` como alternativa.

```css
.headline {
  font-family: var(--font-headline-outline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  color: [COR_ACCENT];
  text-shadow:
    0 0 10px [COR_ACCENT],
    0 0 30px [COR_ACCENT]44;
}
```

**Melhor para:** Futurista, inovação, minimalismo tech
**Combina com:** Tech/Dark, Forest/Growth, Deep Purple

---

## 8. Offset Duplo

Duas camadas da mesma fonte headline com deslocamento. Bold e dinâmico.

```css
.headline-container { position: relative; }

.headline-back {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  color: [COR_ACCENT];
  position: absolute;
  top: 4px;
  left: 4px;
}

.headline-front {
  font-family: var(--font-headline);
  font-size: 80px;
  text-transform: uppercase;
  letter-spacing: 4px;
  color: #FFFFFF;
  position: relative;
}
```

**HTML:**
```html
<div class="headline-container">
  <div class="headline-back">TITULO</div>
  <div class="headline-front">TITULO</div>
</div>
```

**Melhor para:** Bold, dinâmico, chamativo, jovem
**Combina com:** Midnight/Impacto, Quente/Energia, Sunset/Warm

---

## Como escolher o efeito

1. Identificar o mood do carrossel (baseado no tema + template + paleta)
2. Consultar "Melhor para" e "Combina com" de cada efeito
3. Selecionar 1-2 opções
4. Apresentar ao usuário com preview no slide 1
5. O efeito aprovado é aplicado em TODOS os slides que têm headline

## Adaptação de cores

Os exemplos usam cores fixas, mas SEMPRE adaptar à paleta aprovada:
- [COR_1], [COR_2]: usar accent e variações da paleta
- [COR_NEON]: usar accent da paleta
- Branco: usar cor de texto da paleta
- Sombras: usar preto ou cor escura do background com opacidade
