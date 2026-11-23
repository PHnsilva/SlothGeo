# Decisões para refinamento com Pedro

Registro inicial de 21/11/2026. A orientação vigente é preparar uma base e aguardar novas orientações para melhorá-la. Estes pontos serão refinados com Pedro; não exigem resposta a uma lista inteira para que ele possa revisar os UC. Nenhuma alternativa abaixo é uma decisão aprovada por silêncio.

| ID | Decisão específica | O que a fonte já determina | O que falta e condição para liberar |
| --- | --- | --- | --- |
| D01 | Entradas e geometria do primeiro ciclo | Dimensões/coordenadas; prioridade para listas e GeoJSON; referência explícita, validade e suficiência. | Tipos de figura e geometria, furos/MultiPolygon, CRS/unidades aceitos, normalizações, casos de antimeridiano/polos e limites de vértices/bytes. Registrar o conjunto escolhido antes das issues afetadas. |
| D02 | Método, precisão e tolerâncias | Área/perímetro verificáveis; distinguir plano/geodésico e precisão da entrada. | Métodos por entrada, unidades de saída, arredondamento, erro/tolerância por caso e referências de comparação. Registrar matriz método/caso/tolerância, sem prometer precisão física ausente. |
| D03 | Contrato MCP geoespacial e disponibilidade | Cálculo é responsável pelo motor; SlothGeo prepara/orquestra; indisponibilidade é explícita. | Ferramentas/schemas reais para figuras/polígonos e geodesia, transporte, versões, fronteiras de transformação, erros e timeouts. Confirmar artefato executável e teste real; não inventar nome de ferramenta nem mudar o outro repositório nesta rodada. |
| D04 | Entrada assistida de imagem/documento | OCR extrai medidas; pessoa confirma ambiguidade; escala/referência suficiente é obrigatória. | Formatos/páginas/pixels, idiomas/unidades, protocolo de confirmação, origem da associação e métodos/condições de calibração. Registrar fluxo e exemplos aceitos/rejeitados antes das issues afetadas. |
| D05 | Consumidor, acesso, privacidade e retenção | Não publicar credenciais/documentos privados; persistência mínima, sem banco obrigatório. | Uso local versus consumidores externos, autenticação, guarda temporária, descarte, logs e responsabilidades do consumidor. Implantação não está autorizada. |
| D06 | Papel dos produtos Google no ciclo | Mapa é consumidor/apresentação; Geocoding/Places são opcionais; custo/chaves/faturamento não autorizados. | Qual produto é realmente necessário, qual entrega pode ser local/documental e o que permanecerá bloqueado. Uso real só se houver autorização específica compatível com custo zero; não ativar nada por inferência. |
| D07 | Metas de desempenho e robustez | Limites de entrada/tempo e proteção contra abuso são obrigatórios. | Hardware/ambiente, carga, latência/percentis e limites de execução, concorrência, arquivos e timeout. Medir antes de prometer SLA. |
| D08 | Priorização e ciclo de entrega | Até 5 sprints de entrega + 1 de validação/mudanças, cada uma até uma semana; validar desde S1. | Após revisão dos UC/requisitos, decompor e estimar todas as issues, dependências e capacidade por sprint. Conferir cobertura e Kanban antes de implementar. Não há cronograma de produto aprovado nesta versão. |

## Dependências observadas em 21/11/2026

- O contrato na branch principal do [Cálculo](https://github.com/PHnsilva/sofiee-agent-calculation/blob/main/contracts/v1/contracts.json) é v1.0.0 e lista `calculation.evaluate`, `calculation.symbolic` e `calculation.convertUnits`; esse arquivo descreve schemas e não comprova runtime disponível.
- [Cálculo #19](https://github.com/PHnsilva/sofiee-agent-calculation/issues/19) planeja figuras/polígonos planos; [Cálculo #20](https://github.com/PHnsilva/sofiee-agent-calculation/issues/20) planeja geodesia e depende de #19. Os PRs abertos consultados nesta rodada não anunciam essas duas entregas. Não há comprovação de integração geoespacial do SlothGeo.
- A cópia canônica local do Cálculo possui alterações existentes e não reflete sozinha todo o estado remoto. Foi somente consultada; nada nela foi alterado, instalado ou executado nesta rodada.
- O acesso GitHub disponível permite issues e PRs; a consulta GraphQL a Projects retornou ausência de `read:project`. A sessão existente no navegador, autenticada como PHnsilva, permite conferir a organização sem ampliar o acesso do token.

## Fontes oficiais conferidas

- [RFC 7946 — GeoJSON](https://datatracker.ietf.org/doc/html/rfc7946): representação geográfica WGS 84, ordem longitude/latitude, anéis e polígonos. Não define precisão de levantamento.
- [Preços do Google Maps Platform](https://developers.google.com/maps/billing-and-pricing/overview): modelo e condições variam por SKU; franquia não é autorização para habilitar faturamento.
- [Descontinuações do Google Maps Platform](https://developers.google.com/maps/deprecations): não planejar integração apoiada em biblioteca de desenho antiga sem conferir suporte vigente.
- [Campos de seleção do GitHub Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects/understanding-fields/about-single-select-fields): estados são campos reais do quadro; conferir opções e itens após configurá-los.

As licenças/versões das bibliotecas do catálogo ainda não foram selecionadas nem validadas para instalação. A direção Python/FastAPI/Pydantic vem da arquitetura existente, não de uma instalação realizada agora.
