# KIE API — Z-Image Model Reference

**Fonte:** docs.kie.ai, kie.ai/z-image, The Data Scientist, Plain English, Hugging Face (Tongyi-MAI/Z-Image-Turbo)
**Atualizado:** 2026-03-28

---

## Endpoint de criaçêo de tarefa

```
POST https://api.kie.ai/api/v1/jobs/createTask
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```

**Payload:**
```json
{
  "model": "z-image",
  "callBackUrl": "https://...",
  "input": {
    "prompt": "...",
    "aspect_ratio": "1:1",
    "nsfw_checker": true
  }
}
```

**Response:**
```json
{ "code": 200, "msg": "success", "data": { "taskId": "task_z-image_1765174270120" } }
```

---

## Parâmetros aceitos

| Campo | Tipo | Obrig. | Descriçêo |
|---|---|---|---|
| `model` | string | Sim | `"z-image"` ou `"z-image-turbo"` |
| `input.prompt` | string | Sim | 3–1000 caracteres. Manter abaixo de 800. |
| `input.aspect_ratio` | string | Sim | Ver valores abaixo |
| `input.nsfw_checker` | boolean | Nêo | Filtragem de conteúdo. Default: `true` |
| `callBackUrl` | string | Nêo | Webhook para resultado (preferir sobre polling) |

**NêO existe:** `negative_prompt` — Z-Image-Turbo nêo suporta classifier-free guidance, entêo negative prompts nêo têm efeito.

---

## Aspect Ratios suportados

| Valor | Uso |
|---|---|
| `"1:1"` | Feed Instagram, Facebook |
| `"4:3"` | Paisagem clássico |
| `"3:4"` | Retrato clássico |
| `"16:9"` | YouTube, landscape |
| `"9:16"` | Stories, Reels, TikTok |

---

## Polling de resultado

```
GET https://api.kie.ai/api/v1/jobs/recordInfo?taskId=TASK_ID
Authorization: Bearer YOUR_API_KEY
```

**Estados:** `waiting` → `queuing` → `generating` → `success` / `fail`

**Response em sucesso:**
```json
{
  "data": {
    "state": "success",
    "resultJson": "{\"resultUrls\":[\"https://cdn.kie.ai/...\"]}"
  }
}
```

> `resultJson` é uma string JSON serializada — fazer `JSON.parse(data.resultJson)` para obter `resultUrls[0]`.

---

## Evitar texto na imagem

O Z-Image-Turbo foi treinado com forte suporte a renderizaçêo de texto bilíngue (EN+ZH). **Ele tende a gerar texto quando o prompt sugere nomes de produtos ou palavras-chave textuais.**

**Estratégia recomendada pela documentaçêo oficial:** colocar restrições no **final** do prompt:

```
[descriçêo do conteúdo visual]
[estilo fotográfico]
[composiçêo e iluminaçêo]
Clean image, no text overlay, no watermark, no logo, no words,
no typography, no letters or numbers visible, text-free, label-free.
```

**Palavras a evitar no prompt** (ativam renderizaçêo de texto):
- Nomes de marcas com texto ("Cold Brew Coffee Co.", brand names completos)
- "label", "sign", "poster", "banner" sem negaçêo
- "packaging with text", "billboard"

**Nota:** Nossa implementaçêo atual coloca "No text..." no INÍCIO do prompt. A doc oficial recomenda o FIM. Para z-image-turbo (sem CFG/guidance), o posicionamento pode ter efeito diferente de modelos SDXL/Flux. Testar ambas posições se texto ainda aparecer.

---

## Template de prompt para ATMKT

```
[Descriçêo do produto/cena — específica e detalhada]
[Estilo: "commercial product photography, soft studio lighting"]
[Composiçêo: "centered composition, shallow depth of field"]
[Paleta de cores]
Clean image, no text overlay, no watermark, no logo, no words,
no typography, no letters or numbers visible, text-free, label-free,
pure visual composition.
```

---

## Códigos de erro

| Código | Significado |
|---|---|
| 401 | API key inválida |
| 402 | Créditos insuficientes |
| 422 | Parâmetro inválido |
| 429 | Rate limit excedido |
| 455 | Conteúdo bloqueado pelo nsfw_checker |
| 500 | Erro interno KIE |
| 501 | Modelo indisponível |

---

## Rate limits

- Até 20 requests novos por 10 segundos
- Até 100+ tasks concorrentes por conta

---

## Diferenças z-image vs z-image-turbo (modelo base)

| Aspecto | Z-Image | Z-Image-Turbo |
|---|---|---|
| Negative prompt | Suportado | **Nêo suportado** |
| Velocidade | Mais lento | Near-instant |
| Passos inferência | Muitos | 8-12 |
| Guidance scale (CFG) | Suportado | Deve ser 0.0 |
| Texto bilíngue | Sim | Sim (ponto forte) |
| Model ID na KIE API | `"z-image"` | `"z-image-turbo"` (na doc KIE marketplace) |
