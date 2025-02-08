# **Lotação do Pasto (UA/HA)**  

---
### **Explicação do Cálculo**  
**Fórmula Matemática:**  
$$
\text{Lotação do Pasto} = \frac{\left(\frac{\text{Peso do Rebanho}}{\text{UA}}\right)}{\text{HA}}
$$


**Vídeo Explicativo**
<details>
  <summary>Ver explicação</summary>
<iframe width="560" height="315" src="https://www.youtube.com/embed/wJrcgFslJkE?si=QsNAuiwqRss3TjLX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</details>
</br>



### **Pontos importantes:**  

#### **Peso do Rebanho**  
O valor do peso do rebanho varia de acordo com o contexto:  

- **Mensal:** Representa a soma do ÚLTIMO peso registrado de todos os animais que estavam no rebanho naquele mês.  
- **Anual:** Corresponde à média dos pesos mensais ao longo do ano.  
- **Geral:** Representa a média dos pesos mensais durante o período selecionado.  

#### **Unidade Animal (UA)**  
Consideramos o valor da UA igual a **450 kg**.  

### **Fórmulas DAX**  
A seguir estão detalhadas todas as fórmulas DAX utilizadas.  

#### **Cálculo final**  
```dax
Lotação Pasto = [UA] / [HA]
```  

---  

#### **Medidas intermediárias**  

```dax
Peso Médio por Mês = 
VAR ANOMES_FILTRADO = DISTINCTCOUNT('PesoPorAnimalPorMes'[ano_mes])
VAR PESO = SUM('PesoPorAnimalPorMes'[peso])

RETURN 
    IF(
        ANOMES_FILTRADO = 1, 
        PESO, 
        DIVIDE(PESO, ANOMES_FILTRADO, 0)
    )
```  

```dax
Const - UA = 450
```  

```dax
UA = [Peso Médio por Mês] / [Const - UA]
```  

```dax
HA = SUM(Fazendas[area_ha])
```  

```dax
Bench - Lotação Pasto UA/HA (Média clientes) = CALCULATE(SUM(BenchmarkRecria[media_clientes]), BenchmarkRecria[metrica] = "LOTAÇÃO PASTO UA/HA")
```  

```dax
Bench - Lotação Pasto UA/HA (Média top indicadores) = CALCULATE(SUM(BenchmarkRecria[media_top_indicadores]), BenchmarkRecria[metrica] = "LOTAÇÃO PASTO UA/HA")
```  

```dax
Bench - Lotação Pasto UA/HA (Média top rentáveis) = CALCULATE(SUM(BenchmarkRecria[media_top_rentaveis]), BenchmarkRecria[metrica] = "LOTAÇÃO PASTO UA/HA")
```  

```dax
Ating - Lotação Pasto UA/HA (Média clientes) = DIVIDE([Lotação Pasto], Medidas[Bench - Lotação Pasto UA/HA (Média clientes)])
```  

```dax
Ating - Lotação Pasto UA/HA (Média top indicadores) = DIVIDE([Lotação Pasto], Medidas[Bench - Lotação Pasto UA/HA (Média top indicadores)])
```  

```dax
Ating - Lotação Pasto UA/HA (Média top rentáveis) = DIVIDE([Lotação Pasto], Medidas[Bench - Lotação Pasto UA/HA (Média top rentáveis)])
```  
