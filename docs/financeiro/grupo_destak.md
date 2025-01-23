# **GRUPO DESTAK**
Essa página explica como os lançamentos realizados na planilha `financeiro` com a `fazenda` `GRUPO DESTAK` são tratados pelo Power BI.  

Os lançamentos realizados na guia `financeiro` que estiverem na `fazenda` `GRUPO DESTAK` lançados como `SAÍDAS` tem seu valor distribuído igualmente entre as fazendas do grupo.  


**EXEMPLO DE FUNCIONAMENTO**


Imagine o seguinte lançamento: 

| **data_nota** | **data_vencimento** | **data_pagamento** | **fazenda** | **desc_lancamento** | **forma_pgto** | **banco** | **valor_pagamento** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 11/12/2023 | 11/12/2023 | 11/12/2023 | GRUPO DESTAK | FRETE CARGILL | PIX | CAIXA | R$ 31.882,27 |

Esse lançamento deve ser distribuído entre as 5 fazendas, ou seja, essa uma linha de lançamento deve ser convertido no seguinte:

| **data_nota** | **data_vencimento** | **data_pagamento** | **fazenda** | **desc_lancamento** | **forma_pgto** | **banco** | **valor_pagamento** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 11/12/2023 | 11/12/2023 | 11/12/2023 | AURORA | FRETE CARGILL | PIX | CAIXA | R$ 6.376,45 |
| 11/12/2023 | 11/12/2023 | 11/12/2023 | DESTAK | FRETE CARGILL | PIX | CAIXA | R$ 6.376,45 |
| 11/12/2023 | 11/12/2023 | 11/12/2023 | MORADA NOVA | FRETE CARGILL | PIX | CAIXA | R$ 6.376,45 |
| 11/12/2023 | 11/12/2023 | 11/12/2023 | PARAÍSO | FRETE CARGILL | PIX | CAIXA | R$ 6.376,45 |
| 11/12/2023 | 11/12/2023 | 11/12/2023 | SANTA BÁRBARA | FRETE CARGILL | PIX | CAIXA | R$ 6.376,45 |

