# Introdução a JavaScript e Lógica de Programação

A linguagem JavaScript começou como um script de 10 dias para fazer botões piscarem em navegadores e agora... bem, agora ela domina o mundo. Do seu celular à sua geladeira, o JS está lá, silenciosamente julgando suas escolhas de lanches.

Prepare-se para uma jornada divertida através de lógica, esquisitices e um poder imenso. Vamos decifrar essa códigos juntos!

---

## 1. O que é JavaScript
JavaScript é a linguagem padrão para lógica em páginas web, também usada em backend (Node.js), mobile, desktop e IoT. Multiparadigma: suporta programação imperativa, funcional e orientada a objetos. Hoje se escreve JS moderno (ES6+), evitando `var` e usando módulos, funções puras e padrões reusáveis.

## 2. Ambiente rápido
Browser (Console DevTools) ou Node.js:  
```bash
node
```
Digite código e teste imediatamente.

---

## 3. Tipos de Dados (Primitivos e Referência)

### 3.1 Primitivos
- string
- number (inteiro e ponto flutuante)
- bigint
- boolean
- null (ausência intencional)
- undefined (não definido)
- symbol (identificador único)

Exemplos:
```js
const nome = "Ana";          // string
const idade = 28;            // number
const saldo = 1234.75;       // number
const grande = 9007199254740993n; // bigint
const ativo = true;          // boolean
const nada = null;           // null
let naoDefinido;             // undefined
const chave = Symbol("id");  // symbol
```

### 3.2 Objetos (referência)
Arrays, funções, datas e objetos literais:
```js
const pessoa = { nome: "Ana", idade: 28 };
const numeros = [1, 2, 3];
function somar(a, b) { return a + b; }
```
Objetos são mutáveis por referência:
```js
const a = { x: 1 };
const b = a;
b.x = 99;
console.log(a.x); // 99 (mesmo objeto)
```

### 3.3 Checando tipos
```js
typeof 10;              // "number"
typeof null;            // "object" (peculiaridade histórica)
Array.isArray([]);      // true
```

---

## 4. Conversões
Explícitas:
```js
Number("42");    // 42
String(10);      // "10"
Boolean("");     // false
Boolean("ok");   // true
```
Curto-circuito e coalescência:
```js
const porta = process.env.PORT || 3000;     // usa 3000 se valor "falsy"
const porta2 = process.env.PORT ?? 3000;    // usa 3000 só se null/undefined
```

---

## 5. Operadores

### 5.1 Aritméticos
`+ - * / % **`
```js
2 ** 3; // 8 potenciação
```

### 5.2 Atribuição
`= += -= *= /= ??= ||= &&=`
```js
let x = 0;
x += 5;    // 5
x ||= 10;  // se falsy vira 10 (não muda porque 5 é truthy)
```

### 5.3 Comparação
`==` (coerção) evite. Use `===`.
```js
0 == false;  // true (indesejado)
0 === false; // false
```

### 5.4 Lógicos
`&&` (e), `||` (ou), `!` (nega)
Atalhos modernos:
```js
const user = { perfil: { nome: "Ana" } };
const nome = user?.perfil?.nome;      // optional chaining
const idade = user?.idade ?? 0;       // nullish coalescing
```

### 5.5 Desestruturação / Spread / Rest
```js
const livro = { titulo: "JS", ano: 2024 };
const { titulo, ano: publicado } = livro; // renomeando
const cores = ["azul", "verde", "vermelho"];
const [primeira, , terceira] = cores;

const base = { a: 1, b: 2 };
const extra = { b: 9, c: 3 };
const combinado = { ...base, ...extra }; // { a:1, b:9, c:3 }

function somaTudo(...nums) {
    return nums.reduce((acc, n) => acc + n, 0);
}
somaTudo(1,2,3); // 6
```

---

## 6. Estruturas de Controle

### 6.1 if / else
```js
const nota = 85;
if (nota >= 90) {
    console.log("A");
} else if (nota >= 80) {
    console.log("B");
} else {
    console.log("C");
}
```

### 6.2 switch
```js
const role = "admin";
switch (role) {
    case "admin":
        console.log("Acesso total");
        break;
    case "user":
        console.log("Acesso limitado");
        break;
    default:
        console.log("Nenhum");
}
```

### 6.3 Loop for / while
```js
for (let i = 0; i < 3; i++) {
    console.log(i);
}

let c = 0;
while (c < 3) {
    console.log(c);
    c++;
}
```

### 6.4 for...of / for...in
```js
for (const cor of ["azul","verde"]) {
    console.log(cor); // valores
}

const obj = { a:1, b:2 };
for (const k in obj) {
    console.log(k, obj[k]); // chaves
}
```

### 6.5 Iteração funcional (preferida)
```js
[1,2,3].forEach(n => console.log(n));
const dobrados = [1,2,3].map(n => n * 2);       // [2,4,6]
const pares = [1,2,3,4].filter(n => n % 2 === 0); // [2,4]
const soma = [1,2,3].reduce((acc,n)=>acc+n,0);  // 6
```

---

## 7. Funções

### 7.1 Declaração vs Expressão
```js
function soma(a,b){ return a+b; }         // hoisted
const mult = function(a,b){ return a*b; } // expressão
```

### 7.2 Arrow Functions
Sintaxe curta, não liga this próprio.
```js
const quadrado = n => n * n;
const somaLista = (a, b, ...rest) => rest.reduce((acc,n)=>acc+n, a+b);
```

### 7.3 Parâmetro padrão
```js
function conectar(host="localhost", porta=5432) {
    console.log(host, porta);
}
```

### 7.4 Funções puras e imutabilidade
```js
const adicionarUsuario = (lista, usuario) =>
    [...lista, { ...usuario }]; // não muta a original
```

---

## 8. Escopo

- Escopo de bloco: `let`, `const`
- Escopo de função: parâmetros e variáveis internas
- Global: evitar poluição

```js
let xGlobal = 10;
{
    const interno = 5;
    let outro = 7;
    // interno e outro existem só aqui
}
// acessar interno => erro
```

`var` ignora bloco (exceto função) — evite.

---

## 9. Closures

Closure é a função que lembra o ambiente léxico onde foi criada.

```js
function contador(inicial = 0) {
    let valor = inicial;
    return function proximo() {
        valor++;
        return valor;
    };
}
const c1 = contador(10);
c1(); // 11
c1(); // 12
const c2 = contador(); 
c2(); // 1 (independente)
```
Explicação: `proximo` mantém acesso à variável `valor` mesmo após `contador` terminar.

Outro exemplo prático (cache):
```js
function memoizar(fn) {
    const cache = new Map();
    return arg => {
        if (cache.has(arg)) return cache.get(arg);
        const r = fn(arg);
        cache.set(arg, r);
        return r;
    };
}
const lento = n => {
    console.log("computando...");
    return n * 2;
};
const rapido = memoizar(lento);
rapido(5); // computando... 10
rapido(5); // 10 (cache, sem log)
```

---

## 10. Módulos (ES Modules)
Arquivo math.js:
```js
export function soma(a,b){ return a+b; }
export const PI = 3.14159;
export default function dobro(n){ return n*2; }
```
Arquivo uso.js:
```js
import dobro, { soma, PI } from "./math.js";
console.log(dobro(4), soma(2,3), PI);
```

---

## 11. Promises e Assíncrono

### 11.1 Promise
```js
function esperar(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}
esperar(500).then(()=> console.log("Ok"));
```

### 11.2 async/await
```js
async function fluxo() {
    console.log("Início");
    await esperar(300);
    console.log("Depois");
}
fluxo();
```

### 11.3 fetch (browser / node >=18)
```js
async function carregarUsuario(id) {
    const resp = await fetch(`https://jsonplaceholder.typicode.com/users/${id}`);
    if (!resp.ok) throw new Error("Falha HTTP");
    const dados = await resp.json();
    return dados;
}
carregarUsuario(1)
    .then(u => console.log(u.name))
    .catch(e => console.error(e.message));
```

Parallel:
```js
const ids = [1,2,3];
const promessas = ids.map(id => carregarUsuario(id));
const resultados = await Promise.all(promessas);
```

---

## 12. Manipulação de Arrays moderna
```js
const users = [
    { id:1, ativo:true, nome:"Ana" },
    { id:2, ativo:false, nome:"Bruno" },
    { id:3, ativo:true, nome:"Carla" },
];

// achar
users.find(u => u.id === 2); // { id:2, ... }

// transformar
const nomesAtivos = users
    .filter(u => u.ativo)
    .map(u => u.nome.toUpperCase());

// agrupar (reduce)
const porAtivo = users.reduce((acc,u)=>{
    const chave = u.ativo ? "ativos" : "inativos";
    acc[chave].push(u);
    return acc;
}, { ativos:[], inativos:[] });
```

---

## 13. Imutabilidade em Objetos
```js
const estado = { usuario: { nome:"Ana", pontos:10 } };
const novoEstado = {
    ...estado,
    usuario: { ...estado.usuario, pontos: estado.usuario.pontos + 5 }
};
```

---

## 14. Tratamento de Erros
```js
function dividir(a,b){
    if (b === 0) throw new Error("Divisão por zero");
    return a / b;
}
try {
    dividir(4,0);
} catch(e) {
    console.error("Erro:", e.message);
} finally {
    console.log("Sempre executa");
}
```

---

## 15. Boas Práticas Modernas
- Usar const por padrão; let se reatribuir; evitar var.
- Funções pequenas e puras.
- Nomear claramente.
- Preferir métodos de array a loops manuais quando legível.
- Tratar erros em async/await com try/catch ou Promise.allSettled.
- Evitar mutações compartilhadas.
- Documentar intenção (comentários curtos, código claro).

---

## 16. Mini Projeto Integrado

Objetivo: Carregar usuários ativos, normalizar e exibir.

```js
async function fetchUsuarios() {
    const r = await fetch("https://jsonplaceholder.typicode.com/users");
    if (!r.ok) throw new Error("Falha ao buscar");
    return r.json();
}

function normalizar(users) {
    return users.map(u => ({
        id: u.id,
        nome: u.name,
        email: u.email.toLowerCase(),
        cidade: u.address?.city
    }));
}

function filtrarPorNome(users, termo) {
    const t = termo.toLowerCase();
    return users.filter(u => u.nome.toLowerCase().includes(t));
}

async function main() {
    try {
        const brutos = await fetchUsuarios();
        const norm = normalizar(brutos);
        const filtrados = filtrarPorNome(norm, "Lea");
        console.log(filtrados);
    } catch(e) {
        console.error("Erro no fluxo:", e.message);
    }
}

main();
```
Explicação rápida:
- fetchUsuarios: busca e retorna JSON.
- normalizar: cria um novo array transformado (não muta original).
- filtrarPorNome: reutilizável.
- main: orquestra com async/await e trata erros.

---

## 17. Próximos Passos
- DOM e eventos
- Testes (Jest / Vitest)
- Bundlers (Vite / Webpack)
- TypeScript
- Performance e profiling

Resumo: Você viu bases sólidas: tipos, operadores, controle, funções, escopo, closures, módulos e assíncrono. Pratique escrevendo pequenos utilitários e testando tudo no console.