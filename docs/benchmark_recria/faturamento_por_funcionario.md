# **Faturamento por Funcionário**  

---
### **Explicação do Cálculo**  
**Fórmula Matemática:**  
$$
\text{Faturamento por funcionário} = \frac{\text{Faturamento}}{\text{Número de funcionários}}
$$


**Vídeo Explicativo**
<details>
  <summary>Ver explicação</summary>
<iframe width="560" height="315" src="https://www.youtube.com/embed/465u9RC0Sb8?si=BtrNuqAHNF-L8WNq" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</details>
</br>

### **Fórmulas DAX**  
A seguir estão detalhadas todas as fórmulas DAX utilizadas.  

#### **Cálculo final**  
```dax
Faturamento por funcionário = DIVIDE([Faturamento], [Número de funcionários])
```  

---  

#### **Medidas intermediárias**  

```dax
Faturamento = CALCULATE(SUM(MovimentacoesFinanceiras[valor_pagamento]), MovimentacoesFinanceiras[classificacao] = "RECEITAS")
```  

```dax
Número de funcionários = SUM(Fazendas[num_funcionarios])
```  

```dax
Faturamento por funcionário = DIVIDE([Faturamento], [Número de funcionários])
```  

```dax
HA = SUM(Fazendas[area_ha])
```  

```dax
Bench - Faturamento/Funcionário (Média clientes) = CALCULATE(SUM(BenchmarkRecria[media_clientes]), BenchmarkRecria[metrica] = "FATURAMENTO/FUNCIONÁRIOS")
```  

```dax
Bench - Faturamento/Funcionário (Média top indicadores) = CALCULATE(SUM(BenchmarkRecria[media_top_indicadores]), BenchmarkRecria[metrica] = "FATURAMENTO/FUNCIONÁRIOS")
```  

```dax
Bench - Faturamento/Funcionário (Média top rentáveis) = CALCULATE(SUM(BenchmarkRecria[media_top_rentaveis]), BenchmarkRecria[metrica] = "FATURAMENTO/FUNCIONÁRIOS")
```  

```dax
Ating - Faturamento/Funcionário (Média clientes) = DIVIDE([Faturamento por funcionário], [Bench - Faturamento/Funcionário (Média clientes)])
```  

```dax
Ating - Faturamento/Funcionário (Média top indicadores) = DIVIDE([Faturamento por funcionário], [Bench - Faturamento/Funcionário (Média top indicadores)])
```  

```dax
Ating - Faturamento/Funcionário (Média top rentáveis) = DIVIDE([Faturamento por funcionário], [Bench - Faturamento/Funcionário (Média top rentáveis)])
```  
