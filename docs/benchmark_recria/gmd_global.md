# **GMD Global**  

---
### **Explicação do Cálculo**  
**Fórmula Matemática:**  
$$
\text{GMD Global} = \text{Média} \left( \frac{\text{Peso final} - \text{Peso inicial}}{\text{Data final} - \text{Data inicial}} \right)
$$

**Vídeo Explicativo**
<details>
  <summary>Ver explicação</summary>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/PnB4-p--9qY?si=gjOyL59-6g1JZUF_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  
</details>

---

### **Pontos Importantes**  

#### **Média do GMD**  
O **GMD Global** é a **média dos GMDs de todos os animais** no **período selecionado**. Isso significa que:

- O Power BI avalia a **primeira e a última pesagem** de cada animal **dentro do período escolhido**.
- A partir dessas pesagens, calcula-se o GMD individual dos animais.
- A média desses GMDs define o **GMD Global consolidado**.

📌 *E se um animal não tiver 2 ou mais pesagens dentro do período?*

- Se um animal tiver **apenas 1 pesagem ou nenhuma**, ele **não é considerado** no cálculo.
- Apenas os animais com **pelo menos duas pesagens** são incluídos.

---

### **Fórmulas DAX**  
Aqui estão as fórmulas DAX utilizadas no cálculo do GMD Global.  

#### **Cálculo Final**  
```dax
GMD Global = 
VAR TB_COD_ANIMAIS = DISTINCT(TodasPesagens[cod_animal])
RETURN 
AVERAGEX(
  TB_COD_ANIMAIS, 
  DIVIDE([Peso última pesagem] - [Peso primeira pesagem], 
  DATEDIFF([Primeira pesagem], [Última pesagem], DAY)))
```

---  

### **Medidas Intermediárias**  

#### **Identificação das Pesagens**
```dax
Primeira pesagem = 
MIN(TodasPesagens[data])
```

```dax
Última pesagem = 
MAX(TodasPesagens[data])
```

#### **Cálculo dos Pesos**  
```dax
Peso primeira pesagem = 
    CALCULATE(
        FIRSTNONBLANK(TodasPesagens[peso], 0),
        FILTER(
            TodasPesagens,
            TodasPesagens[data] = [Primeira pesagem] &&
            TodasPesagens[cod_animal] = SELECTEDVALUE(TodasPesagens[cod_animal])
        )
    )
```

```dax
Peso última pesagem = 
CALCULATE(
    MAX(TodasPesagens[peso]),
    FILTER(
        TodasPesagens,
        INT(TodasPesagens[data]) = [Última pesagem] && 
        TodasPesagens[cod_animal] = SELECTEDVALUE(TodasPesagens[cod_animal])
    )
)
```

#### **Cálculo de Intervalo de Dias e Contagem de Pesagens**  
```dax
Dias entre pesagem = 
DATEDIFF([Primeira pesagem], [Última pesagem], DAY)
```

```dax
Número de pesagens = 
COUNTROWS(TodasPesagens)
```

---  

### **Benchmarks e Indicadores**  

#### **Médias de Benchmark**
```dax
Bench - GMD Global (Média clientes) = 
CALCULATE(
  SUM(BenchmarkRecria[media_clientes]), 
  BenchmarkRecria[metrica] = "GMD GLOBAL (Kg)")
```

```dax
Bench - GMD Global (Média top indicadores) = 
CALCULATE(
  SUM(BenchmarkRecria[media_top_indicadores]), 
  BenchmarkRecria[metrica] = "GMD GLOBAL (Kg)")
```

```dax
Bench - GMD Global (Média top rentáveis) = 
CALCULATE(
  SUM(BenchmarkRecria[media_top_rentaveis]), 
  BenchmarkRecria[metrica] = "GMD GLOBAL (Kg)")
```

#### **Atingimento dos Benchmarks**
```dax
Ating - GMD Global (Média clientes) = 
DIVIDE([GMD Global], [Bench - GMD Global (Média clientes)])
```

```dax
Ating - GMD Global (Média top indicadores) = 
DIVIDE([GMD Global], [Bench - GMD Global (Média top indicadores)])
```

```dax
Ating - GMD Global (Média top rentáveis) = 
DIVIDE([GMD Global], [Bench - GMD Global (Média top rentáveis)])
```

---  
