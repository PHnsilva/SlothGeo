# Escopo inicial — 06/11/2026

## Finalidade

Fornecer uma API reutilizável que transforme dados de terrenos em uma representação geométrica rastreável, valide suficiência e calcule área/perímetro pelo agente de Cálculo. Atender sistemas imobiliários e outros consumidores sem incorporar regras particulares de uma imobiliária ao motor genérico.

## Incluído no primeiro planejamento

- Entrada estruturada de dimensões, ângulos, unidades e coordenadas com sistema de referência declarado; polígonos e formatos usuais com informação suficiente.
- Importação de formatos geoespaciais simples a delimitar, priorizando GeoJSON e listas de coordenadas; tratar ordem de eixos, fechamento, furos e geometrias inválidas.
- Área e perímetro planos/geodésicos com método explícito, unidades, CRS/datum, origem dos dados, avisos e resultado reproduzível. Coordenadas em graus não são metros.
- Integração real com o agente de Cálculo por MCP; fórmulas, integrais e rotinas genéricas pertencem ao agente, com contrato e versionamento. SlothGeo prepara o contexto geoespacial e orquestra o caso. Se a dependência não estiver disponível, informar indisponibilidade; mocks não demonstram integração.
- Entrada de imagem/documento com medidas legíveis, OCR e associação assistida de dados; exigir confirmação para ambiguidade. Plantas/imagens com escala ou georreferenciamento podem ser preparadas e calibradas com assistência; não deduzir referência ausente.
- Adaptador Google Maps: documentar apresentação de mapa, seleção de vértices no consumidor e envio de geometria à API. Uma página demonstrativa mínima pode apoiar esse fluxo; o produto principal continua uma API.
- Geocoding/Places, quando necessário, para localização de referência; endereço não identifica sozinho o contorno do terreno. Elevation é candidato para análise futura de relevo, com precisão/resolução explicitadas.
- Resposta com resultado, método, dados utilizados e estado `calculated`, `estimated`, `insufficient_data` ou `dependency_unavailable`; nomes finais e contrato são definidos no início.
- Autenticação adequada ao uso, limites de entrada/tempo/arquivo, proteção de uploads e acesso mínimo a sistemas consumidores. Não executar fórmulas como código arbitrário.
- Documentação OpenAPI, exemplos públicos/sintéticos, testes de casos de referência e rastreabilidade das dependências/versões.

## Fora do primeiro ciclo

- Medição garantida a partir de qualquer material, fotografia sem referência suficiente ou apenas endereço.
- Cadastro oficial de limites de propriedades, certificação de levantamento ou afirmação de precisão superior à dos dados de entrada.
- Fotogrametria de drone, reconstrução 3D e segmentação automática geral de limites. Área real da superfície inclinada exige elevações/modelo de terreno adequado; não a confundir com área horizontal do polígono.
- Treinar um modelo visual próprio, criar agentes/repos extras ou duplicar o agente de Cálculo.
- Dashboard imobiliário completo, gestão de imóveis/contratos e banco obrigatório sem requisito.
- Ativar faturamento, contratar serviços, publicar API ou habilitar chaves Google sem autorização específica. Operação paga não é requisito já financiado.

## Aceite do ciclo a detalhar em RF/RNF

Um consumidor deve conseguir fornecer um terreno por entrada suportada, receber área/perímetro verificáveis ou uma explicação precisa dos dados ausentes, consultar documentação e reproduzir o método. Integração MCP e integração Google precisam de evidências reais próprias; o núcleo local não pode depender de cobrança para funcionar. Casos visuais devem distinguir extração, confirmação humana e medição.
