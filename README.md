# Testes unitários com Jest

## O que são testes unitários?
Teste unitário é um método de teste de software que permite verificar se uma unidade isolada de código (por exemplo, uma função ou um método) está funcionando como o esperado. O objetivo é identificar problemas rapidamente e com eficiência, sem ter que testar todo o sistema. Testes unitários são normalmente escritos pelos desenvolvedores e executados automaticamente como parte do processo de build.

### Para trabalhar com testes unitários usando Jest, você precisa ter conhecimento básico em JavaScript e compreender os conceitos de testes unitários em geral. Além disso, você precisa saber:

1. Instalação e configuração do Jest em seu projeto.

2. Escrita de testes: Jest fornece vários métodos, como describe, it, test, expect, etc., para escrever e executar seus testes.

3. Asserções: você precisa saber como usar a biblioteca expect para fazer asserções sobre o resultado dos testes.

4. Mocks: Jest permite que você crie "mocks" para funções externas, o que é útil para testar funções isoladas sem depender de seus componentes externos.

5. Snapshots: Jest permite que você crie "snapshots" de seus componentes, que podem ser usados para testar se sua saída é consistente.

6. Execução de testes: você precisa saber como executar seus testes usando o Jest, incluindo como gerar relatórios e cobertura de código.

Em geral, a familiaridade com Jest e a prática de escrever testes irão ajudá-lo a se tornar proficiente em testes unitários com Jest.

### Os métodos mais comuns do Jest são:

1. `describe`: usado para agrupar testes relacionados em blocos lógicos. Cada describe pode conter vários it ou test para descrever comportamentos específicos.

2. `it`: usado para descrever um comportamento específico que você está testando. É equivalente ao test.

3. `test`: usado para descrever um comportamento específico que você está testando. É equivalente ao it.

4. `beforeEach` e `afterEach`: usados para executar código antes ou depois de cada teste. É útil para inicializar ou limpar dados antes ou depois de cada teste.

5. `expect`: usado para fazer asserções sobre o resultado dos testes. É a biblioteca central do Jest para verificar se seus testes estão passando ou falhando.

6. `jest.fn`: usado para criar mocks de funções. É útil para testar funções isoladas sem depender de seus componentes externos.

## Asserções
**Aqui estão alguns exemplos de asserções com Jest usando o método `expect`**:

Verificar se um valor é igual a um determinado valor:
```javascript
test('should return the correct value', () => {
  const result = 2 + 2;
  expect(result).toBe(4);
});
```

Verificar se um valor é verdadeiro:
```javascript
test('should return true', () => {
  const result = true;
  expect(result).toBeTruthy();
});
```

Verificar se um valor é falso:
```javascript
test('should return false', () => {
  const result = false;
  expect(result).toBeFalsy();
});
```

Verificar se um valor é null:
```javascript
test('should return null', () => {
  const result = null;
  expect(result).toBeNull();
});
```

Verificar se um valor é undefined:
```javascript
test('should return undefined', () => {
  let result;
  expect(result).toBeUndefined();
});
```

Verificar se um valor é um determinado tipo:
```javascript
test('should return a string', () => {
  const result = 'hello, world';
  expect(typeof result).toBe('string');
});
```

**Estes são apenas alguns exemplos básicos de asserções com Jest. Existem muitos outros métodos expect disponíveis, incluindo comparações de objetos, arrays e expressões regulares.**

## Mocks

Mocks são versões simuladas de objetos, funções ou módulos que você pode usar em seus testes para controlar e prever o comportamento de seu código. Em vez de depender de componentes externos, você pode criar mocks para substituir esses componentes durante os testes.

Aqui está um exemplo de como você pode escrever um mock de uma função usando o Jest:

```javascript
test('should call the mock function', () => {
  const mockFunction = jest.fn();
  mockFunction();
  expect(mockFunction).toHaveBeenCalled();
});
```

Neste exemplo, estamos criando uma função mock usando jest.fn() e chamando essa função. Em seguida, usamos expect para verificar se a função mock foi realmente chamada.

Você também pode configurar a função mock para retornar um valor específico quando chamada:

```javascript
test('should call the mock function with the correct arguments', () => {
  const mockFunction = jest.fn();
  mockFunction.mockReturnValueOnce(42);
  const result = mockFunction();
  expect(result).toBe(42);
  expect(mockFunction).toHaveBeenCalled();
});
```

Neste exemplo, estamos configurando a função mock para retornar o valor 42 quando chamada pela primeira vez. Verificamos se o resultado da chamada à função mock é o esperado e se a função mock foi realmente chamada.

