# Introdução ao HTML

HTML (HyperText Markup Language) é a linguagem base da web. Ele permite estruturar o conteúdo das páginas, como textos, imagens, links e listas, organizando as informações de forma que os navegadores possam exibi-las corretamente para os usuários.

## Estrutura básica de um documento HTML

Todo arquivo HTML segue uma estrutura padrão:

```html
<!DOCTYPE html>
<html lang="pt-BR">
    <head>
        <meta charset="UTF-8">
        <title>Título da Página</title>
    </head>
    <body>
        <!-- Conteúdo visível da página -->
    </body>
</html>
```

- `<!DOCTYPE html>`: Indica que o documento está usando HTML5.
- `<html>`: Elemento raiz do documento.
- `<head>`: Contém informações sobre a página (metadados), como título, codificação de caracteres e links para arquivos externos (CSS, scripts).
- `<body>`: Onde fica o conteúdo que será exibido ao usuário, como textos, imagens, links, listas, tabelas, etc.

## Principais elementos HTML

### Títulos e parágrafos

```html
<h1>Título Principal</h1>
<h2>Subtítulo</h2>
<p>Este é um parágrafo de texto.</p>
```

- `<h1>` até `<h6>`: Definem títulos, do mais importante (`h1`) ao menos importante (`h6`).
- `<p>`: Define um parágrafo.

### Links e imagens

```html
<a href="https://www.exemplo.com">Visite o site</a>
<img src="imagem.jpg" alt="Descrição da imagem">
```

- `<a>`: Cria um link. O atributo `href` define o destino.
- `<img>`: Exibe uma imagem. O atributo `src` indica o caminho da imagem e `alt` fornece um texto alternativo.

### Listas

```html
<ul>
    <li>Item de lista não ordenada</li>
    <li>Outro item</li>
</ul>
<ol>
    <li>Primeiro item de lista ordenada</li>
    <li>Segundo item</li>
</ol>
```

- `<ul>`: Lista não ordenada (com marcadores).
- `<ol>`: Lista ordenada (numerada).
- `<li>`: Item da lista.

### Tabelas

```html
<table>
    <tr>
        <th>Nome</th>
        <th>Idade</th>
    </tr>
    <tr>
        <td>Ana</td>
        <td>25</td>
    </tr>
    <tr>
        <td>João</td>
        <td>30</td>
    </tr>
</table>
```

- `<table>`: Cria uma tabela.
- `<tr>`: Linha da tabela.
- `<th>`: Cabeçalho da tabela.
- `<td>`: Célula de dados.

## Dicas importantes

- Sempre feche as tags corretamente.
- Use indentação para facilitar a leitura do código.
- Utilize o atributo `alt` em imagens para acessibilidade.
- O conteúdo dentro do `<head>` não aparece na página, mas é importante para SEO e funcionamento