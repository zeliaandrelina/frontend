# Tailwind CSS – Prática Guiada Essencial

Objetivo: em ~2 horas você entende o 80/20 do uso diário construindo blocos pequenos e reaproveitáveis.  
Formato: explicação curta → você faz → sugestão de variação.

--------------------------------------------------

## 1. Visão 80/20 (Memorize Estes Grupos)

Você repete o tempo todo:
- Layout: `flex`, `grid`, `gap-*`, `p-*` / `m-*`, largura (`max-w-*`), breakpoints (`sm: md: lg:`).
- Tipografia: `text-sm|base|lg|xl`, `font-medium|semibold|bold`, `leading-tight|relaxed`, `tracking-tight`, `max-w-prose`.
- Cores & estados: `bg-* text-* border-* hover: focus-visible: dark: disabled:`.
- Componentes base: botão, card, input.
- Acessibilidade: foco visível (`focus-visible:*`), hierarquia de headings, texto alternativo para ícones.

Resumo mental ao montar algo: Estrutura → Tipografia → Cores/Estados → Ajustes responsivos → (só então) Reuso com `@apply`.

--------------------------------------------------

## 2. Setup Rápido

Instale Tailwind (Vite, PostCSS ou CLI). Arquivo mínimo `tailwind.config.js`:

```js
// tailwind.config.js
module.exports = {
    darkMode: 'class',
    content: ['./src/**/*.{html,js,jsx,ts,tsx,html}'],
    theme: {
        extend: {
            colors: {
                brand: { 50:'#eef6ff',100:'#d9ecff',500:'#1976d2',600:'#155fae',700:'#124d8d' }
            },
            keyframes: {
                fade: { '0%':{opacity:0,transform:'translateY(4px)'}, '100%':{opacity:1,transform:'translateY(0)'} }
            },
            animation: { 'fade-in':'fade .3s ease-out' }
        }
    },
    plugins: []
};
```

CSS de entrada (ex.: `src/index.css`):
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Crie um HTML simples, importe o CSS gerado. Se ao escrever `<div class="text-brand-600">Olá</div>` a cor aparece, está ok.

--------------------------------------------------

## 3. Mini Cheatsheet

Layout container: `max-w-5xl mx-auto px-4`  
Agrupar vertical: `flex flex-col gap-4` ou `space-y-4`  
Grid responsiva: `grid gap-6 sm:grid-cols-2 lg:grid-cols-3`  
Texto base: `text-sm sm:text-base leading-relaxed`  
Título seção: `text-xl sm:text-2xl font-semibold leading-tight`  
Botão linha (versão final):  
`inline-flex items-center justify-center font-medium rounded-md h-10 px-4 bg-brand-600 text-white hover:bg-brand-500 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 disabled:opacity-50 disabled:pointer-events-none transition-colors`  
Card linha:  
`rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 p-5 flex flex-col gap-3`  
Input linha:  
`w-full rounded-md border border-slate-300 dark:border-slate-600 bg-white dark:bg-slate-900 h-10 px-3 text-sm focus:border-brand-500 focus-visible:ring-2 focus-visible:ring-brand-500`

--------------------------------------------------

## 4. Microatividades (Faça em Ordem)

### 0. Verificar Ambiente (3min)
Crie `index.html`, importe o CSS. Teste:
```html
<p class="text-red-500">Funcionou?</p>
```
Se está vermelho, prossiga.

### 1. Base + Dark Mode Manual (5min)
Use a classe `dark` direto no `<html>` para testar tema escuro (sem JavaScript por enquanto):
```html
<html class="dark">
<body class="min-h-screen bg-white dark:bg-slate-900 text-slate-800 dark:text-slate-100 antialiased">
    <main class="p-4 space-y-10 max-w-4xl mx-auto"></main>
</body>
</html>
```
Depois remova/adicione `dark` e veja a mudança.

### 2. Cabeçalho e Ritmo de Leitura (6min)
Dentro de `<main>`:
```html
<header class="space-y-4">
    <h1 class="text-3xl sm:text-4xl font-bold leading-tight tracking-tight">Título Principal</h1>
    <p class="text-slate-600 dark:text-slate-300 max-w-prose">
        Resumo curto explicando a proposta do projeto em 1–2 linhas.
    </p>
</header>
```
Experimente trocar `text-3xl` por `text-2xl` em telas pequenas.

### 3. Botão Evolutivo (8min)
Comece simples:
```html
<button class="px-4 h-10 bg-brand-600 text-white rounded">Ação</button>
```
Adicione, um de cada vez:
1. `inline-flex items-center justify-center`
2. `font-medium`
3. `hover:bg-brand-500 transition-colors`
4. `focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500`
5. `disabled:opacity-50 disabled:pointer-events-none`

Crie variante outline:
```html
<button class="inline-flex items-center justify-center h-10 px-4 rounded font-medium border border-slate-300 dark:border-slate-600 hover:bg-slate-50 dark:hover:bg-slate-800 transition-colors">
    Ação
</button>
```

### 4. Card Simples (8min)
```html
<div class="rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 p-5 flex flex-col gap-3 max-w-sm">
    <h3 class="font-semibold text-lg">Título</h3>
    <p class="text-sm text-slate-500 dark:text-slate-400">Breve descrição do conteúdo do card.</p>
    <button class="text-sm text-brand-600 hover:underline inline-flex w-fit">Saiba mais</button>
</div>
```
Teste adicionar `shadow-sm` e depois `hover:shadow` no card.

### 5. Navbar Simples (8min)
```html
<nav class="sticky top-0 z-40 bg-white/80 dark:bg-slate-900/70 backdrop-blur border-b border-slate-200 dark:border-slate-800">
    <div class="max-w-6xl mx-auto h-14 flex items-center justify-between px-4">
        <span class="font-bold text-brand-600">LOGO</span>
        <ul class="hidden md:flex gap-6 text-sm">
            <li><a class="hover:text-brand-600 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 rounded" href="#">Item</a></li>
            <li><a class="hover:text-brand-600 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 rounded" href="#">Item</a></li>
        </ul>
    </div>
</nav>
```
Verifique comportamento ao reduzir a largura (links somem em mobile).

### 6. Mini Hero (10min)
```html
<section class="py-16">
    <div class="max-w-5xl mx-auto px-4 space-y-6 lg:grid lg:grid-cols-2 lg:gap-12 lg:space-y-0">
        <div class="space-y-6">
            <h2 class="text-4xl font-bold leading-tight tracking-tight">Construa rápido</h2>
            <p class="text-slate-600 dark:text-slate-300 max-w-md">Texto curto explicando o valor principal.</p>
            <div class="flex gap-4">
                <button class="inline-flex items-center justify-center font-medium rounded-md h-11 px-6 bg-brand-600 text-white hover:bg-brand-500 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 transition-colors">Começar</button>
                <button class="inline-flex items-center justify-center font-medium rounded-md h-11 px-6 border border-slate-300 dark:border-slate-600 hover:bg-slate-50 dark:hover:bg-slate-800 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 transition-colors">Ver Código</button>
            </div>
        </div>
        <div class="mt-10 lg:mt-0">
            <div class="aspect-video w-full rounded-xl bg-gradient-to-br from-brand-50 to-brand-100 dark:from-slate-700 dark:to-slate-600 flex items-center justify-center text-brand-600 dark:text-brand-100 font-medium">
                Imagem / Ilustração
            </div>
        </div>
    </div>
</section>
```

### 7. Grid de Features (10min)
```html
<section class="py-12 px-4">
    <h3 class="text-xl font-semibold mb-6">Recursos</h3>
    <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <div class="rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 p-5 flex flex-col gap-2">
            <div class="w-10 h-10 rounded-md bg-brand-600 text-white flex items-center justify-center text-sm">🙂</div>
            <h4 class="font-medium">Título</h4>
            <p class="text-sm text-slate-500 dark:text-slate-400">Breve explicação.</p>
        </div>
        <!-- Duplique e troque emoji / título -->
    </div>
</section>
```

### 8. Formulário Básico (12min)
```html
<form class="space-y-5 max-w-md">
    <div class="space-y-1">
        <label for="nome" class="text-sm font-medium">Nome</label>
        <input id="nome" class="w-full rounded-md border border-slate-300 dark:border-slate-600 bg-white dark:bg-slate-900 h-10 px-3 text-sm placeholder-slate-400 focus:border-brand-500 focus-visible:ring-2 focus-visible:ring-brand-500" placeholder="Seu nome">
    </div>
    <div class="space-y-1">
        <label for="email" class="text-sm font-medium">Email</label>
        <input id="email" type="email" class="w-full rounded-md border border-slate-300 dark:border-slate-600 bg-white dark:bg-slate-900 h-10 px-3 text-sm placeholder-slate-400 focus:border-brand-500 focus-visible:ring-2 focus-visible:ring-brand-500" placeholder="voce@exemplo.com">
        <p class="text-xs text-slate-500">Somente contato.</p>
    </div>
    <button class="inline-flex items-center justify-center font-medium rounded-md h-11 px-6 bg-brand-600 text-white hover:bg-brand-500 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 transition-colors">
        Enviar
    </button>
</form>
```
Simule erro adicionando `border-red-500` no input.

### 9. Reuso com @apply (8min)
Quando repetir MUITO, extraia:
```css
@layer components {
    .btn { @apply inline-flex items-center justify-center font-medium rounded-md h-11 px-6 transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 disabled:opacity-50 disabled:pointer-events-none; }
    .btn-primary { @apply btn bg-brand-600 text-white hover:bg-brand-500; }
    .btn-outline { @apply btn border border-slate-300 dark:border-slate-600 hover:bg-slate-50 dark:hover:bg-slate-800; }
    .card { @apply rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 p-5 flex flex-col gap-3; }
    .input { @apply w-full rounded-md border border-slate-300 dark:border-slate-600 bg-white dark:bg-slate-900 h-10 px-3 text-sm placeholder-slate-400 focus:border-brand-500 focus-visible:ring-2 focus-visible:ring-brand-500; }
}
```
Regra rápida: só extraia após usar 3+ vezes.

### 10. Responsividade (6min)
Cheque:
- Hero: `lg:grid lg:grid-cols-2`
- Navbar: `hidden md:flex`
- Features: `sm:grid-cols-2 lg:grid-cols-3`
Teste largura pequena → média → grande.

### 11. Dark Mode (6min)
Para cada:
- Fundo claro (`bg-white`) → par escuro (`dark:bg-slate-800|900`)
- Texto secundário → `text-slate-500 dark:text-slate-400`
Evite contrastes fracos (texto cinza claro demais no fundo escuro).

### 12. Acessibilidade Básica (6min)
- Foco visível: use `focus-visible:ring-2`.
- Headings em ordem (`h1` único).
- Ícone sem texto → incluir `<span class="sr-only">Descrição</span>`.
- Botões descrevem ação claramente.

### 13. Limpeza Final (5min)
- Remova classes não usadas.
- Verifique se não há cores soltas fora da paleta (`brand`, `slate`).
- Simplifique onde empilhou classes redundantes.

--------------------------------------------------

## 5. Extras Rápidos (Se Sobraram 15min)
- Botão “ghost”: só `hover:bg-slate-100 dark:hover:bg-slate-800`.
- Badge/contador: absoluto em um card `absolute top-2 right-2`.
- Instalar plugin e usar `line-clamp-2` em descrições longas.

(Modal exige JavaScript mínimo; deixe para depois de dominar o básico acima.)

--------------------------------------------------

## 6. Checklist Final
[ ] Layout responde em sm/md/lg  
[ ] Dark mode alterna (classe `dark`)  
[ ] Foco visível em links e botões  
[ ] Componentes base (botão, card, input) consistentes  
[ ] Reuso só onde compensa  
[ ] Headings hierárquicos  
[ ] Sem classes supérfluas

--------------------------------------------------

## 7. Próximos Passos
- Adicionar seção de blog (cards com imagem + texto).
- Inserir gráfico em um card (lib externa).
- Criar tokens extras: espaçamentos, sombras e animações suaves.

Resumo: pratique blocos pequenos → combine → extraia padrões depois de repetir. Clareza e consistência primeiro; personalização avançada depois.