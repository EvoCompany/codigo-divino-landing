# Código Divino — Landing Page

Página de vendas (venda direta) do infoproduto **Código Divino**, um sistema visual de estudo bíblico. Site estático, sem build step, pronto para deploy na Vercel.

## Estrutura

```
index.html        → página de vendas principal
privacidad.html    → política de privacidade
terminos.html      → termos de uso
```

## Antes de publicar — checklist obrigatório

Edite o bloco `CONFIG` no final do `index.html` (procure por `CONFIGURAÇÃO`):

- [ ] `linkCheckout` — troque `LINK_CHECKOUT_AQUI` pelo link real de checkout (Hotmart, Kiwify, Cakto etc.)
- [ ] `dataLimiteOferta` — defina uma data real de encerramento da oferta (o contador regressivo usa essa data)
- [ ] `SEU_PIXEL_ID` — troque pelo ID real do Meta Pixel (aparece 2x no `<head>`)
- [ ] `GTM-XXXXXXX` — troque pelo ID real do Google Tag Manager (aparece 2x: `<head>` e `<body>`)
- [ ] `og:image` — troque pela URL de uma imagem real 1200x630px (mockup do produto)

## Conteúdo que precisa de dados reais

- **Depoimentos** (seção `.depoimentos`): os 3 cards estão marcados como exemplo — substitua por depoimentos reais de clientes (nome, cidade, e idealmente print de conversa/avaliação). Nunca publique depoimentos fabricados como se fossem reais.
- **Foto de autoridade** (seção `.autoridade`): opcionalmente troque o selo com emoji por uma foto real do criador/equipe.
- **Número de clientes** ("+4.000 cristianos"): ajuste para o número real e verificável antes de publicar.

## Rastreamento

- Meta Pixel dispara `PageView` automaticamente e `InitiateCheckout` ao clicar em qualquer CTA de compra.
- O evento `Purchase` **não** deve ser disparado no front-end — configure-o via webhook da plataforma de checkout (Conversions API), pois bloqueadores de anúncios impedem a captura no client-side.

## Deploy

Este repositório está conectado a um projeto na Vercel. Qualquer push na branch `main` gera um novo deploy automaticamente.
