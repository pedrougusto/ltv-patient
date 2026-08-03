# Caminhos Mais Rentáveis de Aquisição de Novos Pacientes

## Contexto
Análise para uma empresa de diagnósticos de saúde de grande porte, com três variantes de segmentação: todos os canais, com detalhamento de operadora/convênio, e visão consolidada.

## Pergunta de negócio
Qual é o caminho (combinação canal → subcanal → campanha → operadora/produto) que traz o paciente novo mais rentável? Onde concentrar esforço de aquisição?

## Metodologia
- Leitura e limpeza de base de atendimentos, com deduplicação por paciente e tratamento de valores nulos/categorias "Não identificado".
- Construção de combinações completas (canal × subcanal × ... × operadora) e ranking Top 20 por volume e por receita.
- Funções de visualização reutilizáveis para inspeção rápida e comparação entre cortes.

## Stack
`Python` · `pandas` · `matplotlib` · `SQL (BigQuery)`

## So What?
Ao invés de decidir investimento por canal isolado, o ranking de combinações completas revela nichos de alta rentabilidade (ex.: um subcanal específico cruzado com um tipo de convênio) que ficariam escondidos em análises agregadas por canal.
