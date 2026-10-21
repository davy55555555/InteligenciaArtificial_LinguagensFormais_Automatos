# Aula 1 — Linguagens Formais e Gramáticas

> Introdução aos principais conceitos de alfabetos, palavras, linguagens e gramáticas.

## 1. Alfabeto Σ
Um alfabeto é um conjunto finito de símbolos. Exemplo: `Σ = {a, b, 0, 1}`.

## 2. Cadeia
Uma cadeia (ou palavra) é uma sequência finita de símbolos do alfabeto. Exemplo: `abba`.

## 3. Palavra vazia ε
`ε` representa a cadeia vazia, sem nenhum símbolo. Seu comprimento é zero.

## 4. Prefixos e sufixos
- Prefixo: parte inicial da palavra
- Sufixo: parte final da palavra

Exemplo para `ab`:
- Prefixos: `ε`, `a`, `ab`
- Sufixos: `ε`, `b`, `ab`

## 5. Σ*
`Σ*` representa o conjunto de todas as cadeias finitas sobre Σ, incluindo ε.

## 6. Linguagem formal L
Uma linguagem formal é um subconjunto de `Σ*`.

## 7. Gramática formal
Uma gramática formal é uma quádrupla `G = (N, Σ, P, S)`, onde:
- N: não-terminais
- Σ: terminais
- P: regras de produção
- S: símbolo inicial

## 8. Regras de produção
Uma regra tem a forma `A → α` e indica a substituição de um não-terminal por outra sequência.

## 9. Derivação
O processo de aplicar regras até formar uma cadeia somente com símbolos terminais.

Exemplo:
```text
S → aS → aaS → aa
```

## 10. Resumo
LFA estuda como linguagens podem ser descritas, geradas e reconhecidas por formalismos como gramáticas, autômatos e máquinas de Turing.
