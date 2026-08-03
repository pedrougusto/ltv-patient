# Curvas de LTV Acumulado por Canal, Subcanal e Tipo de Pagamento

## Contexto
Conjunto de notebooks/scripts que geram curvas de LTV acumulado (receita acumulada por paciente ao longo dos meses desde a aquisição) para uma empresa de diagnósticos de saúde, com recortes por canal de aquisição, subcanal e tipo de pagamento (convênio vs. particular).

## Pergunta de negócio
Como o valor do paciente evolui ao longo do tempo, e essa evolução muda dependendo de onde ele foi adquirido ou como ele paga?

## Metodologia
- Query BigQuery: coorte de aquisição (primeiro atendimento como "novo", com `QUALIFY ROW_NUMBER()` para evitar duplicidade), receita mensal por paciente, receita acumulada via window function, e LTV médio por paciente = receita acumulada / tamanho da coorte.
- Segmentação por tipo de pagamento capturada no momento da aquisição (metodologia documentada explicitamente no código para evitar ambiguidade: o tipo de pagamento pode mudar ao longo da vida do paciente, mas a coorte é definida pelo tipo de pagamento na aquisição).
- Funções reutilizáveis de agregação e plotagem, com anotação automática do valor final de cada curva.

## Stack
`Python` · `pandas` · `matplotlib` · `SQL (BigQuery)`

## So What?
Curvas de LTV por tipo de pagamento revelam se pacientes de convênio e particular têm trajetórias de valor divergentes — informação relevante para precificação, priorização de canal e estratégia comercial por segmento.
