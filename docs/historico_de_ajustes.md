# **Linha do Tempo de Ajustes**

Este documento registra todas as alterações realizadas para facilitar buscas e consultas futuras.

---

## **15/02/2025**

### **Faturamento Pecuário por HA**

- **Ajuste na medida de HA usado e no valor do HA pasto**
  - **Descrição:** Ajuste no cálculo para considerar HA pasto ao invés de HA geral e ajuste nos valores de HA pasto das fazendas:
AURORA 411,24 -> 431,24
DESTAK 412,12 -> 411,12
  - **O que mudou:** Substituimos a medida `HA`por `HA pasto`.

- **Painéis Impactados:**
  - [Faturamento Pecuário por HA - Benchmark Cria](./benchmark_cria/custo_por_cabeca.md)
  - [Faturamento Pecuário por HA - Benchmark Recria](./benchmark_recria/custo_por_cabeca.md)

### **Custo por Cabeça**

- **Ajuste no Cálculo do Custo**
  - **Descrição:** O cálculo do custo médio mensal foi ajustado para garantir que o filtro de saída considere apenas registros classificados como "DESPESAS".
  - **O que mudou:** A medida `Custo médio mensal` foi alterada para excluir qualquer valor que não seja categorizado como "DESPESAS" do cálculo.

- **Painéis Impactados:**
  - [Custo por cabeça - Benchmark Cria](./benchmark_cria/custo_por_cabeca.md)
  - [Custo por cabeça - Benchmark Recria](./benchmark_recria/custo_por_cabeca.md)

---