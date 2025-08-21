# Formulários e Interatividade

Formulários são ferramentas essenciais para coletar informações dos usuários e enviá-las ao servidor. Vamos aprender a montar um formulário funcional e acessível.

## Estrutura de Formulários

Os principais elementos de um formulário HTML são:

```html
<form>
    <input type="text" name="nome" placeholder="Digite seu nome">
    <textarea name="mensagem" placeholder="Sua mensagem"></textarea>
    <select name="opcao">
        <option value="1">Opção 1</option>
        <option value="2">Opção 2</option>
    </select>
    <button type="submit">Enviar</button>
</form>
```

### Elementos

- `<form>`: Container principal do formulário.
- `<input>`: Campo para entrada de dados simples.
- `<textarea>`: Campo para textos mais longos.
- `<select>`: Lista suspensa para seleção de opções.
- `<button>`: Botão para enviar o formulário.

## Tipos de Input

O `<input>` pode assumir diferentes tipos, conforme a necessidade:

| Tipo      | Descrição                        |
|-----------|----------------------------------|
| text      | Texto simples                    |
| email     | E-mail (com validação automática)|
| password  | Senha (entrada oculta)           |
| checkbox  | Caixa de seleção                 |
| radio     | Botão de opção (seleção única)   |

Exemplo:

```html
<input type="text" name="usuario">
<input type="email" name="email">
<input type="password" name="senha">
<input type="checkbox" name="newsletter"> Receber novidades
<input type="radio" name="genero" value="masculino"> Masculino
<input type="radio" name="genero" value="feminino"> Feminino
```

## Atributos Importantes

- `required`: Campo obrigatório.
- `placeholder`: Texto de orientação dentro do campo.
- `value`: Valor inicial do campo.
- `name`: Identificador do campo no envio dos dados.

Exemplo:

```html
<input type="email" name="contato" required placeholder="Seu e-mail">
```

## Boas Práticas de Acessibilidade

- Utilize sempre o `<label>` para identificar campos.
- Forneça descrições claras e objetivas.
- Use `aria-label` quando necessário para leitores de tela.
- Garanta que todos os campos possam ser acessados via teclado.

Exemplo:

```html
<label for="nome">Nome:</label>
<input type="text" id="nome" name="nome" required>
```

## 🚀 Atividade Prática 04

Crie um formulário de cadastro com os seguintes campos:

- Nome (texto, obrigatório)
- E-mail (email, obrigatório)
- Senha (password, obrigatório)
- Gênero (radio: Masculino, Feminino, Outro)
- Aceitar termos (checkbox, obrigatório)

Aplique as práticas de acessibilidade e utilize os atributos apresentados. Um bom formulário é claro, acessível e fácil de usar.