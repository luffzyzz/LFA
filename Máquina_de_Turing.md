# Atividade — Máquinas de Turing

## Etapa 1 — Introdução

### 1. O que é uma Máquina de Turing?
A Máquina de Turing é um modelo simples de como um computador funciona. Ela tem uma fita dividida em quadros e um leitor que consegue olhar o símbolo de cada quadro, apagar, escrever algo novo e se mover para os lados. O leitor segue regras bem definidas sobre o que fazer. É com esse modelo que se estuda como os algoritmos operam e o que dá ou não para calcular.

### 2. Quais são os principais componentes de uma Máquina de Turing?

Os principais componentes são:

- **Fita:** armazena os símbolos utilizados durante a execução.
- **Cabeça de leitura/escrita:** lê e altera os símbolos da fita e pode se movimentar para a esquerda ou para a direita.
- **Estados:** representam as diferentes situações em que a máquina pode estar durante a execução.
- **Alfabeto:** conjunto de símbolos que podem ser utilizados.
- **Regras de transição:** determinam qual ação deve ser realizada para cada símbolo lido em determinado estado.
- **Estado inicial:** estado em que a máquina começa.
- **Estados de aceitação e rejeição:** determinam se a entrada foi aceita ou rejeitada.

### 3. Qual é a importância das Máquinas de Turing para a computação?
As Máquinas de Turing são fundamentais para explicar de forma teórica o funcionamento de computadores e algoritmos. Esse modelo permite analisar a capacidade de resolução de problemas por meio de processos computacionais e identificar os limites da computação, demonstrando a existência de problemas para os quais não há algoritmo capaz de encontrar uma solução.

### 4. Qual é a relação entre Máquina de Turing e algoritmo?
Um algoritmo é uma sequência de instruções para resolver um problema. A Máquina de Turing representa essa execução utilizando estados, símbolos e regras de transição. Trata-se de um modelo que permite analisar formalmente o funcionamento dos algoritmos e a capacidade computacional na resolução de problemas.

## Etapa 2 — Simulação

### Linguagem reconhecida

A Máquina de Turing reconhece palavras da forma:

**0ⁿ1ⁿ**

Ou seja, a palavra deve possuir uma quantidade igual de símbolos `0` e `1`, com todos os `0` aparecendo antes dos `1`.

### Exemplos aceitos

- `01`
- `0011`
- `000111`
- `00001111`

### Exemplos rejeitados

- `0`
- `1`
- `001`
- `011`
- `00111`

### Funcionamento da máquina

A máquina utiliza os símbolos auxiliares `X` e `Y`.

- `X` representa um `0` que já foi utilizado.
- `Y` representa um `1` que já foi utilizado.
- A máquina procura um `0` ainda não marcado e o transforma em `X`.
- Em seguida, procura um `1` correspondente e o transforma em `Y`.
- Esse processo continua até que todos os `0` tenham sido associados a um `1`.
- Ao final, a máquina aceita somente quando existir a mesma quantidade de `0` e `1` e os símbolos estiverem na ordem correta.

### Estados

- `q0` — procura o próximo `0` não marcado.
- `q1` — procura o `1` correspondente ao `0` marcado.
- `q2` — retorna para o início da fita.
- `q3` — verifica se não existem símbolos `0` não correspondidos.
- `qAceita` — aceita a palavra.
- `qRejeita` — rejeita a palavra.

### Regras principais de transição

| Estado | Lê | Escreve | Movimento | Próximo estado |
|---|---|---|---|---|
| `q0` | `X` | `X` | → | `q0` |
| `q0` | `0` | `X` | → | `q1` |
| `q0` | `Y` | `Y` | → | `q3` |
| `q1` | `0` | `0` | → | `q1` |
| `q1` | `Y` | `Y` | → | `q1` |
| `q1` | `1` | `Y` | ← | `q2` |
| `q1` | `□` | `□` | → | `qRejeita` |
| `q2` | `0` | `0` | ← | `q2` |
| `q2` | `X` | `X` | ← | `q2` |
| `q2` | `Y` | `Y` | ← | `q2` |
| `q2` | `□` | `□` | → | `q0` |
| `q3` | `Y` | `Y` | → | `q3` |
| `q3` | `1` | `1` | → | `qRejeita` |
| `q3` | `0` | `0` | → | `qRejeita` |
| `q3` | `□` | `□` | → | `qAceita` |

---

## Etapa 3 — Registro da simulação

### Teste 1

**Entrada:** `0011`

**Resultado esperado:** ACEITA

**Resultado obtido:** ACEITA

**Estados percorridos:**

`q0 → q1 → q2 → q0 → q1 → q2 → q0 → q3 → q3 → qAceita`

---

### Teste 2

**Entrada:** `000111`

**Resultado esperado:** ACEITA

**Resultado obtido:** ACEITA

**Estados percorridos:**

`q0 → q1 → q2 → q0 → q1 → q2 → q0 → q1 → q2 → q0 → q3 → q3 → q3 → qAceita`

---

### Teste 3

**Entrada:** `00111`

**Resultado esperado:** REJEITA

**Resultado obtido:** REJEITA

**Estados percorridos:**

`q0 → q1 → q2 → q0 → q1 → q2 → q0 → q3 → q3 → q3 → qRejeita`

---

## Descrição da Máquina de Turing criada

A Máquina de Turing criada verifica se uma palavra possui a mesma quantidade de 0 e 1, mantendo os 0 antes dos 1. Para isso, cada 0 encontrado é marcado com X e associado a um 1, que é marcado com Y. A máquina repete esse processo até que todos os símbolos sejam verificados. Caso exista uma quantidade diferente de 0 e 1, ou a ordem dos símbolos esteja incorreta, a palavra é rejeitada. Quando todos os símbolos são correspondentes e a estrutura da palavra está correta, a máquina aceita a entrada.

---

## Etapa 4 — Reflexão sobre os limites computacionais

A Máquina de Turing é capaz de resolver apenas problemas que possuem uma solução algorítmica, conhecidos como problemas computáveis. Existem questões que não podem ser resolvidas por nenhum computador, independentemente de sua capacidade ou tempo do processamento, essas questões são classificadas como problemas indecidíveis, para os quais é impossível criar um algoritmo universalmente correto. Dessa forma, o modelo da Máquina de Turing serve para mapear com clareza as fronteiras do que é teoricamente possível calcular, com essa análise, torna-se simples diferenciar um problema que é apenas difícil daqueles que são de fato impossíveis de resolver.

---

## Questão final
Um problema difícil possui um algoritmo para sua resolução, ainda que exija bastante tempo ou recursos, em contrapartida, um problema indecidível não conta com nenhum algoritmo capaz de solucioná-lo em todos os casos, a Máquina de Turing é o modelo teórico utilizado para demonstrar essa diferença. Analisar a existência de um algoritmo permite identificar a viabilidade teórica da solução, essa distinção separa o que é apenas complexo daquilo que é computacionalmente impossível.
