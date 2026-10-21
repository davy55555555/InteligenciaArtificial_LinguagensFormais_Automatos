# Gramáticas Formais

**Disciplina:** Linguagens Formais e Autômatos  
**Tema:** Gramáticas Formais e Hierarquia de Chomsky

## 1. Objetivos da aula
- Compreender o conceito de gramática formal
- Identificar os componentes de uma gramática
- Interpretar regras de produção
- Realizar derivações passo a passo
- Classificar gramáticas conforme a hierarquia de Chomsky

## 2. O que é uma gramática formal?
Uma gramática formal pode ser representada por:

```text
G = (V, T, P, S)
```

Onde:
- `V`: variáveis ou não-terminais
- `T`: terminais
- `P`: produções
- `S`: símbolo inicial

## 3. Como ler uma regra de produção?
Exemplo:
```text
S → aS
```
Lê-se: "S produz aS".

Outra regra:
```text
S → b
```
Lê-se: "S produz b".

## 4. Exemplo de derivação
```text
S ⇒ aS ⇒ aaS ⇒ aab
```

A palavra gerada é `aab`.

## 5. Importância
Gramáticas formam a base para descrever linguagens e relacionar diferentes formalismos de análise.
