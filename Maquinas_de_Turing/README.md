# Aula 09 — Máquinas de Turing

Atividade remota de Linguagens Formais e Autômatos.

| Arquivo | Conteúdo |
|---|---|
| `tabela_de_transicoes.md` | máquina que reconhece 0ⁿ1ⁿ |
| `maquina.yaml` | programa para colar no simulador |
| `registro_dos_testes.md` | testes com estados percorridos |
| `Atividade_Maquinas_de_Turing_Deivid_Cerqueira.pdf` | relatório completo |

A máquina em questão reconhece sequências da forma `0^n1^n` com `n ≥ 1`.

## Ideia geral
A fita percorre da esquerda para a direita, marcando `0` e `1` conforme a lógica da máquina. Quando todos os zeros forem pareados com os uns, a máquina entra em um estado de aceitação.
