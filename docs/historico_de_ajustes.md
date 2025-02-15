# **Linha do Tempo de Ajustes**

Este documento registra todas as alterações realizadas para facilitar buscas e consultas futuras.

---

## **15/02/2025**

### **Mortes Bezerros**
- **Ajuste query TodasMovimentações**
  - **Descrição:** Painel não estava considerando todos os bezerros.
  - **Ajuste realizado:** Ajuste na query `TodasMovimentações`, agora todos animais que entram via planilha de `nascimentos`recebem a categoria de `BEZERRO`. 

- **Painéis Impactados:**
  - [Mortes Bezerros - Benchmark Cria](./benchmark_cria/mortalidade_bezerros.md)
  - [Mortes Bezerros - Benchmark Recria](./benchmark_recria/mortalidade_bezerros.md)


### **Lotação Pasto (UA/HA)**

- **Ajuste na Medida de HA Usado**
  - **Descrição:** O cálculo foi ajustado para considerar `HA pasto` em vez de `HA geral`.
  - **Ajuste realizado:** A medida `HA` foi substituída por `HA pasto` para refletir o uso correto de área.

- **Painéis Impactados:**
  - [Lotação Pasto (UA/HA) - Benchmark Cria](./benchmark_cria/lotacao_pasto.md)
  - [Lotação Pasto (UA/HA) - Benchmark Recria](./benchmark_recria/lotacao_pasto.md)

### **Valor HA Pasto**

- **Ajuste no valor do HA Pasto**
  - **Descrição:** Atualização nos valores de `HA pasto` para algumas fazendas.
  - **Ajuste realizado:**: Mudança nos valores das seguintes fazendas:
    - **AURORA**: 411,24 → 431,24
    - **DESTAK**: 412,12 → 411,12


### **Faturamento Pecuário por HA**

- **Ajuste na Medida de HA Usado**
  - **Descrição:** O cálculo foi ajustado para considerar `HA pasto` em vez de `HA geral`.
  - **Ajuste realizado:** A medida `HA` foi substituída por `HA pasto` para refletir o uso correto de área.

- **Painéis Impactados:**
  - [Faturamento Pecuário por HA - Benchmark Cria](./benchmark_cria/faturamento_pecuario_por_ha.md)
  - [Faturamento Pecuário por HA - Benchmark Recria](./benchmark_recria/faturamento_pecuario_por_ha.md)

### **Custo por Cabeça**

- **Ajuste no Cálculo do Custo**
  - **Descrição:** O cálculo do custo médio mensal foi refinado para garantir que apenas registros classificados como "DESPESAS" sejam considerados no filtro de saída.
  - **Ajuste realizado:** A medida `Custo médio mensal` foi ajustada para excluir qualquer valor que não se enquadre na categoria "DESPESAS".

- **Painéis Impactados:**
  - [Custo por Cabeça - Benchmark Cria](./benchmark_cria/custo_por_cabeca.md)
  - [Custo por Cabeça - Benchmark Recria](./benchmark_recria/custo_por_cabeca.md)

---