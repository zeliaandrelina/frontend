# Grid CSS

O CSS Grid Layout é um sistema bidimensional para criar layouts complexos de forma simples e responsiva. Ele permite organizar elementos em linhas e colunas, facilitando o controle do posicionamento e do espaçamento.

---

## Ativando o Grid

Para usar o Grid, defina `display: grid` no container:

```css
.container {
    display: grid;
}
```

---

## Principais Propriedades do Container

### 1. `grid-template-columns` e `grid-template-rows`

Definem o número e o tamanho das colunas e linhas.

```css
.container {
    grid-template-columns: 200px 1fr 2fr;
    grid-template-rows: 100px auto;
}
```
- **`px`**: valor fixo em pixels (ex: `200px`).
- **`em`**: relativo ao tamanho da fonte do elemento.
- **`%`**: porcentagem em relação ao elemento pai.
- **`fr`**: fração do espaço disponível (ex: `1fr 2fr` divide em 1 parte e 2 partes).

### 2. `gap`, `row-gap`, `column-gap`

Espaçamento entre linhas e colunas.

```css
.container {
    gap: 20px; /* Espaço entre linhas e colunas */
    row-gap: 10px;
    column-gap: 30px;
}
```
- **`gap`**: define o espaçamento geral entre linhas e colunas.
- **`row-gap`**: define apenas o espaçamento entre linhas.
- **`column-gap`**: define apenas o espaçamento entre colunas.

### 3. `grid-template-areas`

Permite nomear áreas do grid para facilitar o posicionamento.

```css
.container {
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
}
```
- Cada string representa uma linha do grid.
- Palavras representam áreas nomeadas.
- Pontos (`.`) podem ser usados para áreas vazias.

### 4. `justify-items` e `align-items`

Alinha os itens nas células do grid.

```css
.container {
    justify-items: center; /* horizontal */
    align-items: stretch;  /* vertical */
}
```
- **`start`**: alinha ao início (esquerda/superior).
- **`end`**: alinha ao final (direita/inferior).
- **`center`**: centraliza.
- **`stretch`**: estica para preencher a célula (padrão).

### 5. `justify-content` e `align-content`

Alinha o grid dentro do container.

```css
.container {
    justify-content: space-between;
    align-content: center;
}
```
- **`start`**: alinha o grid ao início do container.
- **`end`**: alinha ao final.
- **`center`**: centraliza o grid.
- **`stretch`**: estica o grid para preencher o container.
- **`space-between`**: distribui o espaço igualmente entre as linhas/colunas, sem espaço nas extremidades.
- **`space-around`**: distribui o espaço com metade do espaço nas extremidades.
- **`space-evenly`**: distribui o espaço igualmente entre e nas extremidades.

### 6. `grid-auto-flow`

Controla o preenchimento automático das células.

```css
.container {
    grid-auto-flow: row; /* padrão */
}
```
- **`row`**: preenche por linhas.
- **`column`**: preenche por colunas.
- **`dense`**: tenta preencher espaços vazios automaticamente.
- **`row dense`**: linhas com preenchimento denso.
- **`column dense`**: colunas com preenchimento denso.

### 7. `grid-auto-rows` e `grid-auto-columns`

Define tamanho padrão para linhas/colunas criadas automaticamente.

```css
.container {
    grid-auto-rows: 100px;
    grid-auto-columns: 1fr;
}
```
- **`grid-auto-rows`**: altura padrão das linhas extras.
- **`grid-auto-columns`**: largura padrão das colunas extras.

---

## Propriedades dos Itens do Grid

### 1. `grid-column` e `grid-row`

Define início e fim do item no grid.

```css
.item {
    grid-column: 2 / 4; /* da coluna 2 até antes da 4 */
    grid-row: 1 / span 2; /* ocupa 2 linhas */
}
```
- **`grid-column: início / fim`**: define de onde até onde o item vai nas colunas.
- **`span`**: faz o item ocupar múltiplas linhas ou colunas.

### 2. `grid-area`

Associa o item a uma área nomeada ou define início/fim de linhas e colunas.

```css
.item {
    grid-area: header;
}
/* ou */
.item {
    grid-area: 1 / 2 / 3 / 4; /* linha início / coluna início / linha fim / coluna fim */
}
```
- **Nome da área**: associa ao nome definido em `grid-template-areas`.
- **Quatro valores**: linha início / coluna início / linha fim / coluna fim.

### 3. `justify-self` e `align-self`

Alinha individualmente o item na célula.

```css
.item {
    justify-self: end;
    align-self: center;
}
```
- **`start`**: início da célula.
- **`end`**: final da célula.
- **`center`**: centraliza.
- **`stretch`**: estica para preencher a célula.

---

## Exemplos Práticos

### Exemplo 1: Grid Básico

```html
<div class="container">
    <div>1</div>
    <div>2</div>
    <div>3</div>
</div>
```

```css
.container {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    gap: 10px;
}
```

### Exemplo 2: Grid com Áreas

```html
<div class="container">
    <header>Header</header>
    <aside>Sidebar</aside>
    <main>Main</main>
    <footer>Footer</footer>
</div>
```

```css
.container {
    display: grid;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
    grid-template-columns: 200px 1fr;
    grid-template-rows: 60px 1fr 40px;
    gap: 10px;
}
header { grid-area: header; }
aside { grid-area: sidebar; }
main { grid-area: main; }
footer { grid-area: footer; }
```

---

## 🚀 Atividade Prática 07

### Objetivo

Construir um layout de página usando CSS Grid, explorando as principais propriedades.

### Passos

1. **Estrutura HTML**
     ```html
     <div class="grid-exercicio">
         <header>Header</header>
         <nav>Menu</nav>
         <main>Conteúdo</main>
         <aside>Sidebar</aside>
         <footer>Footer</footer>
     </div>
     ```

2. **Defina o Container Grid**
     ```css
     .grid-exercicio {
         display: grid;
         grid-template-areas:
             "header header header"
             "nav main aside"
             "footer footer footer";
         grid-template-columns: 150px 1fr 200px;
         grid-template-rows: 60px 1fr 40px;
         gap: 15px;
         height: 100vh;
     }
     ```

3. **Associe as Áreas**
     ```css
     header { grid-area: header; background: #b3cde0; }
     nav { grid-area: nav; background: #6497b1; }
     main { grid-area: main; background: #005b96; color: #fff; }
     aside { grid-area: aside; background: #03396c; color: #fff; }
     footer { grid-area: footer; background: #011f4b; color: #fff; }
     ```

4. **Teste Propriedades**
     - Altere `grid-template-columns` para ver o efeito.
     - Modifique `gap` para ajustar espaçamento.
     - Use `justify-items` e `align-items` para alinhar o conteúdo.
     - Experimente `grid-auto-flow: dense;` e adicione mais elementos.

5. **Desafio Extra**
     - Adicione mais linhas/colunas.
     - Use `grid-column` e `grid-row` em elementos para sobrepor áreas.

---

## Referências

- [MDN Web Docs: CSS Grid Layout](https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Grid_Layout)
- [CSS Tricks: A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

