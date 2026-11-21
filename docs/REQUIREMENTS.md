# Requisitos derivados dos casos de uso

Versão inicial de 21/11/2026, derivada de [USE_CASES.md](USE_CASES.md) e do escopo existente. A classificação **base documental** significa que a necessidade está descrita nas fontes; não significa aceite de Pedro ou implementação. **Detalhar** aponta uma decisão ainda necessária em [DECISIONS.md](DECISIONS.md). Nomes definitivos de campos, endpoints e estados, versões e valores de limites serão definidos depois do refinamento.

## Requisitos funcionais

| ID | Necessidade observável | Origem | Verificação prevista e pendência |
| --- | --- | --- | --- |
| RF-01 | Receber solicitações estruturadas em contrato versionado, preservando tipo de entrada, unidade/referência e proveniência pertinentes. | UC-01/02/03/09 | Exemplos válidos/inválidos e compatibilidade de contrato; detalhar D01/D03. |
| RF-02 | Aceitar dimensões e ângulos somente para figuras e combinações de dados declaradas suficientes. | UC-01 | Retângulo conhecido e quadrilátero indeterminado; detalhar conjunto em D01. |
| RF-03 | Validar coordenadas planas, unidades, CRS/referência e ordem de eixos antes da preparação ou medição. | UC-02 | Casos métricos válidos, referência ausente e eixos ambíguos; detalhar D01. |
| RF-04 | Importar os tipos GeoJSON incluídos, respeitando longitude/latitude WGS 84, fechamento de anéis e regras de validade/furos. | UC-03 | Geometrias válidas, inválidas e fora do suporte; detalhar tipos/furos/limites em D01. |
| RF-05 | Verificar suficiência e informar os dados específicos ausentes ou ambíguos antes de produzir uma medida. | UC-01/02/03/04/05/07 | Foto sem escala, endereço sem contorno, unidades ausentes e dados indeterminados não retornam área inventada. Base documental. |
| RF-06 | Preparar e validar geometrias com GIS, registrando normalizações/transformações e preservando os dados de origem necessários à rastreabilidade. | UC-02/03/05 | Invalidade é informada; contorno não é reparado silenciosamente; detalhar fronteira em D01/D03. |
| RF-07 | Consumir ferramentas reais e schemas versionados do agente de Cálculo por MCP, verificando a capacidade necessária. | UC-01/02/03/08/09 | Descoberta/chamada real, contrato incompatível e ferramenta ausente; detalhar D03. Fixtures isoladas não comprovam integração. |
| RF-08 | Orquestrar área/perímetro planos ou geodésicos no Cálculo e devolver resultado com método, unidades, referência e tolerância/limitação pertinentes. | UC-01/02/03/05/08 | Referências independentes por método; não medir graus como metros nem chamar área horizontal de superfície 3D; detalhar D02/D03. |
| RF-09 | Distinguir cálculo, estimativa justificada, insuficiência, entrada inválida/fora do suporte e dependência indisponível, sem fallback matemático oculto. | UC-01–09 | Casos de falha não produzem número fictício; detalhar nomes/códigos e política em D03. Estado de estimativa exige fundamento explícito. |
| RF-10 | Expor proveniência, método/versões, hipóteses e limitações suficientes para conferir a medição. | UC-08 | Entrada sintética reproduzível sem publicar dados privados; detalhar D02/D03/D05. |
| RF-11 | Extrair candidatos de medidas/unidades com vínculo à origem e exigir confirmação/correção de ambiguidades antes de medir. | UC-04 | Número ambíguo e associação incerta interrompem a medição; detalhar formatos e interação em D04. |
| RF-12 | Preparar contorno de imagem somente com referência e calibração adequadas ao método, com confirmação e limitações explícitas. | UC-05 | Imagem calibrada sintética versus a mesma imagem sem referência; detalhar método em D04 e tolerâncias em D02. |
| RF-13 | Aceitar geometria selecionada e confirmada no consumidor, validando-a independentemente de sua origem no mapa. | UC-06 | Entrada do consumidor não contorna validação; integração Google real permanece condicionada a D06. |
| RF-14 | Quando necessário e incluído no ciclo, obter candidatos de localização por adaptador específico, sem deduzir contorno/área de endereço. | UC-07 | Ambiguidade, ausência de resultado e indisponibilidade; requisito condicional a D06. |
| RF-15 | Documentar contrato OpenAPI, formatos/limites e exemplos sintéticos reproduzíveis de sucesso e falha. | UC-09 | Exemplos conferidos com contrato e, após implementação, com execução real. Depende das decisões D01–D07. |
| RF-16 | Aplicar controle de acesso e ciclo de tratamento/descarte de documentos adequados ao contexto de uso definido. | UC-04/05/09; arquitetura | Acesso não autorizado e descarte conferíveis, sem expor credenciais; detalhar D05. |

## Requisitos não funcionais

| ID | Restrição ou qualidade verificável | Origem | Critério e decisão necessária |
| --- | --- | --- | --- |
| RNF-01 | Custo adicional autorizado zero; núcleo e avaliação local não dependem de serviço pago. | UC-01/02/03/09; restrição do proprietário | Nenhuma chave, conta paga, faturamento ou chamada cobrável ativados por inferência. Produtos opcionais têm análise separada em D06. |
| RNF-02 | Entradas/arquivos não confiáveis têm limites verificáveis de tamanho, complexidade, páginas/pixels e tempo pertinentes. | UC-01–06/09; arquitetura | Limite e limite+1, tipo incompatível, fórmula hostil e URL/caminho arbitrário; valores a definir em D01/D04/D07. |
| RNF-03 | Dados privados e credenciais são protegidos; conteúdo/documentos/coordenadas completas não entram em logs por padrão. | UC-04/05/08/09 | Conferência de logs, erros, arquivos temporários e descarte; política exata em D05. Não reter por conveniência não acordada. |
| RNF-04 | Resultado identifica dados/método/versões necessários à reprodução sob condições equivalentes. | UC-08/09 | Repetição de casos sintéticos e registro das dependências; detalhar D02/D03. |
| RNF-05 | Precisão numérica, tolerância por método e incerteza dos dados são distinguíveis e verificáveis. | UC-01/02/03/05/08 | Referências independentes, degenerados e casos extremos com tolerâncias aprovadas em D02; nenhuma precisão fixa é presumida. |
| RNF-06 | Latência e capacidade são medidas em ambiente declarado, com limites de requisição e dependências explícitos. | UC-01–06/09 | Definir métricas, percentis, carga, hardware e orçamento de tempo em D07 antes de prometer um SLA. |
| RNF-07 | Arquitetura mantém API Python modular e separação entre ingestão, GIS, orquestração MCP e adaptadores. | UC-01–09; arquitetura | Inspeção das fronteiras e compatibilidade Windows; nenhuma duplicação do motor de Cálculo. Versões serão selecionadas depois do inventário pertinente. |
| RNF-08 | Evidências distinguem simulado, executado, integrado e aceito, com casos de sucesso, falha e limites. | UC-01–09 | MCP real e Google real têm evidências próprias; testes locais de adaptador não atestam serviço remoto. |
| RNF-09 | Falhas de dependência retornam estado explícito e respeitam limites de execução/concor­rência, sem acesso arbitrário à rede/disco. | UC-01–06/09 | Simular falha só testa tratamento; comprovar integração exige chamada real. Política de timeout/retry/capacidade em D03/D07. |
| RNF-10 | Dependências têm licença, compatibilidade e necessidade verificadas; ferramentas, caches e artefatos ficam no C:. | UC-09; restrições do proprietário | Inventário e fontes oficiais antes de adoção; nenhuma instalação indiscriminada, uso do D: ou infraestrutura antecipada. |

## Regras de domínio que atravessam os requisitos

1. Endereço ou imagem sem referência suficiente não define contorno nem área de uma propriedade.
2. GeoJSON usa coordenadas geográficas em graus; uma grandeza em graus não é um resultado em metros ou metros quadrados.
3. Área horizontal, área esférica, área elipsoidal e superfície inclinada não são intercambiáveis.
4. Geometria corrigida, medida estimada e extração OCR confirmada precisam ter origem e hipóteses explícitas.
5. Operações matemáticas/geodésicas reutilizáveis pertencem ao Cálculo; o SlothGeo não substitui uma capacidade faltante por motor duplicado.
6. Busca/Validação não são dependências obrigatórias de toda medição; integração adicional exige necessidade e contrato.

## Estado da especificação

Há **9 UC, 16 RF e 10 RNF iniciais**. Todos têm origem e verificação prevista; decisões quantitativas e contratos ainda não fechados permanecem pendentes. A [matriz inicial](INITIAL_PLAN.md) rastreará o refinamento, sem apresentar essas issues documentais como cobertura implementada do produto. A criação de todas as issues de implementação e a conferência do ciclo completo ocorrerão após as próximas orientações de Pedro.
