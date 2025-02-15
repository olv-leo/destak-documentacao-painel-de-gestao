# **Custo por Cabeça**  

## **Descrição**  
Este documento detalha o cálculo do custo por cabeça, incluindo a explicação da fórmula, pontos de atenção e medidas DAX utilizadas para a análise.

---

## **Explicação do Cálculo**  

### **Fórmula Matemática**  
$$
\text{Custo por Cabeça} = \text{Média} \left( \frac{\text{Custo Mensal}}{\text{Quantidade de Animais}} \right)
$$

### **Vídeo Explicativo**  
<details>
  <summary>Ver explicação</summary>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/7o45jziJ26A?si=hS6tki3fqTu3xlQP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</details>

---

## **Pontos de Atenção**  

### **Custo Mensal**  
Ao considerar um período superior a um mês, o custo mensal utilizado é a média do custo dos meses que compõem o período. Por exemplo:

| Ano/Mês | Valor (R$) |
|----------|-----------|
| 2025-01  | 500       |
| 2025-02  | 350       |
| 2025-03  | 480       |

O custo total considerado será a média dos custos nesses 3 meses:
$$
(500 + 350 + 480) / 3 = 443,33
$$

### **Quantidade de Animais**  
- Para um mês específico, considera-se o total de animais ativos no período.
- Para um período maior que um mês, utiliza-se o total de animais distintos que existiram ao longo desse período.

---

## **Fórmulas DAX**  

### **Cálculo Final**  
```dax
Custo por cabeça =
DIVIDE([Custo médio mensal], [Número de cabeças])
```

### **Medidas Intermediárias**  
```dax
Custo médio mensal =
VAR TotalCusto =
    CALCULATE(
        SUM(MovimentacoesFinanceiras[valor_pagamento]),
        MovimentacoesFinanceiras[classificacao] = "DESPESAS"
    )
VAR DistinctMonths =
    DISTINCTCOUNT('Calendário'[ano_mes])

RETURN
    DIVIDE(TotalCusto, DistinctMonths)
```

```dax
Número de cabeças =
DISTINCTCOUNT(PesoPorAnimalPorMes[cod_animal])
```

---

## **Benchmarks e Indicadores**  

### **Médias de Benchmark**  
```dax
Bench - Custo por cabeça (Média clientes) =
CALCULATE(
    SUM(BenchmarkRecria[media_clientes]),
    BenchmarkRecria[metrica] = "CUSTEIO CAB/MÊS")
```

```dax
Bench - Custo por cabeça (Média top indicadores) =
CALCULATE(
    SUM(BenchmarkRecria[media_top_indicadores]),
    BenchmarkRecria[metrica] = "CUSTEIO CAB/MÊS")
```

```dax
Bench - Custo por cabeça (Média top rentáveis) =
CALCULATE(
    SUM(BenchmarkRecria[media_top_rentaveis]),
    BenchmarkRecria[metrica] = "CUSTEIO CAB/MÊS")
```

### **Atingimento dos Benchmarks**  
```dax
Ating - Custo por cabeça (Média clientes) =
DIVIDE(
    [Custo por cabeça],
    [Bench - Custo por cabeça (Média clientes)])
```

```dax
Ating - Custo por cabeça (Média top indicadores) =
DIVIDE(
    [Custo por cabeça],
    [Bench - Custo por cabeça (Média top indicadores)])
```

```dax
Ating - Custo por cabeça (Média top rentáveis) =
DIVIDE(
    [Custo por cabeça],
    [Bench - Custo por cabeça (Média top rentáveis)])
```

---

