# Relatório — Expressões Regulares

## Objetivo
Modelar linguagens formais por meio de expressões regulares, verificar exemplos de aceitação e rejeição e relacionar cada padrão à ideia de um autômato finito.

## Notação usada
- `|`: escolha entre alternativas
- `*`: zero ou mais ocorrências
- `?`: ocorrência opcional
- `()`: agrupamento
- `^` e `$`: início e fim da entrada
- `[A-Z]`, `[a-z]` e `[0-9]`: faixas de caracteres
- `{n}`: exatamente `n` ocorrências

---

## Exercício 1 — palavras binárias terminadas em `00`

**Linguagem:** `L₁ = { w00 | w ∈ {0,1}* }`

**Regex:**
```regex
^(0|1)*00$
```

| Aceitos | Rejeitados |
|---|---|
| `00` | `0` |
| `10100` | `1010` |
| `01100` | `001` |

**Relação com o autômato:** o autômato precisa reter a informação de que os dois últimos símbolos lidos são `00`.

---

## Exercício 2 — palavras com exatamente dois `a`

**Linguagem:** palavras sobre `{a,b}` contendo exatamente duas ocorrências de `a`.

**Regex:**
```regex
^b*ab*ab*$
```

| Aceitos | Rejeitados |
|---|---|
| `aa` | `a` |
| `aba` | `bbbb` |
| `bbaabb` | `aababa` |

---

## Exercício 3 — identificador estruturado

**Linguagem:** identificadores formados por duas letras maiúsculas, três algarismos e uma letra minúscula opcional.

**Regex:**
```regex
^[A-Z]{2}[0-9]{3}[a-z]?$ 
```

| Aceitos | Rejeitados |
|---|---|
| `AB123` | `A123` |
| `QZ008m` | `AB12` |
| `XY999a` | `xy999` |
| `RT451` | `RT451qq` |

---

## Desafio — matrícula acadêmica
Formato exigido: `CURSO-ANO-NÚMERO-TURNO`.

**Regex:**
```regex
^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-(M|T|N)$
```

### Justificativa dos blocos
- `(CCO|ESW|SIS)`: aceita somente os cursos permitidos
- `202[4-9]`: restringe o ano
- `[0-9]{4}`: exige quatro dígitos
- `(M|T|N)`: turno válido
- `-`: separa os blocos
- `^` e `$`: impedem prefixos e sufixos

| Aceitos | Rejeitados |
|---|---|
| `CCO-2024-0007-M` | `CCO-2030-0007-M` |
| `ESW-2026-1842-T` | `ESW-2026-842-T` |
| `SIS-2029-9999-N` | `SIS-2029-9999-V` |
| `CCO-2025-1200-N` | `CCO-2025-1200-Nx` |

---

## Ferramenta de validação
Os exemplos foram validados em ferramentas de regex, como Regex101, para verificar aceitação e rejeição.
