# Check List Veículos Pesados — PWA

## Estrutura de Arquivos

```
checklist-pwa/
├── index.html        ← Aplicação principal (HTML + CSS + JS)
├── manifest.json     ← Manifesto PWA (ícones, nome, cores, atalhos)
├── sw.js             ← Service Worker (cache offline, sync)
├── icons/
│   ├── icon-192.png  ← Ícone 192×192 (tela inicial Android)
│   └── icon-512.png  ← Ícone 512×512 (splash screen)
└── README.md
```

## Como publicar (opções gratuitas)

### 1. GitHub Pages (recomendado)
1. Crie um repositório no GitHub
2. Envie todos os arquivos para a branch `main`
3. Vá em **Settings → Pages → Deploy from branch → main → / (root)**
4. Acesse: `https://<seu-usuario>.github.io/<repo>/`

### 2. Netlify (arrastar e soltar)
1. Acesse [netlify.com/drop](https://app.netlify.com/drop)
2. Arraste a pasta `checklist-pwa` inteira
3. URL gerada automaticamente (HTTPS obrigatório para PWA)

### 3. Vercel
```bash
npm i -g vercel
cd checklist-pwa
vercel
```

> ⚠️ **HTTPS é obrigatório** para Service Workers e instalação PWA.
> Não funciona em `file://` ou `http://` locais.

## Instalar como App

### Android (Chrome)
- Abra a URL no Chrome
- O banner "Instalar Check List" aparecerá automaticamente
- Ou: menu **⋮ → Adicionar à tela inicial**

### iPhone / iPad (Safari)
- Abra no Safari
- Toque em **Compartilhar → Adicionar à Tela de Início**

### Desktop (Chrome/Edge)
- Clique no ícone de instalar (⊕) na barra de endereços

## Funcionamento Offline

O Service Worker (`sw.js`) usa a estratégia **Stale While Revalidate**:
- Primeira visita: faz cache de todos os recursos
- Visitas seguintes: carrega instantaneamente do cache, atualiza em background
- Sem internet: funciona completamente offline
- Dados do formulário: salvos no `localStorage` mesmo offline
- Quando voltar online: exibe toast "Conexão restaurada" e tenta sincronizar

## Customização de Ícones

Substitua os arquivos em `icons/` por PNGs reais com:
- `icon-192.png` — 192×192 px
- `icon-512.png` — 512×512 px

Use o [Maskable.app](https://maskable.app) para verificar compatibilidade.

## Supabase

As credenciais estão em `index.html` nas constantes:
```js
const SUPABASE_URL  = 'https://...supabase.co';
const SUPABASE_ANON = 'eyJ...';
```

## Versão

`v2.0 PWA · Auto-Save · Fotos 30 dias · Offline Ready`
