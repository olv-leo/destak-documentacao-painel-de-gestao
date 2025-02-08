# **Impacto dos Lançamentos de Estoque no Financeiro**

Esta página explica como os lançamentos na planilha de `estoque` afetam o financeiro.

## **Lançamentos na Fazenda "ESTOQUE"**
Na planilha de movimentações de estoque, a entrada de itens ocorre através de um lançamento de entrada na fazenda `ESTOQUE`. Esses lançamentos possuem um comportamento específico no financeiro.

Quando um item entra no estoque, o valor total da entrada é inicialmente registrado na fazenda `ESTOQUE`.

### **Exemplo de Lançamento no Estoque**

| data_lancamento | fazenda | cod_produto | desc_produto | fornecedor | status_item | classif_mov | qtde_unit | unid_medida | valor_unitario | valor_total |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 24/10/2024 | ESTOQUE | 37 | BEBEDOUROS 1.200L | CAMPO FACIL | RECEBIDO | ENTRADA | 31 | UNI | R$ 1.403,23 | R$ 43.500 |

### **Lançamento Financeiro da Compra**

| data_nota | data_vencimento | data_pagamento | fazenda | desc_lancamento | forma_pgto | banco | valor_pagamento |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 24/10/2024 | 18/10/2024 | 14/10/2024 | ESTOQUE | BEBEDOUROS 1.200L | PIX | BRADESCO | R$ 43.500,00 |

### **Resumo Simplificado**

#### **Planilha `estoque`**
| data | fazenda | produto | movimen | qtde | valor_unitario | total |
| --- | --- | --- | --- | --- | --- | --- |
| 01/01/2025 | ESTOQUE | BEBEDOUROS 1.200L | ENTRADA | 31 | R$ 1.403,23 | R$ 43.500,13 |

#### **Planilha `financeiro`**
| data | fazenda | desc_lancamento | valor_pagamento |
| --- | --- | --- | --- |
| 01/01/2025 | ESTOQUE | BEBEDOUROS 1.200L | R$ 43.500,13 |

## **Distribuição do Custo ao Longo do Tempo**
Conforme os itens saem do estoque para outras fazendas, o custo correspondente é transferido da fazenda `ESTOQUE` para a fazenda de destino.

Exemplo:

### **Planilha `estoque` com Movimentações**

| data | fazenda | produto | movimen | qtde |
| --- | --- | --- | --- | --- |
| 01/01/2025 | ESTOQUE | BEBEDOUROS 1.200L | ENTRADA | 31 |
| 05/01/2025 | PARAÍSO | BEBEDOUROS 1.200L | SAÍDA | 2 |

### **Planilha `financeiro` após a Saída**

| data | fazenda | desc_lancamento | valor_pagamento |
| --- | --- | --- | --- |
| 01/01/2025 | ESTOQUE | BEBEDOUROS 1.200L | R$ 40.693,67 |
| 01/01/2025 | PARAÍSO | BEBEDOUROS 1.200L | R$ 2.806,46 |

O custo foi transferido do `ESTOQUE` para a fazenda `PARAÍSO` conforme a saída dos itens.

## **Cálculo do Custo de Saída (FIFO)**
Se um produto teve múltiplas entradas, o custo considerado para a saída será o da entrada mais antiga, seguindo a metodologia **FIFO (First In, First Out)**.

Exemplo:

| data_entrada | produto | qtde_entrada | preco_unitario |
| --- | --- | --- | --- |
| 01/01/2025 | PRODUTO 1 | 5 | R$ 25,00 |
| 05/01/2025 | PRODUTO 1 | 10 | R$ 34,00 |

Se houver uma saída de 3 unidades, o custo considerado será:
- **3 unidades a R$ 25,00 (entrada de 01/01/2025)**

## **Múltiplos Custos na Saída**
Se uma saída envolver produtos adquiridos em momentos diferentes, o custo será proporcional às entradas mais antigas.

Exemplo:

| data_entrada | produto | qtde_entrada | preco_unitario |
| --- | --- | --- | --- |
| 01/01/2025 | PRODUTO 2 | 4 | R$ 20,00 |
| 05/01/2025 | PRODUTO 2 | 20 | R$ 55,00 |

Caso haja uma saída de **10 unidades**, a alocação do custo será:
- **4 unidades a R$ 20,00 (entrada de 01/01/2025)**
- **6 unidades a R$ 55,00 (entrada de 05/01/2025)**

---
Essa lógica garante que o custo real das saídas seja refletido corretamente no financeiro.
