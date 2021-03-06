# Tipo de dado: Tupla

Os tipos de ***tupla*** permitem expressar um array com um número fixo de elementos cujos tipos são conhecidos, mas não precisam ser os mesmos. Por exemplo, você pode querer representar um valor como um par de uma string e um número:

```typescript
// Declare um tipo de tupla
let x: [string, number];

// Inicialize
x = ["hello", 10]; // OK

// Inicialize incorretamente
x = [10, "hello"]; // Error
```

> O tipo 'number' não pode ser atribuído ao tipo 'string'.

> O tipo 'string' não pode ser atribuído ao tipo 'number'.

Ao acessar um elemento com um índice conhecido, o tipo correto é recuperado:

```typescript
// OK
console.log(x[0].substring(1));

console.log(x[1].substring(1));
```
> A propriedade 'substring' não existe no tipo 'number'.

Acessar um elemento fora do conjunto de índices conhecidos falha com um erro:

```typescript
x[3] = "world";
```
> O tipo de tupla '[string, number]' de comprimento '2' não tem nenhum elemento no índice '3'.

```typescript
console.log(x[5].toString());
```

> O objeto está possivelmente 'undefined'.

> O tipo de tupla '[string, number]' de comprimento '2' não tem nenhum elemento no índice '5'.

## Desestruturação de tupla

As tuplas podem ser desestruturadas como matrizes; as variáveis de desestruturação obtêm os tipos dos elementos de tupla correspondentes:

```typescript
let tuple: [number, string, boolean] = [7, "hello", true];

let [a, b, c] = tuple; // a: number, b: string, c: boolean
```

É um erro desestruturar uma tupla além do intervalo de seus elementos:

```typescript
let [a, b, c, d] = tuple; // Erro, nenhum elemento no índice 3
```

Tal como acontece com arrays, você pode desestruturar o resto da tupla com `...`, para obter uma tupla mais curta:

```typescript
let [a, ...bc] = tuple; // bc: [string, boolean]
let [a, b, c, ...d] = tuple; // d: [], a tupla vazia
```

Ou ignore os elementos finais ou outros elementos:

```typescript
let [a] = tuple; // a: number
let [, b] = tuple; // b: string
```