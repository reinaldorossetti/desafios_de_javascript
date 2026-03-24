# Resumo de JavaScript

Este é um resumo completo e estruturado de JavaScript, organizado como um guia prático para consulta rápida e estudo. O conteúdo abaixo reúne os tópicos principais e também adiciona novos pontos importantes, como herança entre classes e interface.

## 1. Fundamentos básicos e tipos de dados

O JavaScript moderno utiliza `let` para valores mutáveis e `const` para valores fixos. Ele suporta diversos tipos de dados, agrupando informações em objetos e listas (`arrays`).

```javascript
// Variáveis e tipos
const nome = "Reinaldo"; // String
let idade = 30; // Number
const ativo = true; // Boolean

// Objeto (agrupa propriedades)
const usuario = { nome: "Reinaldo", papel: "Desenvolvedor" };

// Array (lista de itens)
const tecnologias = ["HTML", "CSS", "JS"];

// Função (Arrow Function)
const saudar = (nomeUsuario) => `Olá, ${nomeUsuario}!`;
```

### Tipos mais comuns

- `string` — texto
- `number` — números inteiros ou decimais
- `boolean` — `true` ou `false`
- `null` — valor nulo intencional
- `undefined` — valor não definido
- `object` — objetos e estruturas compostas
- `array` — listas de elementos
- `function` — blocos de código reutilizáveis

## 2. Diferença entre `var`, `let` e `const`

A principal diferença é o escopo.

- `var` tem escopo de função ou escopo global, podendo “vazar” de blocos lógicos.
- `let` e `const` têm escopo de bloco, existindo apenas dentro das chaves `{}` onde foram criados.

```javascript
// Problema do var (vazamento de escopo)
if (true) {
  var nomeVar = "João";
}
console.log(nomeVar); // Imprime "João" fora do bloco

// Segurança do let (escopo de bloco)
if (true) {
  let nomeLet = "Maria";
}
// console.log(nomeLet); // ERRO: nomeLet is not defined
```

### Boas práticas

- Prefira `const` sempre que possível.
- Use `let` apenas quando o valor precisar mudar.
- Evite `var` em código moderno.

## 3. Operadores e comparações

JavaScript oferece operadores aritméticos, lógicos e de comparação.

```javascript
const a = 10;
const b = 5;

console.log(a + b); // 15
console.log(a - b); // 5
console.log(a * b); // 50
console.log(a / b); // 2
console.log(a % b); // 0

console.log(a > b); // true
console.log(a === b); // false
console.log(a !== b); // true
```

### Igualdade `==` vs `===`

- `==` converte tipos antes de comparar.
- `===` compara valor e o tipo.
- Use sempre `===` para evitar surpresas.

```javascript
console.log(0 == false);  // true
console.log(0 === false); // false
```

## 4. Estruturas de controle e repetição

Essas estruturas são usadas para tomada de decisões e execução de tarefas repetitivas.

```javascript
const notas = [7.5, 5.5, 9.0];

for (let i = 0; i < notas.length; i++) {
  if (notas[i] >= 7.0) {
    console.log(`Nota ${notas[i]}: Aprovado`);
  } else {
    console.log(`Nota ${notas[i]}: Reprovado`);
  }
}
```

### Estruturas comuns

- `if / else`
- `switch`
- `for`
- `while`
- `do...while`
- `for...of`
- `for...in`

## 5. Funções

Funções permitem reutilizar lógica e organizar melhor o código.

```javascript
function somar(x, y) {
  return x + y;
}

const multiplicar = (x, y) => x * y;

console.log(somar(2, 3)); // 5
console.log(multiplicar(2, 3)); // 6
```

### Conceitos importantes

- Parâmetros e argumentos
- `return`
- Funções tradicionais
- Arrow functions
- Funções anônimas

## 6. Objetos e manipulação de propriedades

Objetos armazenam dados em formato de chave e valor.

```javascript
const usuario = {
  nome: "Reinaldo",
  papel: "Desenvolvedor",
  ativo: true,
};

console.log(usuario.nome);
usuario.idade = 30;
```

### Recursos úteis

- Acessar propriedades com ponto ou colchetes
- Destructuring
- Spread e rest operator
- `Object.keys()`, `Object.values()`, `Object.entries()`

## 7. Arrays e manipulação de listas

O JavaScript moderno utiliza métodos funcionais para transformar dados de forma limpa, substituindo laços `for` complexos quando apropriado.

```javascript
const carrinho = [
  { produto: "Notebook", preco: 4500, ativo: true },
  { produto: "Mouse", preco: 150, ativo: false },
  { produto: "Teclado", preco: 300, ativo: true },
];

// Encadeamento de métodos: filtra, aplica desconto e soma
const total = carrinho
  .filter((item) => item.ativo)
  .map((item) => item.preco * 0.9)
  .reduce((acc, preco) => acc + preco, 0);

console.log(`Total: R$ ${total}`); // R$ 4320
```

### Entendendo o `reduce`

O `reduce` serve para transformar uma lista em um único valor. No exemplo acima, ele soma todos os preços já com desconto.

- `acc` significa **acumulador**: ele guarda o valor parcial da soma.
- `preco` é o valor atual do item que está sendo processado.
- `0` é o valor inicial do acumulador.

Funciona assim:

1. Começa com `acc = 0`.
2. Soma o primeiro `preco`.
3. Guarda o resultado em `acc`.
4. Repete o processo até percorrer todo o array.

Exemplo simples:

```javascript
const numeros = [10, 20, 30];

const soma = numeros.reduce((acc, numero) => acc + numero, 0);

console.log(soma); // 60
```

Se quiser pensar de forma prática, o `reduce` é ótimo para:

- somar valores
- contar itens
- agrupar dados
- montar objetos a partir de arrays

### Métodos mais usados

- `push`, `pop`, `shift`, `unshift`
- `slice`, `splice`
- `map`, `filter`, `reduce`
- `find`, `some`, `every`
- `includes`, `indexOf`

## 8. Classes e orientação a objetos

As classes facilitam a criação de objetos com propriedades e métodos, organizando o código de forma estruturada.

```javascript
class Usuario {
  constructor(nome, email) {
    this.nome = nome;
    this.email = email;
  }

  fazerLogin() {
    console.log(`${this.nome} logou com ${this.email}.`);
  }
}

const usuario1 = new Usuario("Reinaldo", "reinaldo@email.com");
usuario1.fazerLogin();
```

### Herança: classe mãe e classe filha

Em JavaScript, uma classe filha pode herdar comportamentos de uma classe mãe usando `extends` e `super()`.

```javascript
class Pessoa {
  constructor(nome) {
    this.nome = nome;
  }

  apresentar() {
    console.log(`Olá, meu nome é ${this.nome}.`);
  }
}

class Aluno extends Pessoa {
  constructor(nome, curso) {
    super(nome);
    this.curso = curso;
  }

  estudar() {
    console.log(`${this.nome} está estudando ${this.curso}.`);
  }
}

const aluno1 = new Aluno("Maria", "JavaScript");
aluno1.apresentar();
aluno1.estudar();
```

### Conceitos de OOP

- Classe mãe: base reutilizável
- Classe filha: especialização da classe base
- `constructor`
- `this`
- `extends`
- `super()`
- Encapsulamento
- Polimorfismo

## 9. Interface

O JavaScript puro não possui `interface` nativa como o TypeScript, mas o conceito de interface é importante para definir contratos de estrutura.

### Em TypeScript

```typescript
interface Usuario {
  nome: string;
  email: string;
  ativo: boolean;
}

const usuario2: Usuario = {
  nome: "Reinaldo",
  email: "reinaldo@email.com",
  ativo: true,
};
```

### Em JavaScript, o equivalente conceitual

- Padronizar objetos com a mesma estrutura
- Validar propriedades esperadas
- Documentar contratos com JSDoc

```javascript
/**
 * @typedef {Object} Usuario
 * @property {string} nome
 * @property {string} email
 * @property {boolean} ativo
 */

/** @type {Usuario} */
const usuario3 = {
  nome: "Carlos",
  email: "carlos@email.com",
  ativo: true,
};
```

## 10. Assincronismo: Promise, async e await

Usado para operações que demoram, como buscar dados em uma API, sem travar o restante do código.

```javascript
const buscarDados = async (id) => {
  try {
    // Simula espera de 2 segundos por uma resposta
    const resposta = await new Promise((resolve) => {
      setTimeout(() => resolve({ id, status: "OK" }), 2000);
    });
    console.log("Dados:", resposta);
  } catch (erro) {
    console.error("Erro:", erro);
  }
};

buscarDados(1);
```

### Quando usar

- Requisições HTTP
- Leitura de arquivos
- Operações com banco de dados
- Qualquer tarefa que leve tempo para concluir

## 11. Conversão de tipos (type coercion)

O JavaScript tenta converter tipos automaticamente, o que pode gerar resultados inesperados. É recomendado usar conversão explícita quando possível.

```javascript
// Implícita (o JS tenta adivinhar)
console.log("5" + 2); // "52" (concatena como texto)
console.log("5" - 2); // 3 (converte para número e subtrai)

// Explícita (recomendado)
const numero = Number("10");
const texto = String(10);
```

### Conversões úteis

- `Number()`
- `String()`
- `Boolean()`
- `parseInt()`
- `parseFloat()`

## 12. Erros comuns e armadilhas

Conhecer esses detalhes evita horas de depuração no código.

### Acesso a propriedade indefinida

Tentar ler algo que não existe pode quebrar o código. Use o *Optional Chaining* (`?.`).

```javascript
const cliente = { nome: "Reinaldo" };

// console.log(cliente.endereco.rua); // ERRO FATAL
console.log(cliente.endereco?.rua); // Retorna undefined de forma segura
```

### Outros cuidados comuns

- `null` e `undefined`
- Números `NaN`
- Acesso a índices inexistentes em arrays
- Variáveis não declaradas
- Mistura de tipos sem conversão adequada

## 13. Recursos modernos do JavaScript

Além dos fundamentos, vale conhecer recursos modernos que deixam o código mais limpo.

```javascript
const pessoa = {
  nome: "Ana",
  idade: 28,
  cidade: "São Paulo",
};

// Destructuring
const { nome, idade } = pessoa;

// Spread
const pessoaAtualizada = { ...pessoa, idade: 29 };

// Rest
const somarTudo = (...numeros) => numeros.reduce((acc, n) => acc + n, 0);
```

### Também vale estudar

- Template literals
- Modules (`import` / `export`)
- `localStorage` e `sessionStorage`
- DOM e eventos
- Fetch API

## 14. Boas práticas de codificação em JavaScript

Escrever JavaScript de forma consistente ajuda a manter o código mais legível, fácil de manter e menos sujeito a erros. A ideia aqui é mostrar melhorias reais de código: o que costuma aparecer em projetos pequenos e como transformar isso em algo mais organizado, previsível e fácil de evoluir.

### Princípios recomendados

- Use nomes claros e descritivos para variáveis, funções e classes.
- Prefira `const` e use `let` apenas quando houver reatribuição.
- Evite `var` em código moderno.
- Mantenha funções pequenas e com responsabilidade única.
- Reaproveite código com funções e módulos.
- Use `===` no lugar de `==` sempre que possível.
- Valide dados de entrada antes de processar.
- Evite efeitos colaterais desnecessários.
- Prefira métodos de array como `map`, `filter` e `reduce` quando fizer sentido.
- Trate erros com `try...catch` quando houver risco de falha.

### Antes e depois: nomes mais claros

```javascript
// Antes
const x = "Reinaldo";
const y = 30;

// Depois
const nomeUsuario = "Reinaldo";
const idadeUsuario = 30;
```

Quando o nome da variável explica o que ela representa, o código fica mais fácil de entender sem depender de comentários extras.

### Antes e depois: função com responsabilidade única

```javascript
// Antes
function p(dados) {
  console.log(`Olá, ${dados.nome}!`);
  console.log(`Seu pedido totalizou R$ ${dados.total}.`);
  return dados.total * 0.9;
}

// Depois
function mostrarMensagemBoasVindas(nome) {
  console.log(`Olá, ${nome}!`);
}

function mostrarResumoPedido(total) {
  console.log(`Seu pedido totalizou R$ ${total}.`);
}

function calcularTotalComDesconto(total) {
  return total * 0.9;
}

mostrarMensagemBoasVindas("Reinaldo");
mostrarResumoPedido(100);
console.log(calcularTotalComDesconto(100));
```

Separar responsabilidades evita funções gigantes e melhora a reutilização.

### Antes e depois: melhorando arrays

```javascript
// Antes
const precos = [100, 200, 300];
const comDesconto = [];

for (let i = 0; i < precos.length; i++) {
  comDesconto.push(precos[i] * 0.9);
}

let soma = 0;
for (let i = 0; i < comDesconto.length; i++) {
  soma += comDesconto[i];
}

// Depois
const totalComDesconto = precos
  .map((preco) => preco * 0.9)
  .reduce((acc, preco) => acc + preco, 0);

console.log(totalComDesconto);
```

No segundo exemplo, o fluxo fica mais direto: transformar os valores e depois somar.

### Antes e depois: condição mais legível

```javascript
// Antes
if (usuario.ativo === true && usuario.email !== "" && usuario.email !== null) {
  console.log("Usuário válido");
}

// Depois
const emailValido = usuario.email?.trim() !== "";

if (usuario.ativo && emailValido) {
  console.log("Usuário válido");
}
```

Quando a condição começa a ficar grande, vale extrair partes em variáveis com nome semântico.

### Antes e depois: tratamento de erro

```javascript
// Antes
const buscarUsuario = async () => {
  const resposta = await fetch("/api/usuario");
  const dados = await resposta.json();
  return dados;
};

// Depois
const buscarUsuario = async () => {
  try {
    const resposta = await fetch("/api/usuario");

    if (!resposta.ok) {
      throw new Error("Falha ao buscar usuário");
    }

    return await resposta.json();
  } catch (erro) {
    console.error("Erro ao buscar usuário:", erro);
    return null;
  }
};
```

Tratar erros evita que a aplicação quebre sem aviso e facilita a depuração.

### Exemplo de código mais limpo

```javascript
const calcularDesconto = (preco, percentual) => {
  if (preco <= 0 || percentual <= 0) {
    return 0;
  }

  return preco - (preco * percentual) / 100;
};

const valorFinal = calcularDesconto(100, 10);
console.log(valorFinal); // 90
```

### Dicas extras

- Use indentação consistente.
- Separe bem lógica de negócio, interface e manipulação de dados.
- Comente apenas o que realmente agrega contexto.
- Revise código pensando em manutenção futura.
- Evite abreviações que só fazem sentido no momento da escrita.
- Padronize o estilo do projeto para que o time escreva do mesmo jeito.

## 15. Resumo final

Este material serve como uma excelente folha de dicas (*cheat sheet*) para consultas rápidas. Ele cobre os conceitos mais usados em JavaScript, desde variáveis e funções até arrays, classes, herança, interface e assincronismo.

Se quiser, o próximo passo pode ser transformar este resumo em uma versão ainda mais visual, com tabelas, exemplos práticos ou um mini guia para estudo diário.