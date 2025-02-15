# **Linha do Tempo de Ajustes**

Este documento registra todas as alterações realizadas para facilitar buscas e consultas futuras.

---

## **15/02/2025**

### **Faturamento Pecuário por HA**

- **Ajuste na Medida de HA Usado e no Valor do HA Pasto**
  - **Descrição:** O cálculo foi ajustado para considerar `HA pasto` em vez de `HA geral`, além da atualização nos valores de `HA pasto` para as seguintes fazendas:
    - **AURORA**: 411,24 → 431,24
    - **DESTAK**: 412,12 → 411,12
  - **O que mudou:** A medida `HA` foi substituída por `HA pasto` para refletir o uso correto de área.

- **Painéis Impactados:**
  - [Faturamento Pecuário por HA - Benchmark Cria](./benchmark_cria/custo_por_cabeca.md)
  - [Faturamento Pecuário por HA - Benchmark Recria](./benchmark_recria/custo_por_cabeca.md)

### **Custo por Cabeça**

- **Ajuste no Cálculo do Custo**
  - **Descrição:** O cálculo do custo médio mensal foi refinado para garantir que apenas registros classificados como "DESPESAS" sejam considerados no filtro de saída.
  - **O que mudou:** A medida `Custo médio mensal` foi ajustada para excluir qualquer valor que não se enquadre na categoria "DESPESAS".

- **Painéis Impactados:**
  - [Custo por Cabeça - Benchmark Cria](./benchmark_cria/custo_por_cabeca.md)
  - [Custo por Cabeça - Benchmark Recria](./benchmark_recria/custo_por_cabeca.md)

---