✍️ Usando elementos para dar vida ao HTML

O HTML é a base de toda página web. Ele serve para estruturar, organizar e dar significado ao conteúdo, facilitando tanto a leitura para usuários quanto a compreensão por mecanismos de busca como o Google. Utilizar corretamente as tags HTML é fundamental para criar páginas acessíveis, bem organizadas e preparadas para SEO (Search Engine Optimization).

-----

## 1\. Hierarquia da Informação: Títulos (`<h1>` a `<h6>`)

Títulos são essenciais para dividir o conteúdo em seções e subseções, criando uma hierarquia lógica e facilitando a navegação, inclusive para leitores de tela e indexadores de busca. O HTML oferece seis níveis de títulos, do mais importante (`<h1>`) ao menos importante (`<h6>`).

- `<h1>`: **Título Principal**. Cada página deve ter **apenas um `<h1>`**, representando o assunto central.
- `<h2>`: Títulos de seções principais.
- `<h3>`: Subtítulos de seções.
- `<h4>`, `<h5>`, `<h6>`: Títulos para subdivisões mais específicas.

Pense nos títulos como um sumário de livro: `<h1>` é o título do livro, `<h2>` são os capítulos, `<h3>` as seções dentro dos capítulos, e assim por diante.

**Exemplo:**

```html
<main>
    <h1>A História da Computação</h1>
    <section>
        <h2>Os Primeiros Computadores</h2>
        <p>Nesta seção, exploramos as máquinas pioneiras...</p>
        <h3>O ENIAC</h3>
        <p>O ENIAC foi um dos primeiros computadores eletrônicos de grande escala...</p>
    </section>
    <section>
        <h2>A Revolução dos Computadores Pessoais</h2>
        <p>A década de 80 marcou a ascensão dos PCs...</p>
    </section>
</main>
```

> **Dica:** Use sempre as tags de título de forma sequencial e sem pular níveis para garantir acessibilidade e boa estrutura semântica. Nunca use tags de título apenas para deixar o texto maior ou em negrito; a função delas é semântica.

-----

## 2\. Estruturando o Texto: Parágrafos e Blocos Semânticos

A tag `<p>` agrupa frases em parágrafos, separando visualmente e semanticamente o texto. Além dela, o HTML5 trouxe novas tags semânticas para organizar melhor o conteúdo:

- `<section>`: Agrupa seções tematicamente relacionadas.
- `<article>`: Indica um conteúdo independente, como posts de blog ou notícias.
- `<aside>`: Conteúdo complementar, como barras laterais.
- `<nav>`: Agrupa links de navegação.
- `<header>` e `<footer>`: Cabeçalho e rodapé de uma página ou seção.

**Exemplo:**

```html
<article>
    <header>
        <h1>O Futuro da Web</h1>
        <p>Publicado em <time datetime="2024-06-01">1 de junho de 2024</time></p>
    </header>
    <section>
        <h2>HTML5 e Semântica</h2>
        <p>O uso de tags semânticas melhora a acessibilidade e o SEO.</p>
    </section>
    <footer>
        <p>Autor: <strong>Maria Silva</strong></p>
    </footer>
</article>
```

-----

## 3\. Ênfase, Importância e Destaques: `<em>`, `<strong>`, `<mark>`, `<b>`, `<i>`

Para destacar partes do texto, utilize:

- **`<strong>`**: Indica importância ou urgência. Exibido em negrito.
- **`<em>`**: Dá ênfase, alterando o sentido da frase. Exibido em itálico.
- **`<mark>`**: Destaca texto como se estivesse marcado com um marcador.
- **`<b>`** e **`<i>`**: Apenas estilização visual (negrito/itálico), sem significado semântico.

**Exemplo:**

```html
<p><strong>Atenção:</strong> Sempre salve seu trabalho!</p>
<p>É <em>fundamental</em> entender a diferença entre tags semânticas e visuais.</p>
<p>Use a tag <mark>HTML5</mark> para destacar termos importantes.</p>
```

> **Boas práticas:** Prefira `<strong>`, `<em>` e `<mark>` para significado. Use `<b>` e `<i>` apenas para estilização sem valor semântico.

-----

## 4\. Quebras de Linha, Linhas Horizontais e Espaçamento

- **`<br>`**: Quebra de linha. Use apenas em casos específicos, como endereços ou poesia.
- **`<hr>`**: Linha horizontal para separar blocos de conteúdo.
- **Espaçamento:** Evite múltiplos `<br>`. Prefira CSS para controlar espaçamentos.

**Exemplo:**

```html
<address>
    Softex Recife<br>
    Rua da Guia, 142<br>
    Recife - PE
</address>

<hr>

<p>Nova seção após a linha horizontal.</p>
```

-----

## 5\. Outras Tags Modernas e Úteis

- **`<code>`**: Para trechos de código.
- **`<pre>`**: Para blocos de texto pré-formatado.
- **`<time>`**: Para datas e horários.
- **`<blockquote>`**: Para citações longas.
- **`<small>`**: Para textos secundários ou observações.

**Exemplo:**

```html
<p>Veja o exemplo de código:</p>
<pre><code>console.log('Olá, mundo!');</code></pre>
<p>Publicado em <time datetime="2024-06-01">1 de junho de 2024</time></p>
```

-----

### Exemplo Completo de HTML Moderno

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Usando Elementos Modernos de HTML</title>
</head>
<body>
    <header>
        <h1>A História da Computação</h1>
        <nav>
            <a href="#primeiros">Primeiros Computadores</a> |
            <a href="#pessoais">Computadores Pessoais</a>
        </nav>
    </header>
    <main>
        <section id="primeiros">
            <h2>Os Primeiros Computadores</h2>
            <p>Nesta seção, exploramos as máquinas pioneiras...</p>
            <h3>O ENIAC</h3>
            <p>O ENIAC foi um dos primeiros computadores eletrônicos de grande escala...</p>
        </section>
        <hr>
        <section id="pessoais">
            <h2>A Revolução dos Computadores Pessoais</h2>
            <p>A década de 80 marcou a ascensão dos PCs...</p>
        </section>
    </main>
    <footer>
        <small>&copy; 2024 Seu Nome</small>
    </footer>
</body>
</html>
```

-----

## 🚀 Atividade Prática 02

**Objetivo:** Praticar a estruturação de um texto semântico usando títulos, parágrafos e tags modernas de HTML.

**Instruções:**

1. Crie um novo arquivo chamado `artigo.html` no seu Visual Studio Code.
2. Construa a estrutura essencial do HTML5 (`<!DOCTYPE>`, `<html>`, `<head>`, `<body>`, etc.).
3. No `<title>`, coloque "Artigo sobre Tecnologia".
4. Dentro do `<body>`, crie um artigo sobre um tema de tecnologia que você goste (Inteligência Artificial, Games, Segurança da Informação, etc.), utilizando:
    - Um título principal `<h1>`.
    - Pelo menos duas seções `<section>`, cada uma com um subtítulo `<h2>`.
    - Pelo menos dois parágrafos `<p>` em cada seção.
    - Em algum parágrafo, use `<strong>` para destacar uma informação importante.
    - Em outro parágrafo, use `<em>` para dar ênfase a uma palavra.
    - Use `<mark>` para destacar um termo relevante.
    - Use `<hr>` para separar as duas seções principais.
    - Utilize pelo menos uma tag semântica moderna, como `<article>`, `<aside>`, `<nav>`, `<header>`, `<footer>`, `<time>`, `<code>`, ou `<blockquote>`.
5. Salve o arquivo e abra-o no navegador para conferir se a estrutura está correta.
6. Envie o arquivo `artigo.html` na atividade "Tarefa" correspondente no Moodle.

> **Dica:** Explore as tags semânticas do HTML5 para deixar seu artigo mais moderno, acessível e bem estruturado!
