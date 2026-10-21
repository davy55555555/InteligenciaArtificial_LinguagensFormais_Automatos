# Registro dos testes

Simulador: [turingmachine.io](https://turingmachine.io/) com o programa de `maquina.yaml`.
Convenção: a máquina aceita ao parar em `qA`; rejeita ao parar em qualquer outro estado.

| Teste | Entrada | Resultado esperado | Resultado obtido | Estados percorridos | Passos |
|---|---|---|---|---|---|
| 1 | `0011` | ACEITA | ACEITA | q0 → q1 → q1 → q2 → q2 → q0 → q1 → q1 → q2 → q2 → q0 → q3 → q3 → qA | 13 |
| 2 | `000111` | ACEITA | ACEITA | q0 → q1 → q1 → q1 → q2 → q2 → q2 → q0 → q1 → q1 → q1 → q2 → q2 → q2 → q0 → q3 → qA | 17 |
| 3 | `001` | REJEITA | REJEITA | q0 → q1 → q1 → q2 → q2 → q0 → q1 → q1 | 7 |

## Observação
Entradas com quantidades equilibradas de zeros e uns passam pela lógica de marcação e terminam em `qA`.
