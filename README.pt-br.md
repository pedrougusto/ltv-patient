# Matriz Retenção × LTV e Simulador de Impacto de CRM

## Contexto
O projeto mais avançado da série: além da matriz Retenção × LTV por canal, subcanal, marca e grupo de exames, inclui uma camada de decisão sobre onde investir em CRM (retenção) versus mídia paga (aquisição).

## Pergunta de negócio
Vale mais a pena investir em reter pacientes existentes (CRM) ou em adquirir novos (mídia paga)? Em qual mês do ciclo de vida a intervenção de CRM tem mais impacto?

## Metodologia
- **Matriz Retenção × LTV**: posiciona cada segmento (canal, subcanal, marca, grupo de exames) em dois eixos — taxa de retenção e valor do paciente — para identificar quadrantes de alta prioridade.
- **Decomposição de LTV**: LTV = Ticket Médio × Frequência Anual × Retenção (anos), permitindo isolar qual componente está puxando o LTV para baixo em cada segmento.
- **Early Drop-off**: classifica coortes em "voltou" vs. "sumiu" nos primeiros 4 meses e calcula a diferença de LTV entre os dois grupos — quantifica o custo de não reter cedo.
- **Simulador de Impacto de CRM**: usa os números reais da análise de early drop-off para estimar o ganho de receita de converter uma fração dos pacientes "sumidos" em "retornados".
- **Janela Ótima de Reativação**: identifica em qual mês os pacientes tendem a voltar naturalmente, por subcanal — para calibrar o timing de campanhas de reativação.
- **Slope Analysis**: compara a velocidade marginal de ganho de LTV entre CRM e mídia paga ao longo dos meses — mídia paga captura valor imediato (pico em M0), CRM tem efeito retardado mas sustentável (pico em M3), evidência numérica para justificar investimento em retenção de médio prazo.

## Stack
`Python` · `pandas` · `matplotlib` · `numpy` · `SQL (BigQuery)`

## So What?
Este projeto transforma retenção de um KPI descritivo em uma alavanca de decisão de investimento: quantifica, em receita, o ganho esperado de uma iniciativa de CRM comparado ao custo de aquisição via mídia paga — permitindo priorizar orçamento entre "reter" e "adquirir" com base em evidência, não em intuição.
