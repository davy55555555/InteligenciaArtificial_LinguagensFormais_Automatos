# Lista de Exercícios — Autômatos Finitos Determinísticos (AFD)

> Disciplina: Teoria das Linguagens e Autômatos
> Tema: Autômatos Finitos Determinísticos
> Modalidade: Atividade prática em grupo
> Objetivo: identificar, interpretar, construir e testar AFDs.

---

## Identificação do grupo

| Campo | Preenchimento |
|---|---|
| Turma | 2267189 - Linguagens Formais e Autômatos |
| Data | 05/09/2026 |
| Integrante 1 | Lucas Dórea Cardoso | 37277782 |
| Integrante 2 | Deivid Cerqueira | 39670953 |

---

## Parte 1 — Fundamentos

### Exercício 1 — Entendendo um autômato finito
Uma lâmpada controlada por um interruptor possui os estados `Desligado` e `Ligado`.

```text
Desligado --pressionar--> Ligado
Ligado    --pressionar--> Desligado
```

Responda:
1. Quantos estados existem?
2. Qual é o estado inicial?
3. Qual entrada provoca uma transição?
4. Partindo de `Desligado`, qual será o estado após um acionamento?
5. Partindo de `Desligado`, qual será o estado após dois acionamentos?
6. Explique o funcionamento com suas palavras.

### Exercício 2 — Porta automática
Uma porta automática possui os estados `Fechado` e `Aberto`.

| Estado atual | Entrada | Próximo estado |
|---|---|---|
| Fechado | pessoa_detectada | Aberto |
| Fechado | nenhuma_pessoa | Fechado |
| Aberto | pessoa_detectada | Aberto |
| Aberto | nenhuma_pessoa | Fechado |

Depois, desenhe o diagrama e identifique o estado inicial.

---

## Parte 2 — Anatomia e definição formal

### Exercício 3 — Identificando os elementos
Considere um AFD com `Σ = {0,1}`, `Q = {q0,q1}`, estado inicial `q0`, estado final `q1` e transições:

| δ | 0 | 1 |
|---|---|---|
| q0 | q0 | q1 |
| q1 | q0 | q1 |

Identifique:
1. o alfabeto Σ;
2. o conjunto de estados Q;
3. o estado inicial;
4. o conjunto de estados finais F;
5. os símbolos que podem ser lidos;
6. o significado do círculo duplo;
7. o significado da seta sem origem.

### Exercício 4 — A quíntupla do AFD
Um AFD é formalmente representado por:

```text
M = (Σ, Q, δ, q0, F)
```

Complete:

| Elemento | Significado |
|---|---|
| Σ | alfabeto |
| Q | conjunto de estados |
| δ | função de transição |
| q0 | estado inicial |
| F | estados de aceitação |

---

## Parte 3 — Tabela de transições e cadeias

### Exercício 5 — Interpretando uma tabela
Considere `Σ = {0,1}`, `Q = {q0,q1,q2}`, estado inicial `q0`, `F = {q1}` e:

| δ | 0 | 1 |
|---|---|---|
| q0 | q0 | q1 |
| q1 | q2 | q1 |
| q2 | q1 | q1 |

Responda:
1. Qual é o resultado de `δ(q0,0)`?
2. Qual é o resultado de `δ(q0,1)`?
3. Qual é o resultado de `δ(q1,0)`?
4. Qual é o resultado de `δ(q2,1)`?
5. Qual é o estado de aceitação?
6. Desenhe o diagrama correspondente.
7. Justifique por que o autômato é determinístico.

### Exercício 6 — Aceita ou rejeita?
Utilize o AFD do Exercício 5. Determine se cada cadeia é aceita ou rejeitada:

```text
a) 1
b) 0011001
c) 010010
d) 1101
e) 000011010
```

Para cada cadeia, registre o caminho percorrido e o resultado final.

---

## Parte 4 — Construção de AFDs

### Exercício 7 — Cadeias que terminam em 1
Construa um AFD sobre `Σ = {0,1}` que reconheça todas as cadeias que terminam em 1.

Aceitas: `1`, `01`, `101`, `0001`, `1101`
Rejeitadas: `ε`, `0`, `10`, `100`, `1110`

### Exercício 8 — Número par de símbolos 1
Construir um AFD que reconheça cadeias com quantidade par de 1s.

### Exercício 9 — Pelo menos dois zeros consecutivos
Construa um AFD para:

```text
L(M) = {w ∈ {0,1}* | w possui pelo menos dois 0s consecutivos}
```

Aceitas: `00`, `001`, `100`, `1001`, `110011`, `0000`
Rejeitadas: `ε`, `0`, `1`, `01`, `10`, `10101`

---

## Parte 5 — Desafios de modelagem

### Exercício 10 — Semáforo
Modelagem:
- Estados: Verde, Amarelo, Vermelho
- Entrada: tempo
- Sequência: Verde → Amarelo → Vermelho → Verde

### Exercício 11 — Sistema de login
Regra: após três tentativas incorretas consecutivas, o sistema bloqueia.

---

## Parte 6 — Prática no JFLAP
Use o JFLAP para criar e testar os autômatos construídos, validando as cadeias de exemplo.

---

## Conclusão
AFDs são ferramentas fundamentais para reconhecer linguagens regulares, interpretar padrões e modelar sistemas discretos com memória finita. A prática com tabelas, diagramas e simulações permite consolidar o raciocínio formal da disciplina.
