# Exercício – Particionamento em Classes de Equivalência e Análise do Valor Limite

## 1. Função de cálculo de desconto

### Dados de entrada

A função possui:

- **Cliente:** A, B ou C.
- **Qtd:** quantidade de itens comprados, variando de 1 a 1000.
- **Saída:** percentual de desconto.

### Regras

| Cliente | Quantidade | Desconto |
|---|---:|---:|
| A | < 10 | 0% |
| A | 10 a 99 | 5% |
| A | > 100 | 10% |
| B | < 10 | 5% |
| B | 10 a 99 | 15% |
| B | > 100 | 25% |
| C | < 10 | 0% |
| C | 10 a 99 | 20% |
| C | > 100 | 25% |

> **Observação:** As regras não especificam o que acontece com exatamente **100 itens**. Por isso, esse valor deve ser considerado um caso de teste importante para identificar uma possível inconsistência na especificação.

---

## 1.1 Particionamento em Classes de Equivalência

### Classe da variável Cliente

| Classe | Entrada | Situação |
|---|---|---|
| C1 | A | Válida |
| C2 | B | Válida |
| C3 | C | Válida |
| C4 | Qualquer outro valor | Inválida |

### Classes da variável Qtd

| Classe | Entrada | Situação |
|---|---:|---|
| Q1 | 1 a 9 | Válida |
| Q2 | 10 a 99 | Válida |
| Q3 | 100 | Caso não especificado |
| Q4 | 101 a 1000 | Válida |
| Q5 | Menor que 1 | Inválida |
| Q6 | Maior que 1000 | Inválida |

---

## 1.2 Casos de Teste – Classes de Equivalência

| ID | Cliente | Qtd | Resultado esperado | Tipo |
|---|---|---:|---|---|
| CT01 | A | 5 | 0% de desconto | Válido |
| CT02 | A | 20 | 5% de desconto | Válido |
| CT03 | A | 150 | 10% de desconto | Válido |
| CT04 | B | 5 | 5% de desconto | Válido |
| CT05 | B | 20 | 15% de desconto | Válido |
| CT06 | B | 150 | 25% de desconto | Válido |
| CT07 | C | 5 | 0% de desconto | Válido |
| CT08 | C | 20 | 20% de desconto | Válido |
| CT09 | C | 150 | 25% de desconto | Válido |
| CT10 | D | 20 | Entrada inválida | Inválido |
| CT11 | A | 0 | Entrada inválida | Inválido |
| CT12 | A | 1001 | Entrada inválida | Inválido |
| CT13 | A | 100 | Comportamento não especificado | Limite/especificação |

---

# 1.3 Análise de Valor Limite

Os principais limites da quantidade são:

- **1:** menor quantidade permitida;
- **10:** mudança de faixa;
- **99:** último valor da segunda faixa;
- **100:** valor não especificado;
- **101:** início da terceira faixa;
- **1000:** maior quantidade permitida.

Para testar os limites, podemos utilizar valores imediatamente antes, no limite e imediatamente depois.

| ID | Cliente | Qtd | Resultado esperado |
|---|---|---:|---|
| AVL01 | A | 1 | 0% |
| AVL02 | A | 9 | 0% |
| AVL03 | A | 10 | 5% |
| AVL04 | A | 99 | 5% |
| AVL05 | A | 100 | Não especificado |
| AVL06 | A | 101 | 10% |
| AVL07 | A | 1000 | 10% |
| AVL08 | B | 1 | 5% |
| AVL09 | B | 9 | 5% |
| AVL10 | B | 10 | 15% |
| AVL11 | B | 99 | 15% |
| AVL12 | B | 100 | Não especificado |
| AVL13 | B | 101 | 25% |
| AVL14 | B | 1000 | 25% |
| AVL15 | C | 1 | 0% |
| AVL16 | C | 9 | 0% |
| AVL17 | C | 10 | 20% |
| AVL18 | C | 99 | 20% |
| AVL19 | C | 100 | Não especificado |
| AVL20 | C | 101 | 25% |
| AVL21 | C | 1000 | 25% |

### Testes de limites inválidos

| ID | Cliente | Qtd | Resultado esperado |
|---|---|---:|---|
| AVL22 | A | 0 | Entrada inválida |
| AVL23 | A | 1001 | Entrada inválida |

---

# 2. Caso de Uso – Incluir Contato em uma Agenda Telefônica

## 2.1 Descrição do Caso de Uso

**Nome:** Incluir Contato

**Objetivo:** Permitir que o usuário cadastre um novo contato na agenda telefônica.

### Dados do contato

- Nome
- Telefone
- Email

### Regras de negócio

1. Todo contato deve possuir um número telefônico.
2. Não pode haver dois contatos com o mesmo número telefônico.
3. O número telefônico deve possuir entre **8 e 15 dígitos numéricos**.
4. O contato deve possuir um email válido no formato `*@*.*`.

---

# 2.2 Particionamento em Classes de Equivalência

## Nome

A especificação não estabelece regras de tamanho ou obrigatoriedade para o nome.

| Classe | Entrada | Situação |
|---|---|---|
| N1 | Nome preenchido | Válida |
| N2 | Nome vazio | Não especificado |

---

## Telefone

| Classe | Entrada | Situação |
|---|---|---|
| T1 | 8 a 15 dígitos numéricos | Válida |
| T2 | Menos de 8 dígitos | Inválida |
| T3 | Mais de 15 dígitos | Inválida |
| T4 | Contém letras ou caracteres não numéricos | Inválida |
| T5 | Campo vazio | Inválida |
| T6 | Número já cadastrado | Inválida |

---

## Email

A regra estabelecida é:

```text
*@*.*
