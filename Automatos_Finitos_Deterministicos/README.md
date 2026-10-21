# Entrega — Autômatos Finitos Determinísticos (AFD)

## Identificação do grupo
- Disciplina: Teoria das Linguagens e Autômatos
- Turma: 2267189 - Linguagens Formais e Autômatos
- Data: 05/09/2026
- Integrante 1: Lucas Dórea Cardoso — 37277782
- Integrante 2: Deivid Cerqueira — 39670953

---

## Objetivo
Modelar, interpretar e validar autômatos finitos determinísticos por meio de tabelas, diagramas e testes práticos.

## Conceitos fundamentais

### 1. O que é um AFD?
Um Autômato Finito Determinístico é uma máquina que processa cadeias de símbolos de entrada, avançando de estado em estado conforme uma função de transição.

### 2. Elementos
- Σ: alfabeto
- Q: conjunto de estados
- δ: função de transição
- q0: estado inicial
- F: conjunto de estados finais

### 3. Determinismo
Para cada estado e para cada símbolo do alfabeto, há exatamente uma transição possível.

---

## Exercício 1 — Lâmpada com interruptor
Uma lâmpada com dois estados: Desligado e Ligado.

- Estados: {Desligado, Ligado}
- Estado inicial: Desligado
- Entrada: pressionar
- Transições:
  - δ(Desligado, pressionar) = Ligado
  - δ(Ligado, pressionar) = Desligado

Explicação: o botão alterna o estado da lâmpada.

---

## Exercício 2 — Porta automática
Estados: {Fechado, Aberto}

| Estado atual | Entrada | Próximo estado |
|---|---|---|
| Fechado | pessoa_detectada | Aberto |
| Fechado | nenhuma_pessoa | Fechado |
| Aberto | pessoa_detectada | Aberto |
| Aberto | nenhuma_pessoa | Fechado |

Explicação: quando alguém é detectado, a porta abre; se não houver presença, ela fecha.

---

## Exercício 3 — Interpretação da quíntupla
Um AFD formalmente é:

M = (Σ, Q, δ, q0, F)

- Σ: alfabeto de entrada
- Q: conjunto de estados
- δ: transição
- q0: estado inicial
- F: estados finais

Essa estrutura é suficiente para definir completamente o comportamento do autômato.

---

## Exercício 4 — Cadeias que terminam em 1
Objetivo: reconhecer cadeias sobre {0,1} que terminam em 1.

- Estados: q0, q1
- Estado inicial: q0
- Estado final: q1
- Transições:
  - δ(q0,0)=q0
  - δ(q0,1)=q1
  - δ(q1,0)=q0
  - δ(q1,1)=q1

Exemplos aceitos:
- 1
- 01
- 101
- 0001

Exemplos rejeitados:
- ε
- 0
- 10
- 100

---

## Exercício 5 — Número par de 1s
Objetivo: aceitar cadeias com número par de 1s.

- Estados: q0 (par), q1 (ímpar)
- Estado inicial: q0
- Estado final: q0

Transições:
- δ(q0,0)=q0
- δ(q0,1)=q1
- δ(q1,0)=q1
- δ(q1,1)=q0

---

## Exercício 6 — Pelo menos dois zeros consecutivos
Objetivo: reconhecer cadeias com oo em algum ponto.

- Estados: q0, q1, q2
- Estado inicial: q0
- Estado final: q2

Transições:
- δ(q0,0)=q1
- δ(q0,1)=q0
- δ(q1,0)=q2
- δ(q1,1)=q0
- δ(q2,0)=q2
- δ(q2,1)=q2

Aceitas: 00, 001, 100, 0000
Rejeitadas: ε, 0, 1, 01, 10

---

## Observação prática
AFDs são úteis para reconhecer padrões, validar entradas e modelar sistemas reativos simples. Em aplicações reais, o uso de ferramentas como JFLAP ajuda a testar cadeias e confirmar a lógica das transições.
