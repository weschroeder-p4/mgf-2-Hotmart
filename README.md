# Mapa da Gestão Financeira — Página de Vendas (Nova versão 2 — Hotmart (teste))

Landing page estática de vendas do **Mapa da Gestão Financeira** (P4 Gestão).
Domínio de publicação: **https://mgf2.wesleyschroeder.com.br**

Site 100% estático (HTML + CSS inline + 1 pequeno JS do contador). Fontes e ícones
são **self-hosted** (sem CDN) e otimizados. Sem build, sem dependências externas de render.

## Estrutura

```
.
├── index.html            # Página servida na raiz do domínio
├── images/               # WebP (primário) + PNG (fallback)
│   ├── hero-mockup.{webp,png}        mockup do hero (transparente)
│   ├── mockup-dashboard.{webp,png}   dashboard (transparente)
│   ├── custo.{webp,png}              foto da seção "custo"
│   ├── autor-wesley.{webp,png}       foto do autor
│   ├── passo-01..04.{webp,png}       telas dos 4 passos
│   └── oferta-mgf / oferta-combo .{webp,png}  mockups dos cards de oferta
├── fonts/                # Fontes self-hosted e reduzidas (subset)
│   ├── inter-400/500/600/700.woff2   (~16 KB cada)
│   └── tabler-mgf.woff2              (ícones usados, ~7 KB)
├── _headers              # Headers de cache e segurança do Cloudflare Pages
├── .gitignore
└── README.md
```

## Integrações já configuradas

- **Meta Pixel** `3103391829973250` — PageView no load + InitiateCheckout no clique dos botões.
- **Botões de compra:**
  - Mapa (R$ 67 à vista / 9x R$ 8,80): `https://pay.hotmart.com/F108045307E?checkoutMode=10`
  - Combo 3x1 (R$ 117 à vista / 12x R$ 12,10): `https://pay.hotmart.com/M108099399C`
- **Contador** regressivo até o fim do dia (reinicia diariamente).
- **SEO/Social:** canonical e Open Graph apontando para o domínio acima.

---

## Publicar no Cloudflare Pages

### Opção A — Direct Upload (mais rápido, sem GitHub)

1. Acesse https://dash.cloudflare.com → **Workers & Pages** → **Create** → aba **Pages** →
   **Upload assets**.
2. Dê um nome ao projeto (ex.: `mgf2`) e **arraste a pasta inteira** `MGF-Nova versão 2 — Hotmart (teste)`
   (ou um .zip dela). Clique em **Deploy**. Em ~1 min o site fica em `https://mgf1.pages.dev`.
3. Para atualizar depois: no projeto → **Create new deployment** → suba a pasta de novo.

### Opção B — GitHub (deploy automático a cada push)

1. Crie um repositório no GitHub e suba esta pasta:
   ```bash
   git init && git add . && git commit -m "MGF nova versão 1"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/mgf1.git
   git push -u origin main
   ```
2. Cloudflare → Pages → **Connect to Git** → selecione o repo.
   - Framework preset: **None** · Build command: *(vazio)* · Output directory: `/`
3. A cada `git push` para `main`, o deploy é automático.

---

## Apontar o domínio mgf2.wesleyschroeder.com.br

No projeto do Pages → aba **Custom domains** → **Set up a custom domain** →
digite `mgf2.wesleyschroeder.com.br` → **Continue**.

- **Se `wesleyschroeder.com.br` já está na sua conta Cloudflare:** o registro é criado
  automaticamente. SSL sai em minutos. Pronto.
- **Se o DNS está em outro lugar** (Registro.br, Hostinger, etc.): crie um registro
  **CNAME** `mgf2` apontando para `mgf1.pages.dev` (ou o endereço `.pages.dev` que o
  Cloudflare indicar). Depois volte e conclua a verificação no Pages.

---

## Dicas finais

- No Cloudflare, **Speed → Optimization**: ative Brotli (normalmente já vem ligado).
- Teste a performance real em https://pagespeed.web.dev depois de publicar.
- Valide o pixel com a extensão **Meta Pixel Helper** na página já no ar.
- Revise as respostas do FAQ (principalmente a de **garantia**) antes de divulgar.
