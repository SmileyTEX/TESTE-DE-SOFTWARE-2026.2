### 2. Casos de Teste para o Programa do Triângulo (Análise do Valor Limite)

Na análise do valor limite (AVL), testamos os limites das partições de equivalência (valores mínimo, logo acima do mínimo, normais, logo abaixo do máximo e máximo), considerando também as condições de existência de um triângulo (a < b + c, b < a + c, c < a + b) e a restrição de lados positivos (maiores que zero).

Assumindo os lados a, b e c como inteiros positivos:

| ID | Lado A | Lado B | Lado C | Resultado Esperado | Classe/Objetivo do Teste |
|---|---|---|---|---|---|
| CT01 | 0 | 5 | 5 | Entrada Inválida | Limite inferior inválido (Lado A = 0) |
| CT02 | 1 | 5 | 5 | Triângulo Isósceles | Limite inferior válido (Lado A = 1) |
| CT03 | 5 | 5 | 5 | Triângulo Equilátero | Caso típico / Todos os lados iguais |
| CT04 | 3 | 4 | 5 | Triângulo Escaleno | Caso típico / Todos os lados diferentes |
| CT05 | 5 | 5 | 10 | Não forma Triângulo | Limite da condição de existência (a + b = c) |
| CT06 | 5 | 5 | 9 | Triângulo Isósceles | Limite da condição de existência (a + b > c) |
| CT07 | 10 | 2 | 2 | Não forma Triângulo | Violação da condição de existência (a >= b + c) |

---

### 3. Casos de Teste para o Desconto por Dependente (Análise do Valor Limite)

A variável de entrada é a **Idade** (inteiro no intervalo [0..24]).

**Limites de transição identificados:**
* **Fora do limite inferior:** < 0 (Inválido)
* **Faixa 1 [0..12] (15%):** Limites em 0 e 12
* **Faixa 2 [13..18] (12%):** Limites em 13 e 18
* **Faixa 3 [19..21] (5%):** Limites em 19 e 21
* **Faixa 4 [22..24] (3%):** Limites em 22 e 24
* **Fora do limite superior:** > 24 (Inválido)

| ID | Idade | Resultado Esperado (Desconto) | Descrição / Fronteira Analisada |
|---|---|---|---|
| CT01 | -1 | Entrada Inválida | Logo abaixo do limite mínimo global (Inválido) |
| CT02 | 0 | Desconto de 15% | Limite mínimo global / Limite inferior da Faixa 1 |
| CT03 | 1 | Desconto de 15% | Logo acima do limite mínimo |
| CT04 | 12 | Desconto de 15% | Limite superior da Faixa 1 |
| CT05 | 13 | Desconto de 12% | Limite inferior da Faixa 2 |
| CT06 | 18 | Desconto de 12% | Limite superior da Faixa 2 |
| CT07 | 19 | Desconto de 5% | Limite inferior da Faixa 3 |
| CT08 | 21 | Desconto de 5% | Limite superior da Faixa 3 |
| CT09 | 22 | Desconto de 3% | Limite inferior da Faixa 4 |
| CT10 | 24 | Desconto de 3% | Limite máximo global / Limite superior da Faixa 4 |
| CT11 | 25 | Entrada Inválida | Logo acima do limite máximo global (Inválido) |
