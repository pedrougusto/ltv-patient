# Análise de Retorno/Churn de Pacientes por Múltiplos Cortes

## Contexto
Análise de churn para uma empresa de diagnósticos de saúde, respondendo qual canal, campanha, produto, tipo de convênio e faixa etária mais fideliza ou mais perde pacientes.

## Pergunta de negócio
Onde o churn é concentrado? Quais campanhas/produtos/operadoras merecem atenção prioritária de retenção?

## Metodologia
- Classificação de pacientes em categorias de retorno (ex.: retornou rápido, retornou tardio, sem retorno).
- Distribuição percentual por canal de aquisição, por campanha (Top 20 + "Outros"), por grupo de exames (produto), por operadora e por faixa etária.
- Gráficos de barras empilhadas (100%) ordenados pela taxa de "sem retorno", para priorização visual imediata.

## Stack
`Python` · `pandas` · `matplotlib`

## So What?
Ordenar cada corte pela taxa de churn permite identificar rapidamente os "piores ofensores" (ex.: uma campanha específica ou grupo de exames com churn muito acima da média) para ação direcionada — em vez de tratar retenção como problema genérico.
