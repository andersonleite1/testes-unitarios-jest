# Testes unitários com Jest

**Vamos direto ao ponto**
1. [O que são testes unitários](#o-que-são-testes-unitários)
2. [Conceitos](#conceitos)
3. [O que preciso saber](#o-que-preciso-saber)
4. [Os métodos mais comuns](#os-métodos-mais-comuns)
5. [Asserções](#asserções)
6. [Mocks](#mocks)
7. [Snapshots](#snapshots)
8. [Execução](#execução)
9. [Referências](#referências)

## O que são testes unitários?
Teste unitário é um método de teste de software que permite verificar se uma unidade isolada de código (por exemplo, uma função ou um método) está funcionando como o esperado. O objetivo é identificar problemas rapidamente e com eficiência, sem ter que testar todo o sistema. Testes unitários são normalmente escritos pelos desenvolvedores e executados automaticamente como parte do processo de build.

## Conceitos

Os conceitos de teste unitário incluem:

1. **Isolamento**: Cada teste unitário deve ser isolado e não depender de outros recursos ou dependências externas. Isso garante que os resultados dos testes sejam confiáveis e não sejam afetados por mudanças em outras partes do sistema.

2. **Automatização**: Os testes unitários devem ser automatizados para garantir que possam ser executados rapidamente e com precisão.

3. **Cobertura de código**: A cobertura de código é a medida da quantidade de código que é executada durante a execução dos testes. É importante ter uma cobertura de código adequada para garantir que todas as partes do código sejam testadas e que todos os erros possíveis sejam detectados.

4. **Feedback rápido**: Os testes unitários devem fornecer feedback rápido sobre a qualidade do código, permitindo que os desenvolvedores corrijam problemas rapidamente antes que eles sejam mais difíceis e caros de corrigir.

5. **Confiabilidade**: Os testes unitários devem ser confiáveis e reproduzíveis, de forma que, ao serem executados várias vezes, sempre produzam os mesmos resultados.

6. **Desenvolvimento ágil**: Os testes unitários são uma parte importante do desenvolvimento ágil, permitindo que os desenvolvedores trabalhem de forma rápida e segura, garantindo que as mudanças no código não afetem negativamente outras partes do sistema.

Ao seguir esses conceitos, os testes unitários podem ser uma ferramenta valiosa para garantir a qualidade e a integridade do código, acelerar o processo de desenvolvimento e tornar o trabalho dos desenvolvedores mais fácil e seguro.

## O que preciso saber

Para trabalhar com testes unitários usando Jest, você precisa ter conhecimento básico em JavaScript e compreender os conceitos de testes unitários em geral. Além disso, você precisa saber:

1. [Instalação e configuração do Jest](https://jestjs.io/pt-BR/docs/getting-started) em seu projeto.

2. **Escrita de testes**: Jest fornece vários métodos, como describe, it, test, expect, etc., para escrever e executar seus testes.

3. **Asserções**: você precisa saber como usar a biblioteca expect para fazer asserções sobre o resultado dos testes.

4. **Mocks**: Jest permite que você crie "mocks" para funções externas, o que é útil para testar funções isoladas sem depender de seus componentes externos.

5. **Snapshots**: Jest permite que você crie "snapshots" de seus componentes, que podem ser usados para testar se sua saída é consistente.

6. **Execução de testes**: você precisa saber como executar seus testes usando o Jest, incluindo como gerar relatórios e cobertura de código.

Em geral, a familiaridade com Jest e a prática de escrever testes irão ajudá-lo a se tornar proficiente em testes unitários com Jest.

## Os métodos mais comuns:

1. **`describe`**: usado para agrupar testes relacionados em blocos lógicos. Cada describe pode conter vários it ou test para descrever comportamentos específicos.

2. **`it`**: usado para descrever um comportamento específico que você está testando. É equivalente ao test.

3. **`test`**: usado para descrever um comportamento específico que você está testando. É equivalente ao it.

4. **`beforeEach`** e **`afterEach`**: usados para executar código antes ou depois de cada teste. É útil para inicializar ou limpar dados antes ou depois de cada teste.

5. **`expect`**: usado para fazer asserções sobre o resultado dos testes. É a biblioteca central do Jest para verificar se seus testes estão passando ou falhando.

6. **`jest.fn`**: usado para criar mocks de funções. É útil para testar funções isoladas sem depender de seus componentes externos.

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

## Snapshots

Snapshots são uma forma de testar o comportamento de componentes ou objetos em seus testes de forma mais fácil e rápida. Em vez de escrever todas as verificações manualmente, você pode capturar uma imagem (snapshot) do componente ou objeto em questão e, em seguida, compará-lo com a versão capturada em futuros testes. Se o componente ou objeto mudar, você será notificado e pode atualizar o snapshot manualmente.

Você pode usar snapshots para testar componentes de interface do usuário (UI), como React components, ou objetos JSON.

Aqui está um exemplo de como você pode usar snapshots no Jest:

```javascript
test('should match the snapshot', () => {
  const component = <div>Hello, world</div>;
  expect(component).toMatchSnapshot();
});
```

Neste exemplo, estamos testando um componente React. Usamos o método toMatchSnapshot para comparar o componente com a versão capturada anteriormente. Se o componente mudar, o Jest notificará e você poderá atualizar o snapshot manualmente.

Em geral, você deve usar snapshots quando quiser testar componentes ou objetos que podem mudar com frequência, mas ainda precisam ser comparados com uma versão anterior. Isso permite que você teste o comportamento de seu código de forma mais fácil e rápida, sem precisar escrever verificações manualmente todas as vezes.

## Execução

A execução de testes no Jest funciona da seguinte maneira:

1. O Jest procura por arquivos de teste em seu projeto, geralmente com a extensão .test.js ou .spec.js.

2. Uma vez encontrados, o Jest carrega os arquivos de teste e procura por funções test ou describe.

3. Cada função test representa um caso de teste individual e é executada individualmente pelo Jest.

4. O Jest usa a biblioteca de asserção Jest para verificar se as expectativas em cada caso de teste são satisfeitas.

5. Quando todos os casos de teste são concluídos, o Jest exibe o resultado da execução de testes, incluindo quantos testes passaram ou falharam.

6. Se algum caso de teste falhar, o Jest exibe informações sobre a falha, como a mensagem de erro e a saída do console.

Você pode executar todos os seus testes com um único comando, como jest, ou executar apenas um subconjunto de testes específicos. O Jest também fornece recursos avançados, como testes paralelos, testes em segundo plano e cache de compilação para ajudar a otimizar a velocidade de execução de seus testes.

### Referências

- https://jestjs.io/pt-BR/docs/getting-started
- https://jestjs.io/pt-BR/docs/expect
- https://jestjs.io/pt-BR/docs/mock-function-api
- https://jestjs.io/pt-BR/docs/snapshot-testing
- https://jestjs.io/pt-BR/docs/configuration
