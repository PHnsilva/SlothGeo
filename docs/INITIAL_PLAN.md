# Organização inicial — UC → requisitos → Projects → issues

Versão de trabalho de 21/11/2026. [Issue #1](https://github.com/PHnsilva/SlothGeo/issues/1), tamanho **M = 4**, estado **pré-planejamento**. O objetivo desta rodada é uma base revisável conforme a orientação mais recente de Pedro. Não iniciar produto nem apresentar o ciclo completo como aprovado.

## Sequência e condições

1. Descrever [casos de uso](USE_CASES.md) a partir do escopo existente.
2. Derivar [RF/RNF](REQUIREMENTS.md), mantendo a origem e o critério de verificação.
3. Preparar o Projects inicial e conferir a organização existente antes de criar algo.
4. Criar issues iniciais de refinamento com resultado documental e decisão específica, sem antecipar implementação afetada por dúvida.
5. Incorporar as próximas orientações de Pedro; só depois decompor o ciclo completo e suas issues de produto.

## Quadro e backlog

[Projects nº 14 — SlothGeo — Planejamento inicial](https://github.com/users/PHnsilva/projects/14), criado na conta PHnsilva, com visibilidade privada preservada. A conferência dos itens e estados finais desta rodada será registrada em PROGRESS.md.

Estados configurados e conferidos após recarregar o quadro: **Backlog → Pronto → Em andamento → Em revisão → Em validação → Concluído**. Bloqueio informa condição e responsável; não é confundido com aceite. Nenhuma issue será concluída sem aceite de Pedro. Não há campo de tamanho ou sprint criado nesta base; o tamanho está no título/corpo e em exatamente uma label `size:*`; todas as issues iniciais declaram pré-planejamento.

| Issue | Entrega documental inicial | Tamanho | Decisões/artefatos consumidos |
| --- | --- | --- | --- |
| [#1](https://github.com/PHnsilva/SlothGeo/issues/1) | Preparar UC, requisitos e organização inicial | M = 4 | Escopo e orientação de 21/11; a versão preparada é submetida a revisão. |
| [#2](https://github.com/PHnsilva/SlothGeo/issues/2) | Refinar entradas, geometria e precisão | M = 4 | D01/D02; orientações de Pedro. |
| [#3](https://github.com/PHnsilva/SlothGeo/issues/3) | Definir contrato geoespacial MCP | M = 4 | D03; capacidades reais do Cálculo e fronteiras. |
| [#4](https://github.com/PHnsilva/SlothGeo/issues/4) | Refinar OCR, confirmação e calibração | M = 4 | D04, interfaces D02/D05. |
| [#5](https://github.com/PHnsilva/SlothGeo/issues/5) | Definir acesso, privacidade e metas operacionais | M = 4 | D05/D07, compatibilidade com limites das entradas/MCP. |
| [#6](https://github.com/PHnsilva/SlothGeo/issues/6) | Delimitar mapas/localização com custo adicional zero | P = 2 | D06; mapas reais continuam sem autorização de ativação. |
| [#7](https://github.com/PHnsilva/SlothGeo/issues/7) | Consolidar ciclo completo após o refinamento | M = 4 | D08; bloqueada por #2, #3, #4, #5 e #6, consumindo as decisões registradas. |

As dependências da #7 foram registradas também na relação nativa do GitHub, além do texto legível. A #1 produz a base inicial; não é bloqueio artificial por merge para consultar documentos disponíveis. As issues de refinamento aguardam as próximas orientações, sem compromisso de implementação. A soma de 26 unidades é uma estimativa desse backlog documental, não pontos entregues nem capacidade de uma sprint de produto.

## Matriz inicial de cobertura

| Casos de uso | Requisitos derivados | Refinamento necessário | Issues de refinamento |
| --- | --- | --- | --- |
| UC-01 | RF-01/02/05/07/08/09; RNF-01/02/04/05/06/07/08/09 | D01/D02/D03/D07 | #2, #3, #5 |
| UC-02 | RF-01/03/05/06/07/08/09; RNF-01/02/04/05/06/07/08/09 | D01/D02/D03/D07 | #2, #3, #5 |
| UC-03 | RF-01/04/05/06/07/08/09; RNF-01/02/04/05/06/07/08/09 | D01/D02/D03/D07 | #2, #3, #5 |
| UC-04 | RF-05/09/11/16; RNF-02/03/06/07/08 | D03/D04/D05/D07 | #3, #4, #5 |
| UC-05 | RF-05/06/08/09/12/16; RNF-02/03/04/05/06/07/08 | D02/D03/D04/D05/D07 | #2, #3, #4, #5 |
| UC-06 | RF-09/13; RNF-01/02/06/07/08/09 | D01/D02/D03/D06/D07 | #2, #3, #5, #6 |
| UC-07 | RF-05/09/14; RNF-01/03/07/08 | D05/D06; inclusão condicional | #5, #6 |
| UC-08 | RF-07/08/09/10; RNF-03/04/05/07/08 | D02/D03/D05 | #2, #3, #5 |
| UC-09 | RF-01/07/09/15/16; RNF-01–10 | D01–D07 | #2, #3, #4, #5, #6 |

Esta matriz comprova origem e cobertura documental inicial, não cobertura implementada. Cada issue de refinamento aponta seus UC, requisitos e decisões. A #7 auditará a decomposição de produto depois das orientações, sem substituir as entregas reais por uma issue genérica.

| Requisitos que precisam de especificação | Issue que detalha o critério/contrato |
| --- | --- |
| RF-01, RF-02, RF-03, RF-04, RF-05, RF-06 | #2; interfaces GIS/MCP na #3 e visuais na #4 |
| RF-07, RF-08, RF-09, RF-10 | #3; método/tolerância na #2 e privacidade/erros na #5 |
| RF-11, RF-12 | #4; precisão na #2 e política de dados na #5 |
| RF-13, RF-14 | #6; entrada de geometria na #2 |
| RF-15, RF-16 | #5; contrato e entradas definidos por #2–#4 |
| RNF-01, RNF-10 | #6; operação e dependências na #5 |
| RNF-02, RNF-03, RNF-06 | #5; limites de entrada na #2 e arquivos na #4 |
| RNF-04, RNF-05 | #2 e #3; calibração na #4 |
| RNF-07, RNF-09 | #3 e #5 |
| RNF-08 | #3–#6; consolidação e auditoria na #7 |

## Ciclo de produto posterior

Ainda não há sprint, prazo ou ponto de produto comprometido. O ciclo deverá ter no máximo S1–S5 de entrega e S6 de validação extra/mudanças, cada uma de até uma semana, com todas as issues definidas antes da implementação. A classificação pré-planejamento não cria S7 nem consome capacidade de sprint sem alocação posterior.

Uma issue de produto fica pronta somente com escopo decidido, UC/RF/RNF pertinentes, sucesso/erro/limites, método de validação, tamanho e dependências direcionais. A disponibilidade de um contrato é diferente de aceite ou merge. PRs só são revisados/aprovados e issues aceitas por Pedro.
