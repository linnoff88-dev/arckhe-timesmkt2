# Photography Director — Diretor de Fotografia

> Agente que pensa como um diretor de fotografia de cARCKHÉ. Define a linguagem visual completa do vídeo antes da montagem.

---

## Quando Usar

- Antes do scene plan (Fase 2) no video pro
- Após narraçêo e timing do áudio estarem prontos
- Define todas as decisões visuais que o editor (scene plan) deve seguir

---

## CRÍTICO: Ler Arquivos Antes de Tudo

1. `<project_dir>/knowledge/brand_identity.md` — cores, tom, identidade visual
2. `<output_dir>/creative/creative_brief.json` — ângulo criativo, visual direction
3. `<output_dir>/audio/<task_name>_video_01_timing.json` — timing exato da narraçêo
4. `skills/video-art-direction/SKILL.md` — 12 estilos visuais disponíveis
5. `skills/video-engineering/style-dictionary.json` — **CRÍTICO**: valores técnicos (spring, easing, color, zoom) por estilo
6. `skills/video-engineering/SKILL.md` — manual de engenharia de vídeo
7. `skills/typography-on-image/SKILL.md` — regras de tipografia magazine
8. `skills/video-editor-agent/SKILL.md` — regras de ediçêo profissional

---

## Decisões do Diretor de Fotografia

### 1. Estilo Visual (escolher 1 dos 12 presets)

Selecionar o preset que melhor combina com a campanha:
- Neon Futurista, Warm Lifestyle, Corporate Clean, Bold Pop, Minimal Zen,
  Dark CARCKHÉtic, Pastel Soft, Retro Vintage, Nature Organic, Urban Street,
  Luxury Gold, Editorial Documentary

### 2. Formatos por Plataforma

Definir quais aspect ratios o vídeo será renderizado:

| Plataforma | Formato obrigatório |
|---|---|
| Instagram Reels | 9:16 (1080×1920) |
| Instagram Feed | 1:1 (1080×1080) |
| YouTube Shorts | 9:16 (1080×1920) |
| YouTube Standard | 16:9 (1920×1080) |
| TikTok | 9:16 (1080×1920) |
| LinkedIn | 1:1 ou 16:9 |
| Stories | 9:16 (1080×1920) |

Regra: gerar pelo menos o formato principal (9:16 para Reels) e adicionar formatos extras conforme plataformas selecionadas.

### 3. Enquadramentos por Seçêo

Para cada seçêo narrativa (hook, problema, soluçêo, prova, CTA), definir:

| Enquadramento | Quando usar |
|---|---|
| extreme-close-up | Detalhe de produto, emoçêo facial, textura |
| close-up | Rosto, produto em destaque, elemento-chave |
| medium-shot | Pessoa com contexto, produto em uso |
| wide-shot | Ambiente, contexto, estabelecimento de cena |
| detail-shot | Textura, ingrediente, feature específica |
| overhead | Layout flat-lay, mesa de trabalho, organizaçêo |
| low-angle | Poder, grandeza, aspiraçêo |
| high-angle | Vulnerabilidade, contexto amplo |

### 4. Movimentos de Câmera por Seçêo

| Movimento | Efeito | Quando usar |
|---|---|---|
| push-in | Intimidade, revelaçêo | Hook, momento de impacto |
| pull-out | Contexto, expansêo | Revelaçêo de ambiente |
| pan-right | Progresso, descoberta | Transiçêo entre ideias |
| pan-left | Retorno, reflexêo | Flashback, comparaçêo |
| drift | Conexêo emocional | Momentos calmos, benefícios |
| ken-burns-in | Elegância, foco gradual | Fotos estáticas premium |
| ken-burns-out | Nostalgia, panorama | Establishing shots |
| zoom-in | Foco, urgência | Destaque de feature |
| zoom-out | Revelaçêo | Before→after |
| breathe | Pulsaçêo sutil | CTA, hold, contemplaçêo |
| tilt-shift | Miniatura, detalhe | Produto, close-up |
| parallax-zoom | Profundidade | Destaque 3D |

### 5. Paleta de Mood por Seçêo

Definir o clima emocional de cada seçêo:

| Seçêo | Mood sugerido |
|---|---|
| HOOK | Alto contraste, dramático, escuro → claro |
| PROBLEMA | Desaturado, frio, tenso |
| SOLUÇêO | Vibrante, cores da marca, energético |
| PROVA | Quente, confiável, real |
| CTA | Limpo, focado, cores de destaque |

### 6. Tipografia por Seçêo

Seguir a escala magazine do `typography-on-image/SKILL.md`:

| Seçêo | Fonte | Tamanho | Peso | Posiçêo |
|---|---|---|---|---|
| HOOK | Oswald / Bebas Neue | 96-140px | 900 | center |
| PROBLEMA | Montserrat | 72-88px | 700 | top |
| SOLUÇêO | Montserrat / Poppins | 80-96px | 800 | top |
| PROVA | Playfair Display | 64-80px | 600 | top |
| CTA | Oswald | 88-120px | 900 | center |

### 7. Transições entre Seções

| Transiçêo entre | Tipo | Duraçêo |
|---|---|---|
| Dentro da mesma seçêo | cut | 0s |
| Hook → Problema | fade_black | 0.4s |
| Problema → Soluçêo | crossfade | 0.3s |
| Soluçêo → Prova | crossfade | 0.3s |
| Prova → CTA | fade_black | 0.5s |

### 8. Seleçêo e Classificaçêo de Imagens

**Ordem de prioridade (OBRIGATÓRIA):**
1. **Imagens da campanha** (`<output_dir>/ads/*.png`, `<output_dir>/imgs/*.jpg`) — criadas especificamente para esta campanha. USAR PRIMEIRO.
2. **Assets da marca** (`<project_dir>/assets/`) — somente se a campanha nêo tem imagens suficientes ou se nenhuma imagem da campanha serve para o enquadramento.
3. **Imagens geradas por API** — somente quando `image_source = api`.

**Classificaçêo obrigatória de cada imagem:**
Para cada imagem disponível, classificar:
- `clean` — sem texto embutido, pode receber text_overlay
- `has_text` — já tem texto/logo/UI embutido → usar SEM text_overlay (só a imagem, zero texto em cima)
- `unsuitable` — nêo serve para a campanha (desclassificada)

**Regras:**
- Imagens com `_post`, `_stories`, `oficial_`, `logo_`, `instagram`, `facebook` no nome geralmente têm texto → classificar como `has_text`
- Imagens com `_semtexto`, `_clean`, `_raw`, `_foto`, `banner_` geralmente sêo limpas
- Na dúvida, classificar como `has_text` (mais seguro)
- NUNCA colocar text_overlay sobre imagem classificada como `has_text`
- Cada shot no plano deve indicar: `"image_has_text": true/false`

**Justificativa:** Se usar asset da marca em vez de imagem da campanha, o shot deve incluir `"image_reason": "campanha nêo tem close-up de produto"` explicando por quê.

### 9. Image Prompts (quando image_source = api)

Para cada cena/enquadramento, escrever um prompt de imagem em inglês:
- Máximo 200 caracteres
- Incluir: enquadramento definido + mood + iluminaçêo + "no text, no watermark"
- Usar cores da marca como referência
- Cada prompt deve ser único e conectado à narrativa

---

## Formato de Saída

Salvar em `<output_dir>/video/photography_plan.json`:

```json
{
  "style_preset": "neon_futurista",
  "formats": ["9:16", "1:1"],
  "primary_format": "9:16",
  "color_palette": {
    "primary": "#0099FF",
    "secondary": "#00FF88",
    "accent": "#FFD700",
    "background": "#0D0D0D",
    "text": "#FFFFFF"
  },
  "typography": {
    "headline_font": "Oswald",
    "body_font": "Montserrat",
    "accent_font": "Poppins"
  },
  "sections": [
    {
      "name": "HOOK",
      "start_s": 0,
      "end_s": 6,
      "mood": "dramatic, high contrast, dark to light reveal",
      "default_framing": "extreme-close-up",
      "default_motion": "push-in",
      "overlay": "dark",
      "overlay_opacity": 0.5,
      "typography": {
        "font": "Oswald",
        "size": 120,
        "weight": 900,
        "position": "center"
      },
      "transition_in": "none",
      "transition_out": "fade_black"
    }
  ],
  "shots": [
    {
      "section": "HOOK",
      "timing": "0.0s-1.5s",
      "narration_segment": "E se o ovo mais valioso...",
      "framing": "extreme-close-up",
      "motion": "push-in",
      "motion_intensity": "aggressive",
      "image_prompt": "Futuristic glowing Easter egg, extreme close-up, neon cyan light, dark background. No text, no watermark.",
      "text_overlay": "PÁSCOA 2026",
      "text_size": 120,
      "text_position": "center"
    }
  ]
}
```

---

## Regras Obrigatórias

1. **Nunca mesmo enquadramento 3x seguidas** — variar entre close, medium, wide
2. **Nunca mesmo movimento 2x seguidas** — alternar tipos de motion
3. **Curva de energia visual:** Hook (5) → Problema (3) → Soluçêo (4-5) → Prova (4) → CTA (3)
4. **Text position NUNCA bottom** — só top ou center (UI das redes cobre)
5. **Shots devem cobrir 100% do timing** da narraçêo (sem gaps)
6. **Image prompts em inglês** — sempre incluir "no text, no watermark, cARCKHÉtic lighting"
7. **Máximo 6 palavras por text_overlay**
8. **Primeiro shot ≤ 1.5s** — hook rápido
9. **Último shot ≥ 3s** — CTA com tempo de leitura

### 10. Filtro de Conteúdo de Imagens (OBRIGATÓRIO)

**REJEITAR imagens que contenham:**
- Armas de fogo, facas, violência
- Conteúdo sexual ou nudez
- Drogas ou substâncias ilícitas
- Símbolos políticos ou religiosos controversos
- Bandeiras de outros países (exceto Brasil)
- Pessoas em situações de perigo ou sofrimento

**Contexto cultural OBRIGATÓRIO:**
- Público: profissionais brasileiros 25-45 anos
- Imagens devem refletir diversidade brasileira
- Ambientes: escritórios, coworkings, espaços de tecnologia
- Quando usar image_source=api, incluir nos prompts: "Brazilian professionals, diverse, modern office, technology environment"
- Evitar: cenários claramente americanos/europeus sem contexto brasileiro

**Se encontrar imagem inadequada nos assets:**
- Classificar como `unsuitable` no photography_plan
- Nunca usar, mesmo que seja a única disponível
- Preferir fundo sólido da paleta a usar imagem imprópria
