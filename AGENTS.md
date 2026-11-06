# Instruções para agentes — SlothGeo

Este projeto foi solicitado em 06/11/2026 para começar somente em **21/11/2026 às 06h de America/Sao_Paulo**. O proprietário está priorizando os agentes Sofiee e Roblox. Até a data, apenas preservar a documentação; não iniciar implementação, instalar dependências, criar issues de produto ou habilitar APIs externas.

**A primeira tarefa na data de início é definir RF/RNF, sprints e todas as issues de todas as sprints planejadas, antes de implementar.** Ler docs/START_HERE.md e esclarecer dúvidas reais com Pedro antes das issues afetadas. Nenhum plano detalhado de sprints está aprovado por este bootstrap.

Leia README.md, docs/SCOPE.md, docs/ARCHITECTURE.md e docs/TOOLS_AND_INTEGRATIONS.md. A API usa o agente de Cálculo por MCP; não duplicar seu motor nem fingir integração com fixtures. Mapas, OCR e GIS têm funções diferentes; dados sem escala/referência suficientes exigem estado de insuficiência.

Somente Pedro revisa e aprova PRs. Respeite pausas e instruções posteriores. Trabalhe exclusivamente no C:, sem custos adicionais ou exposição de dados privados. A documentação é planejamento: não anuncia capacidades já funcionando.
<!-- BEGIN GOVERNANCE 2026-11-06 -->
## Regras obrigatórias de implementação e contribuição

Leia `docs/CONTRIBUTION_POLICY.md` antes de criar issues ou implementar. A instrução atual do proprietário exige issue definida → branch → alteração/validação → PR. Somente Pedro (PHnsilva) revisa e aprova PRs e dá aceite das issues; agentes não aprovam, não fazem merge/auto-merge nem deploy por conta própria. Preserve trabalho e PRs existentes.

Issues usam o formulário Entrega verificável, com requisitos/resultado, escopo, aceite, evidências, dependências direcionais, sprint e tamanho: PP=1, P=2, M=4, L=8. Aplique exatamente uma label `size:*` correspondente. No ciclo inicial são no máximo 5 sprints de entrega + 1 de validação extra e mudanças, cada uma de até uma semana; definir todas as issues do ciclo antes da implementação, após resolver dúvidas de escopo/RF/RNF/arquitetura com Pedro. Não substituir o plano existente por suposição.

Rotina ativa exige 1 L equivalente por dia por projeto, sem inflar estimativas ou alegar avanço inexistente; implementação validada e PR pronto para revisão não equivalem a aceite. Respeite pausas, datas e prioridades mais recentes. Custo adicional autorizado permanece zero. Trabalhar apenas no C:, nunca no D:.
<!-- END GOVERNANCE 2026-11-06 -->
