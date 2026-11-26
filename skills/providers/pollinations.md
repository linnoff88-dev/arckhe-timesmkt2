# Provider: Pollinations.ai

## Visêo Geral

Pollinations.ai é um serviço de geraçêo de imagem **gratuito**, sem polling, que retorna a imagem diretamente na resposta HTTP (GET request → binário).

- **Custo:** Gratuito (conta Seed)
- **API key:** Opcional — sem key funciona (anônimo, 1 req/15s); com key free (Seed): 1 req/5s, sem watermark
- **Polling:** Nêo. GET síncrono, resposta é binário da imagem.
- **Modelos:** FLUX Schnell (padrêo), Z-Image Turbo, FLUX Kontext, GPT Image, Gemini Pro

## Como Ativar no Pipeline

### Opçêo 1 — Variável de ambiente global (afeta todas as campanhas)
```env
IMAGE_PROVIDER=pollinations
```

### Opçêo 2 — Por campanha (no payload)
```json
{
  "image_provider": "pollinations",
  "image_model": "flux"
}
```

## Modelos Disponíveis

| ID | Descriçêo | Velocidade |
|---|---|---|
| `flux` | FLUX.1 Schnell — padrêo, bom custo/qualidade | 3–8s |
| `zimage` | Z-Image Turbo — upscaling 2x, mais detalhado | 5–12s |
| `kontext` | FLUX.1 Kontext — melhor para ediçêo em contexto | 8–15s |
| `gptimage` | GPT Image 1 Mini (OpenAI) | 10–20s |
| `nanobanana-pro` | Gemini 3 Pro Image (4K, Thinking) | 15–30s |

**Recomendaçêo para ads:** `flux` (velocidade), `zimage` (detalhamento de produto).

## Autenticaçêo (Conta Seed — Gratuita)

1. Acesse https://enter.pollinations.ai e crie conta gratuita
2. Copie o token e adicione ao `.env`:
   ```env
   POLLINATIONS_TOKEN=sk_sua_chave_aqui
   ```
3. Sem token: funciona, mas 1 req/15s (lento para campanha com 5+ imagens)

## Limitações

- Sem suporte a `negative_prompt`
- Prompt máximo: sem limite oficial (recomendado < 400 chars para robustez)
- Imagens públicas por padrêo (parâmetro `private=false`) — com conta Seed, `private=true` disponível
- Rate limit anônimo (1 req/15s) → campanha de 5 imagens = ~75s; com Seed (1 req/5s) = ~25s

## Comparaçêo com KIE

| | KIE z-image | Pollinations flux | Pollinations zimage |
|---|---|---|---|
| Custo | Pago | Gratuito | Gratuito |
| Velocidade | 20–60s (polling) | 3–8s | 5–12s |
| Qualidade | Alta | Boa | Alta |
| Rate limit | — | 1/5s (Seed) | 1/5s (Seed) |
| Prompt max | 500 chars | ~400 chars | ~400 chars |
