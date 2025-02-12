# **Mortalidade de Animais Adultos**  

## **Descrição**  
Este documento detalha o cálculo da taxa de mortalidade de animais adultos, incluindo a explicação da fórmula, pontos de atenção e as medidas DAX utilizadas para a análise.

---

## **Explicação do Cálculo**  

### **Fórmula Matemática:**  
$$
\text{Mortalidade animais adultos} = \frac{\text{Número de mortes animais adultos}}{\text{Número de animais adultos}}
$$

### **Vídeo Explicativo**  
<details>
  <summary>Ver explicação</summary>
<iframe width="560" height="315" src="https://www.youtube.com/embed/insn992_7Y8?si=X_hWgM346a20b2GY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</details>

---

## **Pontos de Atenção**  

### **Definição de Animais Adultos**  
Um animal adulto é aquele que não está classificado como **BEZERRO** ou **BEZERRA**. Para essa classificação, consideramos o último registro de categoria antes da morte do animal. Caso o animal tenha sido desmamado, ele já é considerado adulto.

---

## **Fórmulas DAX**  
Abaixo estão todas as fórmulas DAX utilizadas na análise.

### **Cálculo Final**  
```dax
Mortalidade animais adultos =
DIVIDE([Mortes animais adultos], [Número animais adultos])
```

### **Medidas Intermediárias**  
```dax
Mortes animais adultos =
CALCULATE(
    COUNTROWS(TodasMovimentacoes),
    TodasMovimentacoes[categoria] <> "BEZERRO",
    TodasMovimentacoes[categoria] <> "BEZERRA",
    TodasMovimentacoes[origem] = "mortes"
)
```

```dax
Número animais adultos =
CALCULATE(
    DISTINCTCOUNT(TodasMovimentacoes[cod_animal]),
    TodasMovimentacoes[categoria] <> "BEZERRO",
    TodasMovimentacoes[categoria] <> "BEZERRA"
)
```

---

## **Benchmarks e Indicadores**  

### **Médias de Benchmark**  
```dax
Bench - Mortalidade animais adultos (Média clientes) =
CALCULATE(
    SUM(BenchmarkRecria[media_clientes]),
    BenchmarkRecria[metrica] = "MORTALIDADE ANIMAIS ADULTOS"
)
```

```dax
Bench - Mortalidade animais adultos (Média top indicadores) =
CALCULATE(
    SUM(BenchmarkRecria[media_top_indicadores]),
    BenchmarkRecria[metrica] = "MORTALIDADE ANIMAIS ADULTOS"
)
```

```dax
Bench - Mortalidade animais adultos (Média top rentáveis) =
CALCULATE(
    SUM(BenchmarkRecria[media_top_rentaveis]),
    BenchmarkRecria[metrica] = "MORTALIDADE ANIMAIS ADULTOS"
)
```

### **Atingimento dos Benchmarks**  
```dax
Ating - Mortalidade animais adultos (Média clientes) =
DIVIDE(
    [Mortalidade animais adultos],
    [Bench - Mortalidade animais adultos (Média clientes)]
)
```

```dax
Ating - Mortalidade animais adultos (Média top indicadores) =
DIVIDE(
    [Mortalidade animais adultos],
    [Bench - Mortalidade animais adultos (Média top indicadores)]
)
```

```dax
Ating - Mortalidade animais adultos (Média top rentáveis) =
DIVIDE(
    [Mortalidade animais adultos],
    [Bench - Mortalidade animais adultos (Média top rentáveis)]
)
```

---

