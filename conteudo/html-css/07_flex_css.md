# Flexbox em CSS

O Flexbox é um módulo do CSS que facilita a criação de layouts flexíveis e responsivos. Ele permite alinhar, distribuir e organizar elementos de forma eficiente, mesmo quando o tamanho dos itens é desconhecido ou dinâmico.

---

## 1. Conceitos Básicos

### O que é Flexbox?

Flexbox (Flexible Box Layout) é um modelo de layout unidimensional que organiza elementos em linhas ou colunas, facilitando o alinhamento e a distribuição do espaço entre eles.

### Como ativar o Flexbox?

Basta adicionar a propriedade `display: flex;` ao elemento container.

```css
.container {
    display: flex;
}
```

---

## 2. Propriedades do Container

### `flex-direction`

Define a direção dos itens dentro do container flex.

- `row` (padrão): organiza os itens em uma linha, da esquerda para a direita.
- `row-reverse`: organiza os itens em uma linha, da direita para a esquerda.
- `column`: organiza os itens em uma coluna, de cima para baixo.
- `column-reverse`: organiza os itens em uma coluna, de baixo para cima.

```css
.container {
    flex-direction: row;
}
```

### `flex-wrap`

Controla se os itens devem ou não quebrar linha quando não couberem no container.

- `nowrap` (padrão): todos os itens permanecem em uma única linha, mesmo que ultrapassem o tamanho do container.
- `wrap`: os itens quebram para a próxima linha quando necessário.
- `wrap-reverse`: os itens quebram para a linha acima, ao invés de abaixo.

```css
.container {
    flex-wrap: wrap;
}
```

### `justify-content`

Alinha os itens ao longo do eixo principal (horizontal em `row`, vertical em `column`).

- `flex-start` (padrão): itens alinhados ao início do container.
- `flex-end`: itens alinhados ao final do container.
- `center`: itens centralizados no container.
- `space-between`: espaço igual entre os itens, sem espaço nas extremidades.
- `space-around`: espaço igual ao redor de cada item.
- `space-evenly`: espaço igual entre todos os itens e também nas extremidades.

```css
.container {
    justify-content: center;
}
```

### `align-items`

Alinha os itens ao longo do eixo cruzado (vertical em `row`, horizontal em `column`).

- `stretch` (padrão): itens esticam para preencher o container.
- `flex-start`: itens alinhados ao início do eixo cruzado.
- `flex-end`: itens alinhados ao final do eixo cruzado.
- `center`: itens centralizados no eixo cruzado.
- `baseline`: itens alinhados pela linha de base do texto.

```css
.container {
    align-items: center;
}
```

### `align-content`

Alinha as linhas do container flex quando há quebra de linha (ou seja, quando `flex-wrap` está ativo).

- `flex-start`: linhas agrupadas no início do container.
- `flex-end`: linhas agrupadas no final do container.
- `center`: linhas centralizadas no container.
- `space-between`: espaço igual entre as linhas.
- `space-around`: espaço igual ao redor de cada linha.
- `stretch` (padrão): linhas esticam para preencher o container.

```css
.container {
    align-content: space-between;
}
```

---

## 3. Propriedades dos Itens

### `flex-grow`

Define quanto o item pode crescer em relação aos outros itens dentro do container quando há espaço extra disponível.

- Valor padrão: `0` (não cresce).
- Exemplo: Se um item tem `flex-grow: 2` e outro tem `flex-grow: 1`, o primeiro crescerá o dobro do segundo.

```css
.item {
    flex-grow: 2;
}
```

### `flex-shrink`

Define quanto o item pode encolher em relação aos outros itens quando o espaço é insuficiente.

- Valor padrão: `1` (pode encolher).
- Exemplo: Se um item tem `flex-shrink: 2` e outro tem `flex-shrink: 1`, o primeiro encolherá o dobro do segundo.

```css
.item {
    flex-shrink: 1;
}
```

### `flex-basis`

Define o tamanho inicial do item antes da distribuição do espaço restante.

- Pode ser um valor em px, %, etc.
- Valor padrão: `auto` (tamanho do conteúdo).

```css
.item {
    flex-basis: 200px;
}
```

### `flex`

Atalho para definir `flex-grow`, `flex-shrink` e `flex-basis` em uma única linha.

- Sintaxe: `flex: <grow> <shrink> <basis>;`
- Exemplo: `flex: 1 1 150px;` (cresce, encolhe e tem tamanho inicial de 150px).

```css
.item {
    flex: 1 1 150px;
}
```

### `align-self`

Permite sobrescrever o alinhamento individual de um item no eixo cruzado, ignorando o `align-items` do container.

- Valores: `auto` (padrão), `flex-start`, `flex-end`, `center`, `baseline`, `stretch`.

```css
.item {
    align-self: flex-end;
}
```

---

## 4. Exemplo Prático

```html
<div class="container">
    <div class="item">A</div>
    <div class="item">B</div>
    <div class="item">C</div>
</div>
```

```css
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height: 200px;
    background: #f0f0f0;
}

.item {
    background: #4f8ef7;
    color: #fff;
    padding: 20px;
    margin: 10px;
    border-radius: 8px;
    flex: 1 1 100px;
    text-align: center;
}
```

---

## 🚀 Atividade Prática 07

### Desafio: Layout de Cards Responsivos

**Objetivo:** Criar um layout de cards responsivos usando Flexbox.

#### Requisitos

1. Crie um container com 6 cards.
2. Os cards devem se alinhar lado a lado em telas grandes e quebrar para baixo em telas menores.
3. O espaçamento entre os cards deve ser uniforme.
4. Cada card deve ter um título, uma imagem e uma breve descrição.
5. Os cards devem ocupar o mesmo tamanho, independentemente do conteúdo.

#### Exemplo de Estrutura HTML

```html
<div class="cards-container">
    <div class="card">
        <img src="imagem1.jpg" alt="Imagem 1">
        <h3>Título 1</h3>
        <p>Descrição do card 1.</p>
    </div>
    <!-- Repita para os outros cards -->
</div>
```

#### Exemplo de CSS

```css
.cards-container {
    display: flex;
    flex-wrap: wrap;
    gap: 24px;
    justify-content: center;
}

.card {
    flex: 1 1 250px;
    max-width: 300px;
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    padding: 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.card img {
    width: 100%;
    height: 160px;
    object-fit: cover;
    border-radius: 8px;
    margin-bottom: 12px;
}
```

#### Dicas

- Use `gap` para espaçamento entre os cards.
- Use `flex-basis` e `max-width` para limitar o tamanho dos cards.
- Teste em diferentes tamanhos de tela para garantir a responsividade.

---

**Experimente modificar as propriedades do Flexbox e observe como o layout se adapta!**