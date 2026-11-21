# SlothGeo

API de medição e análise geométrica de terrenos, combinando ferramentas de geometria/geoprocessamento, entradas documentais e integrações Google Maps com o agente de Cálculo da linha Sofiee.

**Estado em 21/11/2026: preparação de casos de uso, requisitos derivados e organização inicial do trabalho para revisão de Pedro. Nenhuma API, extração visual ou integração está implementada.** O horário autorizado mais recente é 04h30 de America/Sao_Paulo. A orientação atual prioriza a base de planejamento; Pedro dará instruções posteriores para melhorá-la.

## Planejamento inicial em revisão

1. [Casos de uso — atores, fluxos e exceções](docs/USE_CASES.md)
2. [RF/RNF derivados dos UC](docs/REQUIREMENTS.md)
3. [Decisões abertas para refinamento](docs/DECISIONS.md)
4. [Organização inicial e rastreabilidade](docs/INITIAL_PLAN.md)
5. [Estado da rodada e próxima ação](docs/PROGRESS.md)

[Projects inicial](https://github.com/users/PHnsilva/projects/14) · [Issues de preparação e refinamento](https://github.com/PHnsilva/SlothGeo/issues)

A base inicial não significa aprovação do ciclo de produto. Issues de implementação afetadas por dúvidas e o planejamento completo das sprints aguardam o refinamento com Pedro.

O projeto foi preparado em 06/11/2026 por solicitação de Pedro. Após o refinamento dos UC/requisitos e das decisões abertas com ele, será necessário criar todas as issues de todas as sprints do ciclo (até 5 + 1, semanais), com tamanhos, dependências, aceite e Kanban. Somente depois dessa preparação completa poderá haver implementação por issue/branch/PR; Pedro revisa e aprova os PRs. A preparação documental original foi a exceção autorizada de bootstrap; a rodada atual segue a issue #1 em branch própria.

## Leitura para retomada

1. [AGENTS.md](AGENTS.md)
2. [Escopo inicial](docs/SCOPE.md)
3. [Arquitetura e responsabilidades](docs/ARCHITECTURE.md)
4. [Ferramentas e integrações](docs/TOOLS_AND_INTEGRATIONS.md)
5. [Roteiro de início e decisões](docs/START_HERE.md)
6. [Regras de contribuição](docs/CONTRIBUTION_POLICY.md)

O núcleo deve calcular com dados suficientes, explicar método/unidades/referência e retornar incerteza ou insuficiência quando necessário. Não prometer medir qualquer terreno a partir de qualquer foto sem escala. Google Maps é um provedor de dados/apresentação, não uma fonte automática dos limites corretos de uma propriedade.

Dependência planejada: [sofiee-agent-calculation](https://github.com/PHnsilva/sofiee-agent-calculation), consumido por cliente MCP no SlothGeo. Sem criar outro repositório MCP nem duplicar o motor matemático no produto. Busca e Validação podem ser consumidos quando houver necessidade e contrato definido; não são dependências obrigatórias de toda medição.

Cópia local: `C:\Users\peecs\Documents\ChatGPT\SlothGeo`. Dados e ferramentas ficam no C:. Não publicar credenciais, plantas privadas, coordenadas pessoais ou dados de clientes. Nenhuma chave Google, faturamento ou chamada paga foi habilitada.
