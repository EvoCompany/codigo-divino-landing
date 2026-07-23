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

- [ ] `linkCheckoutBasico` — link real de checkout do Plan Básico (Hotmart, Kiwify, Cakto etc.)
- [ ] `linkCheckoutCompleto` — link real de checkout do Plan Completo
- [ ] `linkCheckoutOfertaSalida` — link do checkout usado no pop-up de saída (opcional; se vazio, usa o do Plan Completo — ideal ter um link/cupom próprio para bater com o preço promocional de $9,90)
- [ ] `SEU_PIXEL_ID` — troque pelo ID real do Meta Pixel (aparece 2x no `<head>`)
- [ ] `GTM-XXXXXXX` — troque pelo ID real do Google Tag Manager (aparece 2x: `<head>` e `<body>`)
- [ ] `og:image` — troque pela URL de uma imagem real 1200x630px (mockup do produto)

## Conteúdo que precisa de dados reais

- **Depoimentos** (seção `.depoimentos`): os 3 cards estão marcados como exemplo — substitua por depoimentos reais de clientes (nome, cidade, e idealmente print de conversa/avaliação). Nunca publique depoimentos fabricados como se fossem reais.
- **Foto de autoridade** (seção `.autoridade`): opcionalmente troque o selo com emoji por uma foto real do criador/equipe.
- **Número de clientes** ("+4.000 cristianos"): ajuste para o número real e verificável antes de publicar.

## Componentes de conversão adicionados

- **Cronômetro** (`iniciarContador`): não usa uma data fixa — termina sempre à meia-noite no horário local de cada visitante, recalculado a cada carregamento de página. Não precisa de configuração.
- **Notificações de compra** (`.notif-compra`, canto superior esquerdo): pop-up simulado do tipo "Fulano de [cidade] acaba de comprar", com a cidade escolhida a partir do fuso horário do navegador do visitante (região aproximada). **Os dados são fictícios**, gerados no navegador — há um aviso em comentário no código. Troque por dados reais assim que houver volume de vendas (ex: via webhook da plataforma de pagamento). Prova social fabricada pode configurar publicidade enganosa em alguns países — avalie o risco antes de publicar.
- **Modal de oferta de saída / back-redirect** (`#modal-salida`): aparece 1x por sessão quando o lead tenta voltar pelo botão do navegador (ou move o mouse para fora da janela no desktop), oferecendo o Plan Completo pelo preço do Plan Básico por 10 minutos.
- **Dois planos** (`#oferta`): Plan Básico (só o produto principal) e Plan Completo (produto + 5 bônus). Cada um tem seu próprio link de checkout — não esqueça de configurar ambos.

## Rastreamento

- Meta Pixel dispara `PageView` automaticamente e `InitiateCheckout` ao clicar em qualquer CTA de compra (com o valor correto de cada plano).
- O evento `Purchase` **não** deve ser disparado no front-end — configure-o via webhook da plataforma de checkout (Conversions API), pois bloqueadores de anúncios impedem a captura no client-side.

## Deploy

Este repositório está conectado a um projeto na Vercel. Qualquer push na branch `main` gera um novo deploy automaticamente.
