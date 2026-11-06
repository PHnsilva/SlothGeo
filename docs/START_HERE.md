# Começar aqui em 21/11/2026

## Antes da data

Somente guardar/consultar a preparação documental. Não iniciar código, instalar bibliotecas, criar o backlog de produto, ativar serviços ou publicar. Este projeto não deve consumir a rotina dos cinco agentes nem do Roblox.

## Primeira retomada autorizada — 21/11/2026 às 06h, São Paulo

1. Ler AGENTS, README, SCOPE, ARCHITECTURE, TOOLS_AND_INTEGRATIONS e CONTRIBUTION_POLICY. Conferir instruções mais recentes de Pedro e a configuração real da rotina; não duplicar agendamentos.
2. Inventariar ambiente do C:, dependências existentes, estado do repositório e capacidades reais do agente de Cálculo. Não usar D:.
3. Definir RF/RNF rastreáveis, operações/formatos suportados e contratos de dados/erros. Esclarecer com Pedro decisões que ainda alterem o escopo ou custo antes de criar as issues afetadas.
4. Definir no máximo 5 sprints de entrega + 1 de validação/mudanças, de até uma semana cada, dimensionadas pela capacidade de 1 L equivalente por projeto/dia. A sexta sprint não dispensa validar desde a primeira.
5. **Criar todas as issues de todas as sprints planejadas antes de implementar produto.** Cada uma com escopo, critérios de aceite, validação, dependências e tamanho PP/P/M/L com justificativa e label correspondente. Reconciliar duplicatas e criar/organizar um Kanban real; não anunciar quadro configurado antes de conferir.
6. Priorizar contrato/integração com o Cálculo e núcleo com coordenadas verificáveis antes de sofisticar OCR e mapas. Diagramar fronteiras e registrar a origem da medição.
7. Implementar somente a primeira entrega pronta e desbloqueada, em branch/PR. Revisão e aprovação de PR são exclusivamente de Pedro. Registrar resultado, evidência, limites, bloqueios e próxima ação.

## Decisões a fechar no início

- Formatos e limites de entrada (número de vértices, furos, arquivos, unidades/CRS), precisão e tolerâncias por método.
- Contrato MCP real do Cálculo, disponibilidade do servidor e responsabilidades de transformação/geometria.
- Granularidade do fluxo assistido de imagem: o que é extraído, o que o usuário confirma, e quais escalas/referências são exigidas.
- Google Maps: produtos necessários, chave/cotas e autorização de custo; estratégia de teste sem dependência paga.
- Autenticação, retenção/descarte de documentos, implantação e disponibilidade. Sem banco obrigatório até existir requisito.
- Objetivos mensuráveis de latência, tamanho, precisão e robustez e casos de referência públicos/sintéticos.

Não confundir pendência de contrato com motivo para substituir silenciosamente o agente de Cálculo por uma implementação duplicada. Não criar um escopo de fotogrametria/3D por antecipação.
