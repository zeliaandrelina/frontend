# 🔗 Conectando Páginas com Links e Organizando com Listas

Listas e links são essenciais para criar navegação eficiente e apresentar informações de forma clara em páginas web.

---

## 1. Listas em HTML

Listas agrupam itens relacionados, facilitando a leitura e a organização do conteúdo. Os três tipos principais são:

- **Lista Não-Ordenada (`<ul>`):** Use quando a ordem não importa.
- **Lista Ordenada (`<ol>`):** Use quando a sequência é importante.
- **Lista de Definição (`<dl>`):** Ideal para glossários ou pares nome-valor.

**Exemplo de cada tipo:**

```html
<!-- Não-ordenada -->
<ul>
    <li>Café</li>
    <li>Leite</li>
    <li>Pão</li>
</ul>

<!-- Ordenada -->
<ol>
    <li>Bata os ovos com o açúcar.</li>
    <li>Adicione a farinha e o leite.</li>
    <li>Leve ao forno por 40 minutos.</li>
</ol>

<!-- Definição -->
<dl>
    <dt>HTML</dt>
    <dd>Linguagem de marcação para estruturar páginas web.</dd>
    <dt>CSS</dt>
    <dd>Folhas de estilo para aparência das páginas.</dd>
</dl>
```

---

## 2. Links `<a>`

A tag `<a>` cria hiperlinks, conectando páginas ou seções. O atributo `href` define o destino do link. Para abrir em nova aba, use `target="_blank"`.

**Exemplos:**

```html
<!-- Link externo -->
<a href="https://www.google.com" target="_blank">Google</a>

<!-- Link interno -->
<a href="sobre.html">Sobre nós</a>

<!-- Link para seção da mesma página -->
<h2 id="contato">Contato</h2>
<a href="#contato">Ir para Contato</a>
```

---

## 🚀 Atividade

**Crie um perfil pessoal com listas e links:**

1. Crie `perfil.html` com estrutura básica HTML e `<title>Meu Perfil`.
2. No `<body>`:
     - `<h1>` com seu nome
     - `<h2>Meus Hobbies</h2>` + `<ul>` com 3 hobbies
     - `<h2>Top 3 Músicas</h2>` + `<ol>` com 3 músicas
     - `<h2>Links Úteis</h2>` + `<ul>` com 3 links (cada `<a>` com `target="_blank"`)
3. Teste no navegador e envie conforme instruções.

---

# 🖼️ Imagens e Tabelas

Podemos enriquecer nossas páginas com imagens e organizar dados usando tabelas.

---

## 1. Inserindo Imagens: `<img>`

A tag `<img>` insere imagens. Os atributos essenciais são:

- `src`: caminho da imagem (local ou URL)
- `alt`: texto alternativo para acessibilidade

**Exemplo:**

```html
<img src="imagens/ifpe-logo.png" alt="Logo do IFPE" width="200">
```

---

## 2. Estruturando Dados: Tabelas

Tabelas exibem dados em linhas e colunas. Use:

- `<table>`: envolve a tabela
- `<tr>`: linha
- `<th>`: cabeçalho
- `<td>`: célula de dados

**Exemplo básico:**

```html
<table>
    <thead>
        <tr>
            <th>Produto</th>
            <th>Preço</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Café</td>
            <td>R$ 9,50</td>
        </tr>
        <tr>
            <td>Leite</td>
            <td>R$ 4,70</td>
        </tr>
    </tbody>
</table>
```

Para mesclar células, use `colspan` (colunas) e `rowspan` (linhas):

```html
<td colspan="2">Desenvolvimento Web</td>
<td rowspan="2">Redes</td>
```

---

## 🚀 Atividade Prática 03

**Crie uma página com imagem e tabela de horários:**

1. Crie a pasta `semana-05`, com `horario.html` e uma subpasta `imagens`.
2. No `<body>`, adicione `<h1>Meu Horário de Aulas` e uma imagem relacionada a estudos.
3. Crie uma tabela com `<thead>` para os dias da semana e `<tbody>` para os horários e disciplinas.
4. Use `colspan` para representar aulas em dois horários seguidos.
5. Teste no navegador e envie conforme instruções.