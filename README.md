# SlothGeo

API de medição e análise geométrica de terrenos, combinando ferramentas de geometria/geoprocessamento, entradas documentais e integrações Google Maps com o agente de Cálculo da linha Sofiee.

**Estado: somente escopo e documentação inicial. Nenhuma API, extração visual ou integração está implementada. Início autorizado: 21/11/2026 às 06h, America/Sao_Paulo. Até lá não implementar, instalar dependências, criar o backlog de produto ou ativar serviços externos.**

O projeto foi preparado em 06/11/2026 por solicitação de Pedro. Na retomada, a primeira tarefa é definir RF/RNF, resolver decisões abertas e criar todas as issues de todas as sprints do ciclo (até 5 + 1, semanais), com tamanhos, dependências, aceite e Kanban. Depois, implementar por issue/branch/PR; somente Pedro revisa e aprova PRs. A preparação documental inicial é a exceção autorizada de bootstrap.

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
