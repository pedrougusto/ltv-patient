# Heatmaps de Coorte — Retenção de Pacientes

## Contexto
Análise de retenção mês a mês para uma empresa de diagnósticos de saúde, cobrindo coortes de aquisição por canal digital e por subcanal (ex.: mídia paga de busca).

## Pergunta de negócio
Quanto tempo um paciente adquirido em um canal específico continua retornando? A retenção varia por canal de aquisição?

## Metodologia
- Query BigQuery que constrói a coorte de aquisição, calcula meses desde a aquisição e a taxa de retenção mês a mês.
- Heatmap (matriz coorte × mês) para visualizar rapidamente onde a retenção cai — separado por canal Digital e por subcanal Paid Search.
- Transformações downstream feitas 100% em pandas a partir de um único carregamento de dados (sem queries redundantes).

## Stack
`Python` · `pandas` · `matplotlib` (heatmap) · `SQL (BigQuery)`

## So What?
O heatmap expõe visualmente em qual mês específico a maior parte da coorte deixa de retornar — informação que orienta em qual momento do ciclo de vida (ex.: mês 2 ou 3) vale a pena investir em campanhas de reativação.
