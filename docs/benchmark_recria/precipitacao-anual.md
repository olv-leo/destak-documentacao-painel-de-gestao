# **Precipitação Anual**  

Esse valor puxa dos dados da planilha `precipitacao` e compara com os valores de benchmark.

---

## **Fórmulas DAX**
A seguir estão detalhadas todas as fórmulas DAX utilizadas.


### **Cálculo final**  
```dax
Precipitação anual = 
SUM('Preciptação'[precipitacao_total])
```

---
### **Benchmarks e Indicadores**  

#### **Médias de Benchmark**
```dax
Bench - Precipitação Anual (Média clientes) = 
CALCULATE(SUM(BenchmarkRecria[media_clientes]), 
BenchmarkRecria[metrica] = "PRECIPITAÇÃO ANUAL (mm)")
```

```dax
Bench - Precipitação Anual (Média top indicadores) = 
CALCULATE(SUM(BenchmarkRecria[media_top_indicadores]), 
BenchmarkRecria[metrica] = "PRECIPITAÇÃO ANUAL (mm)")
```

```dax
Bench - Precipitação Anual (Média top rentáveis) = 
CALCULATE(SUM(BenchmarkRecria[media_top_rentaveis]), 
BenchmarkRecria[metrica] = "PRECIPITAÇÃO ANUAL (mm)")
```

#### **Atingimento dos Benchmarks**
```dax
Ating - Precipitação Anual (Média clientes) = 
DIVIDE([Precipitação anual], [Bench - Precipitação Anual (Média clientes)])
```

```dax
Ating - Precipitação Anual (Média top indicadores) = 
DIVIDE([Precipitação anual], [Bench - Precipitação Anual (Média top indicadores)])
```

```dax
Ating - Precipitação Anual (Média top rentáveis) = 
DIVIDE([Precipitação anual], [Bench - Precipitação Anual (Média top rentáveis)])
```

---  
