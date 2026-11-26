# CARCKHÉtography Rules — Motion Director

Referência técnica de movimentaçêo de câmera para vídeos de marketing curtos (10–30s).

---

## Tipos de Movimento

### zoom_in
A câmera se aproxima do sujeito ao longo da cena.
- Cria **tensêo, urgência, proximidade emocional**
- Ideal para: hook, revelaçêo de problema, momento de impacto
- Nunca usar em: CTA (parece agressivo demais no fechamento)

### zoom_out
A câmera se afasta, revelando o contexto.
- Cria **alívio, amplidêo, resoluçêo**
- Ideal para: benefit, soluçêo, social proof
- Efeito "o mundo se abre" após a tensêo do hook

### pan_right / pan_left
Movimento lateral com câmera levemente afastada.
- Cria **fluidez, continuidade narrativa**
- Ideal para: product showcase, transiçêo entre ideias
- Pan direita = progressêo natural (leitura ocidental)
- Pan esquerda = retorno, comparaçêo, contraste

### static
Sem movimento. Imagem fixa.
- Cria **peso, autoridade, clareza**
- Ideal para: CTA, mensagens de fechamento, slides de texto puro
- Força o olho do espectador a focar só no texto

---

## Intensidade de Movimento

| Intensidade | Zoom Range | Quando usar |
|---|---|---|
| `aggressive` | 1.0 → 1.20 | Hook, revelaçêo, impacto. Movimento visível e intencional |
| `moderate` | 1.0 → 1.12 | Benefit, product showcase. Sutil mas perceptível |
| `subtle` | 1.0 → 1.06 | Social proof, contexto. Quase imperceptível — evita imagem parada |
| `static` | 1.0 → 1.0 | CTA, texto puro, banners. Nenhum movimento |

---

## Regras por Tipo de Cena

| Tipo de Cena | Movimento Recomendado | Intensidade |
|---|---|---|
| `hook` | `zoom_in` | `aggressive` |
| `tension` | `zoom_in` ou `pan_left` | `aggressive` |
| `product_showcase` | `pan_right` ou `zoom_out` | `moderate` |
| `benefit` | `zoom_out` | `moderate` |
| `solution` | `zoom_out` | `moderate` |
| `social_proof` | `pan_right` | `subtle` |
| `cta` | `static` ou `zoom_in` | `static` ou `subtle` |

---

## Regras de Composiçêo

### Regra dos terços
O elemento principal (rosto, produto) deve estar num dos 4 pontos de interseçêo da grade 3×3.
O movimento deve revelar ou aproximar desse ponto — nunca afastar.

### Movimento deve seguir a narrativa
- História em ascensêo (hook → soluçêo) → zoom_in progressivo
- História de alívio (tensêo → resoluçêo) → zoom_out progressivo
- Nêo misturar direções aleatoriamente entre cenas consecutivas

### Consistência de direçêo
Pan direita em cena 1 → nêo fazer pan esquerda em cena 2 (confunde o olho).
Alternar pan apenas quando há corte de contexto (ex: de problema para soluçêo).

---

## Transições

| Tipo | Duraçêo | Quando usar |
|---|---|---|
| `crossfade` | 0.4–0.6s | Entre cenas do mesmo bloco narrativo |
| `fade_black` | 0.5–0.8s | Entre blocos diferentes (ex: problema → soluçêo) |
| `cut` | 0s | Corte intencional de impacto — hook ou reveal |

**Regra:** Máximo 1 `cut` por vídeo. Usá-lo com intençêo no ponto de maior impacto.
