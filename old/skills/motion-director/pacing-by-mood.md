# Pacing by Mood — Motion Director

Define ritmo, transições e intensidade de movimento com base no tom da campanha e da marca.

---

## Como Identificar o Mood

Ler `brand_identity.md` e o `campaign_brief`. Cruzar:

| Sinal | Mood resultante |
|---|---|
| Palavras: urgente, transformaçêo, futuro, agora | `energetic` |
| Palavras: emocional, família, memória, celebraçêo | `emotional` |
| Palavras: premium, exclusivo, sofisticado, calma | `premium` |
| Palavras: Páscoa, Natal, festa, celebraçêo | `festive` |
| Palavras: educaçêo, aprender, descoberta, jornada | `inspiring` |

---

## Presets de Ritmo por Mood

### `energetic` — Urgente / Tecnologia / Transformaçêo
- Transições: `crossfade` 0.3s entre cenas do mesmo bloco, `cut` no hook
- Duraçêo média por cena: 2.5–3.5s
- Movimento dominante: zoom_in aggressive no hook, zoom_out moderate no benefit
- Exemplo de marca: ARCKHÉ, startups, cursos de tech

### `emotional` — Família / Datas comemorativas / Conexêo humana
- Transições: `crossfade` 0.6–0.8s — nunca corte seco
- Duraçêo média por cena: 4–5s
- Movimento dominante: zoom_in subtle, pan_right moderate
- Exemplo de marca: Dia das Mêes, campanhas de comunidade

### `premium` — Luxo / Produto hero / Sofisticaçêo
- Transições: `fade_black` 0.5s entre blocos, `crossfade` 0.4s dentro do bloco
- Duraçêo média por cena: 4–6s
- Movimento dominante: zoom_in subtle ou pan_right subtle — nunca aggressive
- Exemplo de marca: Cold Brew Coffee Co., moda, lifestyle

### `festive` — Datas sazonais / Celebraçêo / Animaçêo
- Transições: `cut` no hook (impacto), `crossfade` 0.4s no resto
- Duraçêo média por cena: 2.5–4s
- Movimento dominante: zoom_in moderate no hook, zoom_out moderate no restante
- Exemplo de marca: Páscoa ARCKHÉ, Black Friday, lançamentos

### `inspiring` — Educaçêo / Descoberta / Jornada
- Transições: `crossfade` 0.5s suave ao longo de todo o vídeo
- Duraçêo média por cena: 3.5–5s
- Movimento dominante: pan_right moderate (narrativa de progressêo)
- Exemplo de marca: ARCKHÉ CLUB, tutoriais, trilhas de aprendizado

---

## Regras de Ritmo Geral

- **Hook sempre mais curto** que as demais cenas (2–3s máximo)
- **CTA sempre mais longo** que o esperado (+1s) — dar tempo para ler e agir
- **Nêo usar o mesmo tipo de movimento em 3 cenas consecutivas** — varia para manter atençêo
- **Vídeo com narraçêo** → cenas seguem duraçêo do áudio (renderer distribui automaticamente)
- **Vídeo sem narraçêo** → hook 2.5s, benefit 3.5s, cta 4s
