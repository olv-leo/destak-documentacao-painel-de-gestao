# **GMD MÉDIO**  
Avalie o ganho médio de peso dos animais do rebanho nas últimas 2 pesagens.

---

### **Explicação do Cálculo**  
![Imagem do cálculo: GMD Médio ](assets\gmd_medio.png)


Explicacao calculo 

**Fórmula Matemática:**  
$$
\text{gmd_medio} =\frac{(\text{peso_ult_pesagem - peso_penultima_pesagem})}{\text{(data_ult_pesagem - data_penultima_pesagem)}}
$$



**Vídeo Explicativo**

<details>
  <summary>Ver explicação em vídeo</summary>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/U9wv1_mwHhI?si=F6COFKjhEOmxrscn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</details>
</br>


### **Fórmulas DAX**
A seguir estão detalhadas todas as fórmulas DAX utilizadas.


#### Cálculo final
```dax
GMD Médio = AVERAGE('CalcInfosAnimais'[cc_gmd_atual])
```

---
#### Etapas do cálculo
**1. Data penúltima pesagem**  

```dax
cc_data_penultima_pesagem = 
VAR COD_CL = 'CalcInfosAnimais'[cod_animal]
VAR DATA_ULT_PESAGEM = 'CalcInfosAnimais'[cc_data_ult_pesagem]

RETURN 
CALCULATE(
    MAX('CalcAtividadeAnimai'[data]),
    FILTER(
        'CalcAtividadeAnimai',
        'CalcAtividadeAnimai'[cod_animal] = COD_CL &&
        ISNUMBER('CalcAtividadeAnimai'[peso]) &&
        'CalcAtividadeAnimai'[data] < DATA_ULT_PESAGEM))
```
**2. Peso penúltima pesagem**  

```dax
cc_peso_penultima_pesagem = 
VAR COD_CL = 'CalcInfosAnimais'[cod_animal]
VAR DATA_PENULT_PESAGEM_CL = 'CalcInfosAnimais'[cc_data_penultima_pesagem]

RETURN 
CALCULATE(
    MAX('CalcAtividadeAnimai'[peso]),
    FILTER(
        'CalcAtividadeAnimai',
        'CalcAtividadeAnimai'[cod_animal] = COD_CL &&
        ISNUMBER('CalcAtividadeAnimai'[peso]) &&
        'CalcAtividadeAnimai'[data] = DATA_PENULT_PESAGEM_CL))
```
**3. Data última pesagem**  

```dax
cc_data_ult_pesagem = 
VAR COD_CL = 'CalcInfosAnimais'[cod_animal]

RETURN 
CALCULATE(
    MAX('CalcAtividadeAnimai'[data]),
    FILTER(
        'CalcAtividadeAnimai',
        'CalcAtividadeAnimai'[cod_animal] = COD_CL 
        && ISNUMBER('CalcAtividadeAnimai'[peso]))
)
```
**4. Peso última pesagem**  

```dax
cc_peso_ult_pesagem = 
VAR COD_CL = 'CalcInfosAnimais'[cod_animal]
VAR DATA_ULT_PESAGEM_CL = 'CalcInfosAnimais'[cc_data_ult_pesagem]

RETURN 
CALCULATE(
    MAX('CalcAtividadeAnimai'[peso]),
    FILTER(
        'CalcAtividadeAnimai',
        'CalcAtividadeAnimai'[cod_animal] = COD_CL &&
        ISNUMBER('CalcAtividadeAnimai'[peso]) &&
        'CalcAtividadeAnimai'[data] = DATA_ULT_PESAGEM_CL))

```
**5. Cálculo do GMD por animal**  

```dax
cc_gmd_atual = 
SWITCH(
    TRUE()
    ,OR(ISBLANK('CalcInfosAnimais'[cc_peso_ult_pesagem]), ISBLANK('CalcInfosAnimais'[cc_peso_penultima_pesagem])), BLANK()
    ,DIVIDE(([cc_peso_ult_pesagem] - [cc_peso_penultima_pesagem]), ([cc_data_ult_pesagem] - [cc_data_penultima_pesagem]), BLANK()))
```


