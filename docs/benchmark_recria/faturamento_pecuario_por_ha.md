# **Faturamento Pecuário por HA**  

---
### **Explicação do Cálculo**  
**Fórmula Matemática:**  
$$
\text{Faturamento pecuário por HA} = \frac{\text{Faturamento}}{\text{Número de Hectares}}
$$


### **Fórmulas DAX**  
A seguir estão detalhadas todas as fórmulas DAX utilizadas.  

#### **Cálculo final**  
```dax
Faturamento pecuário por HA = [Faturamento] / [HA]
```  

---  

#### **Medidas intermediárias**  

```dax
Faturamento = 
CALCULATE(
    SUM(MovimentacoesFinanceiras[valor_pagamento])
    , MovimentacoesFinanceiras[classificacao] = "RECEITAS"
    )
```  

```dax
HA pasto = 
SUM(Fazendas[area_ha_pasto])
```  

## **Benchmarks e Indicadores**  

### **Médias de Benchmark**  
```dax
Bench - Faturamento pecuário por HA (Média clientes) = 
CALCULATE(
    SUM(BenchmarkRecria[media_clientes])
    , BenchmarkRecria[metrica] = "FATURAMENTO PECUÁRIO POR HA/ANO"
    )
```

```dax
Bench - Faturamento pecuário por HA (Média top indicadores) = 
CALCULATE(
    SUM(BenchmarkRecria[media_top_indicadores])
    , BenchmarkRecria[metrica] = "FATURAMENTO PECUÁRIO POR HA/ANO"
    )
```

```dax
Bench - Faturamento pecuário por HA (Média top rentáveis) = 
CALCULATE(
    SUM(BenchmarkRecria[media_top_rentaveis])
    , BenchmarkRecria[metrica] = "FATURAMENTO PECUÁRIO POR HA/ANO"
    )
```

### **Atingimento dos Benchmarks**  
```dax
Ating - Faturamento pecuário por HA (Média clientes) = 
DIVIDE(
    [Faturamento pecuário por HA]
    , [Bench - Faturamento pecuário por HA (Média clientes)]
    )
```

```dax
Ating - Faturamento pecuário por HA (Média top indicadores) = 
DIVIDE(
    [Faturamento pecuário por HA]
    , [Bench - Faturamento pecuário por HA (Média top indicadores)]
    )
```

```dax
Ating - Faturamento pecuário por HA (Média top rentáveis) = 
DIVIDE(
    [Faturamento pecuário por HA]
    , [Bench - Faturamento pecuário por HA (Média top rentáveis)]
    )
```

---

