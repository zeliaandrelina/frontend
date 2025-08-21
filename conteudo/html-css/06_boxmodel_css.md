# 📦 Box Model - CSS Moderno

O **Box Model** é a base do layout web: todo elemento HTML é uma caixa composta por conteúdo, preenchimento, borda e margem. Dominar o Box Model é essencial para criar layouts responsivos e modernos.

---

## 1\. Anatomia da Caixa: Camadas do Box Model

Cada elemento tem quatro camadas principais:

- **Content:** O conteúdo real (texto, imagem, etc).
- **Padding:** Espaço interno entre o conteúdo e a borda.
- **Border:** Linha ao redor do padding e conteúdo.
- **Margin:** Espaço externo, separando a caixa de outros elementos.

### Exemplo

```css
.card {
    width: min(100%, 320px);
    padding: 1.5rem;
    border: 1px solid #e0e0e0;
    margin: 1rem auto;
    border-radius: 1rem;
    background: linear-gradient(135deg, #f9f9f9 80%, #e3f2fd 100%);
    box-shadow: 0 2px 8px #0001;
    transition: box-shadow 0.2s;
}
.card:hover {
    box-shadow: 0 8px 24px #0002;
}
```

**Dicas modernas:**
- Use `rem` ou `em` para espaçamentos responsivos.
- `min()` e `max()` ajudam a limitar tamanhos.
- `box-shadow` e `border-radius` criam visuais suaves.

---

## 2\. Tamanho e Cálculo: `width`, `height`, `box-sizing`

Por padrão, `width` e `height` afetam só o conteúdo. O padding e a borda são somados. Para facilitar, use:

```css
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

Assim, o tamanho total do elemento inclui padding e borda, tornando o layout previsível.

### Novidades úteis

- **`aspect-ratio`:** Define proporção fixa da caixa.
- **`gap`:** Espaçamento entre itens em layouts flex/grid.
- **`container queries`:** Adapta estilos ao tamanho do contêiner (suporte crescente).

---

## 3\. Exemplo Prático

```html
<div class="cards">
    <article class="card">
        <h2>Starter</h2>
        <p>Ideal para projetos simples.</p>
    </article>
    <article class="card">
        <h2>Pro</h2>
        <p>Recursos avançados e suporte.</p>
    </article>
    <article class="card">
        <h2>Enterprise</h2>
        <p>Para grandes equipes e demandas.</p>
    </article>
</div>
```

```css
.cards {
    display: flex;
    gap: 2rem;
    flex-wrap: wrap;
    justify-content: center;
    padding: 2rem;
}
```

---

## 🚀 Atividade Prática 06

1. Crie um arquivo `meus-cards.html`.
2. Adicione um container com três `<article class="card">`.
3. No CSS, aplique:
        - `box-sizing: border-box` universal.
        - `.card` com largura máxima, padding, borda, margem, cor de fundo e borda arredondada.
        - Use `gap` no container para espaçamento.
4. Experimente adicionar `aspect-ratio` ou `box-shadow` para um visual moderno.

Abra no navegador e veja cards responsivos, bonitos e alinhados com as melhores práticas atuais.