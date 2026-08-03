# CAC × LTV — Otimização de Investimento em Mídia

## Contexto
Projeto de analytics aplicado a uma empresa de diagnósticos de saúde de grande porte (múltiplas unidades, Brasil). Conecta **custo de aquisição (CAC)** por plataforma de mídia paga com **valor do paciente no tempo (LTV)**, para responder: *onde aumentar ou reduzir investimento?*

## Problema de negócio
Times de mídia decidem alocação de budget olhando apenas CPC/CPL — sem considerar se o paciente adquirido gera receita recorrente suficiente para pagar o custo de aquisição. Isso pode levar a cortar canais que são lucrativos no longo prazo (mas caros no curto) e manter canais baratos que trazem pacientes de baixo valor.

## Metodologia
- Pipeline SQL (BigQuery) com 5 CTEs encadeadas: custo de mídia por plataforma/marca → coorte de aquisição (com desduplicação por `QUALIFY ROW_NUMBER()` para evitar contagem dupla de pacientes) → CAC → LTV acumulado em marcos de 3/6/12/24 meses → Ratio LTV:CAC e Payback Period.
- **Correções de engenharia de dados aplicadas:** tamanho de coorte calculado antes do join com dimensão de marca (evita over-counting); LTV acumulado com `SUM() OVER (... ROWS BETWEEN UNBOUNDED PRECEDING)` particionado corretamente para não inflar o numerador/denominador.
- Semáforo de saúde: Ratio LTV:CAC 12m ≥ 3 (saudável) | ≥ 2 (atenção) | < 2 (crítico).
- Geração automática de recomendações de investimento por (plataforma × marca).

## Stack
`Python` · `pandas` · `matplotlib` · `SQL (BigQuery)` · `google-cloud-bigquery` / `bigquery-storage`

## Outputs
- Tabela CAC × LTV com marcos temporais
- Matriz Retenção × LTV por plataforma e marca
- Ranking de canais por eficiência (Ratio LTV:CAC)
- Diagnóstico de payback period

## Exemplo ilustrativo (dados fictícios)
| Plataforma | Marca | CAC | LTV 12m | Ratio LTV:CAC | Status |
|---|---|---|---|---|---|
| Paid Search | Marca A | R$ 180 | R$ 620 | 3.4x | 🟢 Saudável |
| Paid Social | Marca B | R$ 145 | R$ 210 | 1.4x | 🔴 Crítico |

*Números meramente ilustrativos — não representam dados reais de nenhuma empresa.*

## So What?
Identificar combinações (plataforma × marca) com Ratio LTV:CAC abaixo de 2x permite realocar budget para canais com retorno comprovado no longo prazo, em vez de otimizar apenas por custo de aquisição imediato.
