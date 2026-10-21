# Aula 1 — Atividades Práticas (respostas)

## Atividade 1 — Prefixos e Sufixos
Considere a palavra:
```text
ab
```

### Prefixos
```text
Prefixos(ab) = {ε, a, ab}
```

### Sufixos
```text
Sufixos(ab) = {ε, b, ab}
```

### Observação
A palavra vazia ε é tanto prefixo quanto sufixo de qualquer palavra.

---

## Atividade 2 — Gramática
Considere:
```text
G = ({S}, {a}, {S → aS | ε}, S)
```

### Três palavras geradas
1. `ε`
2. `a`
3. `aa`

A linguagem gerada é:
```text
L(G) = {aⁿ | n ≥ 0}
```
