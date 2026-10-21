---
title: "Tutorial — Usando Regex para representar e validar um e-mail"
subtitle: "Linguagens Formais e Autômatos — Material do estudante"
author: "Professora Kadidja Valéria"
lang: pt-BR
date: "14/09/2026"
---

# 1. Objetivo

Neste tutorial, você aprenderá a construir uma expressão regular para verificar se um texto apresenta o formato básico de um endereço de e-mail.

> **Importante:** uma Regex não escreve o conteúdo de uma mensagem. Ela reconhece, pesquisa ou valida padrões de texto.

# 2. Estrutura de um endereço de e-mail

Um e-mail geralmente possui três partes:

```text
usuario@dominio.extensao
```

Exemplo:
```text
kadidja.oliveira@udf.edu.br
```

| Parte | Exemplo | Descrição |
|---|---|---|
| Usuário | `kadidja.oliveira` | identifica a pessoa ou conta |
| Separador | `@` | separa usuário do domínio |
| Domínio | `udf.edu.br` | identifica a instituição |

# 3. Construção progressiva da Regex

## Etapa 1 — Reconhecer o nome do usuário

```regex
[A-Za-z0-9._+-]+
```

Essa parte aceita letras, números, pontos, sublinhados e hífens.

## Etapa 2 — Acrescentar o símbolo `@`

```regex
[A-Za-z0-9._+-]+@
```

## Etapa 3 — Reconhecer o domínio

```regex
[A-Za-z0-9.-]+
```

## Etapa 4 — Reconhecer a extensão

```regex
\.[A-Za-z]{2,}
```

# 4. Expressão regular completa

```regex
^[A-Za-z0-9._+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$
```

## Função dos delimitadores
- `^`: início do texto
- `$`: final do texto

Esses símbolos impedem que a Regex aceite um e-mail como parte de um texto maior.

# 5. Exemplos de teste

| Entrada | Resultado esperado | Motivo |
|---|---:|---|
| `aluno@gmail.com` | Válido | Possui usuário, `@`, domínio e extensão |
| `nome.sobrenome@udf.edu.br` | Válido | Aceita pontos e mais de uma parte no domínio |
| `estudante_01@faculdade.com` | Válido | Aceita sublinhado e números |
| `contato+curso@exemplo.com.br` | Válido | Aceita o sinal `+` |
| `aluno.gmail.com` | Inválido | Não possui `@` |
| `aluno@` | Inválido | Não possui domínio |
| `@gmail.com` | Inválido | Não possui usuário |
| `aluno@gmail` | Inválido | Não possui extensão |
| `aluno@gmail.c` | Inválido | Extensão curta |
| `aluno gmail.com` | Inválido | Contém espaço |

# 6. Testando a Regex em Python

```python
import re

padrao_email = r"^[A-Za-z0-9._+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$"

email = input("Digite um endereço de e-mail: ")

if re.fullmatch(padrao_email, email):
    print("O e-mail apresenta um formato válido.")
else:
    print("O formato do e-mail é inválido.")
```

# 7. Relação com Linguagens Formais

A regex descreve uma linguagem de cadeias válidas segundo um padrão estrutural.

A expressão se resume em:
```text
USUARIO @ DOMINIO . EXTENSAO
```

# 8. Limitações importantes
A regex valida o formato, mas não garante que o e-mail realmente exista ou esteja ativo.

# 9. Atividade prática
Construa um programa que:
1. solicite cinco endereços de e-mail;
2. valide cada endereço com uma regex;
3. separe válidos e inválidos;
4. explique por que cada entrada foi rejeitada.
