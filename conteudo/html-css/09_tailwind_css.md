# Guia Prático de Tailwind CSS (Revisado)

Tailwind CSS é um framework de utilitários que fornece classes atômicas (ex: p-4, flex, text-center) para você compor qualquer interface diretamente no markup, sem depender de componentes pré-prontos. Diferente de soluções opinativas (ex: Bootstrap), ele evita sobrecarga de estilos, elimina sobrescrições e dá total liberdade de design.

## Por que usar Tailwind?

- Flexibilidade: você cria o design exato, sem “lutar” contra estilos herdados.
- Velocidade: reduz CSS manual; o protótipo vira produção com poucos ajustes.
- Escalabilidade: um design system emergente baseado em tokens configuráveis.
- Consistência: spacing, cores e tipografia padronizados via config.
- Performance: geração apenas das classes usadas (JIT nativo desde a v3).
- Mercado: amplamente adotado em produtos modernos, especialmente com frameworks JS.

---

## 1. Conceito Essencial

Tailwind fornece utilitários coesos para layout, tipografia, cores, espaçamento, efeitos, estados (hover/focus), dark mode e responsividade. Você pode evitar quase todo CSS manual, reservando-o a raros casos via @layer.

---

## 2. Instalação e Configuração

### Uso Rápido (CDN) – prototipagem

```html
<script src="https://cdn.tailwindcss.com"></script>
```

Opcional: customização inline
```html
<script>
  tailwind.config = {
    theme: { extend: { colors: { brand: '#1e40af' } } }
  }
</script>
```

### Ambiente de Projeto (Build)

1. Instalar:
```bash
npm install -D tailwindcss autoprefixer postcss
npx tailwindcss init -p
```

2. Ajustar `tailwind.config.js` (paths corretos):
```js
module.exports = {
  content: [
    "./public/**/*.html",
    "./src/**/*.{html,js,ts,jsx,tsx,vue,svelte}"
  ],
  theme: {
    extend: {
      colors: { primary: "#1e40af" },
      fontFamily: { sans: ["Inter", "ui-sans-serif", "system-ui"] }
    }
  },
  darkMode: "class",
  plugins: []
}
```

3. Criar `src/input.css`:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;

/* Exemplo de componente custom */
@layer components {
  .btn-primary {
    @apply px-4 py-2 rounded bg-primary text-white font-medium hover:bg-primary/90 transition;
  }
}
```

4. Rodar em modo watch:
```bash
npx tailwindcss -i ./src/input.css -o ./public/assets/css/styles.css --watch
```

5. Build de produção (purga + minificação automática):
```bash
NODE_ENV=production npx tailwindcss -i ./src/input.css -o ./public/assets/css/styles.css --minify
```

---

## 3. Estrutura de Utilitários (Exemplos)

- Espaçamento: p-4, px-6, my-8
- Cores: bg-primary, text-slate-700, border-red-500
- Tipografia: text-sm, text-xl, font-semibold, leading-tight, tracking-wide
- Layout: flex, grid, inline-flex, items-center, justify-between
- Borda & raio: border, border-2, rounded, rounded-xl
- Efeitos: shadow, shadow-lg, ring, ring-offset-2
- Transição / animação: transition, duration-300, ease-in-out, animate-pulse
- Estados: hover:bg-blue-600, focus:ring-2, disabled:opacity-50
- Dark mode: dark:bg-slate-800 dark:text-slate-100

Exemplo:
```html
<button class="btn-primary flex items-center gap-2">
  <svg class="w-4 h-4" ...></svg>
  Enviar
</button>
```

---

## 4. Responsividade

Breakpoints padrão:
sm ≥640px | md ≥768px | lg ≥1024px | xl ≥1280px | 2xl ≥1536px

```html
<p class="text-base md:text-lg lg:text-xl">Texto responsivo</p>
<div class="flex flex-col md:flex-row gap-4">
  <div class="flex-1 bg-slate-100 p-4">Item A</div>
  <div class="flex-1 bg-slate-100 p-4">Item B</div>
</div>
```

### Grid
```html
<section class="grid gap-6 grid-cols-1 md:grid-cols-3">
  <article class="p-4 bg-primary/10 rounded">1</article>
  <article class="p-4 bg-primary/10 rounded">2</article>
  <article class="p-4 bg-primary/10 rounded">3</article>
</section>
```

### Utilitários para Layout
- Espaço interno automático entre filhos: space-x-4 / space-y-4
- Ordem: order-1, md:order-2
- Visibilidade: hidden, md:block
- Overflow: overflow-auto, truncate (em conjunto com w- e whitespace-nowrap)
- Posicionamento: relative, absolute, fixed, sticky, inset-0
- Z-index: z-10, z-50
- Container centralizado: max-w-7xl mx-auto px-4

---

## 5. Customização Profunda

Exemplo extend:
```js
extend: {
  spacing: { '4.5': '1.125rem' },
  colors: {
    brand: {
      50:'#eef5ff',100:'#d9e9ff',500:'#1e40af',600:'#173891'
    }
  },
  boxShadow: { card: "0 4px 16px -2px rgba(0,0,0,.1)" }
}
```

Dark mode: adicione a classe `dark` no <html> e use variantes `dark:`.

---

## 6. Plugins

Instalar plugin de formulários:
```bash
npm i -D @tailwindcss/forms
```

Adicionar:
```js
plugins: [require('@tailwindcss/forms')]
```

Uso do plugin typography:
```bash
npm i -D @tailwindcss/typography
```
```js
plugins: [require('@tailwindcss/typography')]
```
```html
<article class="prose dark:prose-invert">
  <h1>Título</h1>
  <p>Texto formatado.</p>
</article>
```

---

## 7. Boas Práticas

- Comece utilitário; extraia componentes apenas quando repetir >2–3 vezes.
- Use nomes utilitários + camadas personalizadas com @layer components.
- Prefira tokens do design system (config) a valores mágicos arbitrários.
- Combine semântica HTML + utilidades (acessibilidade primeiro).
- Evite cascatas complexas; pense em composição.
- Ative produção antes de medir performance (classes não usadas somem).
- Agrupe estados e variantes: md:hover:bg-primary/90.

---

## 8. Exemplo Completo de Card

```html
<div class="max-w-2xl mx-auto bg-white dark:bg-slate-800 rounded-xl shadow-card overflow-hidden">
  <div class="md:flex">
    <img class="h-48 w-full object-cover md:h-full md:w-56" src="imagem.jpg" alt="Ilustração">
    <div class="p-6 space-y-3">
      <span class="uppercase text-xs tracking-wide text-primary font-semibold">Tailwind CSS</span>
      <h2 class="text-xl font-medium text-slate-900 dark:text-slate-100">Tutorial Completo</h2>
      <p class="text-slate-600 dark:text-slate-300">Crie interfaces modernas, acessíveis e escaláveis.</p>
      <a href="#" class="inline-block text-primary hover:underline font-medium">Saiba mais</a>
    </div>
  </div>
</div>
```

---

## 9. Atividade Prática 09: One Page Responsiva

Crie um site one page com:

Requisitos:
- Navbar fixa (scroll suave para âncoras).
- Seções: Home, Sobre, Serviços, Portfólio, Contato.
- Estrutura mobile-first.
- Cores / fontes customizadas no config.
- Formulário acessível (labels, aria-invalid).
- Transições e hovers consistentes.
- Imagens otimizadas (lazy loading).
- Rodapé com links e redes sociais.
- Botão “voltar ao topo”.
- Suporte a dark mode (toggle adicionando/removendo classe no html).

Passos Sugeridos:
1. Setup + config base.
2. Criar tokens (cores, fontes, spacing extras).
3. Navbar responsiva (menu hambúrguer usando hidden / flex).
4. Hero com CTA: gradiente + tipografia escalável.
5. Sobre: grid md:grid-cols-2 (texto + imagem).
6. Serviços: cards em grid, ícones SVG com stroke-current.
7. Portfólio: grid responsivo c/ hover:scale-105 transition.
8. Contato: form usando plugin forms + validação simples JS.
9. Footer: colunas de links + direitos.
10. Acessibilidade: foco visível (focus:ring), landmarks (nav/main/footer).
11. Performance: build produção + imagens comprimidas.
12. Extras: animações sutis (animate-fade via plugin ou util custom).

Dica: prototipe no Playground: https://play.tailwindcss.com/

---

## 10. Erros Comuns

- Esquecer paths corretos no content (gera CSS enorme).
- Usar valores inline repetidos (ex: style="margin-top:13px") ao invés de extender spacing.
- Criar componentes CSS cedo demais (perde agilidade inicial).
- Ignorar contraste (verificar dark mode).
- Overengineering de classes condicionalmente em JS sem patterns (use libs de composição de classes quando necessário).

---

## 11. Checklist Rápido

- Config content correto
- Tokens definidos (cores, fontes, spacing)
- Dark mode funcional
- Componentes extraídos somente quando DRY
- Formulário acessível
- Build de produção minificado
- Teste em breakpoints principais
- Lighthouse ≥ boas notas de performance e acessibilidade

---

## 12. Referências e Recursos

- Documentação: https://tailwindcss.com/docs
- Playground: https://play.tailwindcss.com/
- Customização (Theme): https://tailwindcss.com/docs/theme
- Plugins Oficiais: https://tailwindcss.com/docs/plugins
- Acessibilidade: https://tailwindcss.com/docs/accessibility
- Componentes de Inspiração: https://tailwindui.com/
- Exemplos Open Source: https://github.com/tailwindlabs
- Dark Mode: https://tailwindcss.com/docs/dark-mode

---

Dominar Tailwind = fluxo rápido + design consistente + escalabilidade. Pratique compondo blocos reais e refinando tokens centrais. Boa criação!