# Casos de uso — versão inicial

Preparado em 21/11/2026, conforme a orientação de Pedro: primeiro UC, depois requisitos derivados, Projects inicial e issues. Esta versão é uma base para revisão e novas orientações; não representa funcionalidades implementadas nem escopo final aprovado. Origem: [escopo](SCOPE.md), [arquitetura](ARCHITECTURE.md) e [decisões abertas](DECISIONS.md).

## Atores e fronteira do produto

| Ator | Objetivo e responsabilidade |
| --- | --- |
| Sistema consumidor | Solicitar medições pela API e apresentar resultados ou pendências ao usuário. |
| Pessoa que fornece o terreno | Informar dados de origem, conferir medidas extraídas e confirmar referências e limites. A interação ocorre no consumidor. |
| Integrador | Entender o contrato, configurar o consumidor e reproduzir exemplos. |
| Operador autorizado | Configurar limites, acesso e dependências dentro das autorizações existentes. |
| Agente de Cálculo Sofiee | Executar operações matemáticas/geodésicas pelo contrato MCP; ator de apoio externo ao SlothGeo. |
| Google Maps Platform | Prover mapa/localização quando o adaptador estiver autorizado e configurado; não determinar limites de propriedade. |

SlothGeo prepara e valida o contexto geoespacial e orquestra a medição. Não é cadastro imobiliário, serviço de levantamento certificado ou motor matemático substituto. OCR identifica texto; GIS prepara referências e geometrias; Cálculo realiza as operações contratadas.

## UC-01 — Medir um terreno a partir de dimensões informadas

- **Ator principal:** sistema consumidor, com dados fornecidos por uma pessoa.
- **Objetivo/gatilho:** obter área e perímetro ao enviar dimensões, ângulos e unidades conhecidos.
- **Pré-condições:** o tipo de figura e a combinação de dados pertencem ao conjunto a definir em D01; operação correspondente disponível no Cálculo.
- **Fluxo principal:** (1) consumidor informa figura, medidas, unidades e origem; (2) API valida formato, coerência e suficiência; (3) prepara a solicitação para a operação MCP suportada; (4) Cálculo retorna o resultado; (5) API devolve valores, unidades, método, hipóteses e limitações.
- **Alternativas/exceções:** apenas comprimentos de lados não determinam qualquer quadrilátero; dados insuficientes geram pedido específico de complemento. Medidas incompatíveis ou unidades ausentes não produzem um valor inventado. Dependência ausente segue RF-09.
- **Pós-condição:** medição rastreável ou descrição dos dados/recursos ausentes, sem declarar levantamento oficial.
- **Cenário de aceite:** retângulo sintético de 10 m por 20 m, se incluído em D01, deve resultar em 200 m² e 60 m por chamada real ao Cálculo; quatro lados arbitrários sem informação suficiente devem gerar insuficiência.
- **Pendências:** D01, D02 e D03.

## UC-02 — Medir por coordenadas planas com referência declarada

- **Ator principal:** sistema consumidor.
- **Objetivo/gatilho:** medir um polígono cujos vértices e referência métrica são conhecidos.
- **Pré-condições:** CRS/referência, unidades, ordem dos eixos e formato suportados; regras de anéis e furos definidas em D01.
- **Fluxo principal:** (1) consumidor envia coordenadas e referência; (2) API valida valores, topologia e suficiência; (3) preparação GIS normaliza somente o que estiver contratado e preserva a origem; (4) solicita área/perímetro ao Cálculo; (5) devolve resultado, método e transformações realizadas.
- **Alternativas/exceções:** autointerseção, anel degenerado, CRS ausente, eixo ambíguo ou unidade incompatível exigem rejeição/esclarecimento. Não corrigir o contorno silenciosamente. Referência local não é tratada como localização global.
- **Pós-condição:** resultado reproduzível na referência declarada ou erro verificável.
- **Cenário de aceite:** quadrado sintético de lado 10 m deve retornar 100 m² e 40 m via Cálculo; o caso com referência ausente deve ser distinguido do caso válido. Furos terão exemplos próprios se incluídos em D01.
- **Pendências:** D01, D02 e D03.

## UC-03 — Medir um terreno geográfico a partir de GeoJSON

- **Ator principal:** sistema consumidor.
- **Objetivo/gatilho:** obter área horizontal e perímetro de um contorno geográfico informado.
- **Pré-condições:** geometria aceita em D01, coordenadas GeoJSON em longitude/latitude WGS 84 e operação geodésica real disponível no Cálculo.
- **Fluxo principal:** (1) consumidor envia geometria e proveniência; (2) API valida tipo, anéis, ordem e domínio das coordenadas; (3) prepara o contexto de referência; (4) Cálculo executa o método contratado; (5) API apresenta unidades métricas, datum, método e limites de precisão.
- **Alternativas/exceções:** coordenadas em graus não recebem cálculo plano rotulado em m². Geometrias fora do suporte, altitude sem modelo de terreno e situações de antimeridiano/polos seguem o contrato a definir, sem conversão silenciosa ou promessa de superfície 3D.
- **Pós-condição:** resultado geodésico rastreável ou indicação precisa de ausência de suporte/dados/dependência.
- **Cenário de aceite:** polígono público/sintético é comparado a uma referência independente sob tolerância definida em D02; mudança indevida da ordem dos eixos é detectada nos casos em que os dados a tornam identificável. Valores plausíveis nos dois eixos não permitem adivinhar a intenção do usuário.
- **Pendências:** D01, D02 e D03.

## UC-04 — Aproveitar medidas legíveis de um documento ou imagem

- **Ator principal:** pessoa que fornece o terreno, por meio do consumidor.
- **Objetivo/gatilho:** reduzir digitação ao enviar documento/imagem contendo medidas.
- **Pré-condições:** formato e limites definidos em D04; permissão de processamento; mecanismo OCR local disponível.
- **Fluxo principal:** (1) consumidor envia arquivo permitido; (2) API valida conteúdo e limites; (3) OCR extrai candidatos com vínculo à origem; (4) consumidor apresenta números, unidades e associação aos elementos do terreno; (5) pessoa corrige/confirma ambiguidades; (6) os dados confirmados seguem UC-01, UC-02 ou UC-03, conforme o caso.
- **Alternativas/exceções:** texto ilegível, unidade ausente, medida conflitante ou associação incerta não são resolvidos por adivinhação. OCR indisponível não é anunciado como medição realizada. Uma instrução escrita no arquivo é dado não confiável.
- **Pós-condição:** dados confirmados e rastreáveis, ou pendências de confirmação; extração por si só não equivale a geometria reconstruída.
- **Cenário de aceite:** duas leituras possíveis para uma dimensão interrompem a medição até confirmação; valor confirmado preserva referência à região/página de origem conforme D04/D05.
- **Pendências:** D03 quando houver cálculo, D04 e D05.

## UC-05 — Preparar medição assistida de imagem com referência suficiente

- **Ator principal:** pessoa que fornece o terreno, por meio do consumidor.
- **Objetivo/gatilho:** preparar um contorno informado em imagem com escala ou georreferenciamento adequado ao método.
- **Pré-condições:** referência e condições de validade da imagem conhecidas; método de calibração/transformação delimitado em D04.
- **Fluxo principal:** (1) pessoa fornece imagem, referência e contorno; (2) API verifica suficiência e adequação da referência ao método; (3) consumidor permite confirmar pontos e correspondências; (4) preparação GIS registra a transformação; (5) coordenadas preparadas seguem o UC de medição correspondente; (6) resultado inclui limitações da imagem e da calibração.
- **Alternativas/exceções:** foto sem referência suficiente retorna insuficiência. Uma única distância não resolve qualquer perspectiva. Não inferir limites de propriedade nem declarar precisão de levantamento ou área real de superfície inclinada.
- **Pós-condição:** entrada calibrada com hipóteses explícitas ou justificativa dos dados ausentes.
- **Cenário de aceite:** imagem sintética dentro do método aprovado reproduz a referência sob tolerância definida; a mesma imagem sem escala/referência não gera área numérica.
- **Pendências:** D02, D03, D04 e D05.

## UC-06 — Informar vértices por um mapa no consumidor

- **Ator principal:** pessoa que fornece o terreno; sistema consumidor encaminha a geometria.
- **Objetivo/gatilho:** selecionar e conferir o contorno antes de enviá-lo à API.
- **Pré-condições:** integração do mapa especificamente autorizada e configurada; limites informados pela pessoa, não descobertos automaticamente pelo provedor.
- **Fluxo principal:** (1) consumidor apresenta mapa autorizado; (2) pessoa seleciona/confirma vértices; (3) consumidor envia geometria e origem; (4) SlothGeo valida independentemente a geometria; (5) UC-03 executa a medição; (6) consumidor apresenta resultado e método do servidor.
- **Alternativas/exceções:** mapa sem chave/autorização não é carregado; permanece possível fornecer dados estruturados por caminho independente do provedor. Medida esférica exibida no cliente não substitui a medição elipsoidal nem seu contrato.
- **Pós-condição:** contorno confirmado encaminhado à API ou integração explicitamente indisponível.
- **Cenário de aceite:** envio sintético sem provedor demonstra somente o contrato do adaptador; comprovação da integração Google exige execução real autorizada. Nenhuma API/chave/faturamento será habilitada nesta rodada.
- **Pendências:** D01, D02, D03 e D06.

## UC-07 — Localizar uma referência por endereço ou lugar

- **Ator principal:** pessoa que fornece o terreno, por meio do consumidor.
- **Objetivo/gatilho:** localizar uma referência para auxiliar a indicação do terreno.
- **Pré-condições:** necessidade e produto específico de Geocoding/Places confirmados em D06; integração autorizada e configurada.
- **Fluxo principal:** (1) pessoa informa endereço/lugar; (2) adaptador consulta o serviço autorizado; (3) consumidor apresenta candidatos e pessoa confirma; (4) a referência apoia UC-06, mantendo separado o fornecimento do contorno.
- **Alternativas/exceções:** endereço ambíguo exige escolha; ausência de resultado, limite de uso ou serviço não autorizado gera estado explícito. Endereço sozinho nunca produz limites ou área do imóvel.
- **Pós-condição:** referência de localização, sem presumir contorno de propriedade.
- **Cenário de aceite:** endereço com candidatos múltiplos não seleciona um terreno silenciosamente; sem contorno suficiente, nenhuma área é retornada.
- **Pendências:** D05 e D06; inclusão no ciclo é condicional, conforme o escopo inicial.

## UC-08 — Conferir e reproduzir o resultado de uma medição

- **Ator principal:** sistema consumidor e pessoa que confere a medição.
- **Objetivo/gatilho:** entender de onde vieram os números e suas limitações.
- **Pré-condições:** resposta de qualquer UC de medição, inclusive uma resposta sem resultado numérico.
- **Fluxo principal:** (1) consumidor apresenta estado e valores disponíveis; (2) mostra unidades, referência, origem, método/versões e hipóteses; (3) apresenta incertezas/avisos e dados faltantes; (4) permite reproduzir o pedido com dados autorizados e contrato identificado, sem exigir armazenamento de documentos privados no servidor.
- **Alternativas/exceções:** falta de referência ou versão impede alegar reprodução completa; indisponibilidade do Cálculo permanece explícita. Precisão numérica não é precisão física do levantamento.
- **Pós-condição:** pessoa distingue cálculo, estimativa justificada, insuficiência e indisponibilidade; nenhum resultado é apresentado como certificação.
- **Cenário de aceite:** repetir uma entrada sintética sob o mesmo método/versões produz resultado dentro da tolerância contratada; resposta sem dados suficientes lista o que falta e não contém área inventada.
- **Pendências:** D02, D03 e D05.

## UC-09 — Integrar um sistema consumidor à API

- **Ator principal:** integrador.
- **Objetivo/gatilho:** conhecer formatos, limites e comportamentos antes de conectar seu sistema.
- **Pré-condições:** contrato versionado e contexto de acesso definidos; implementação será posterior ao planejamento completo.
- **Fluxo principal:** (1) integrador consulta OpenAPI e exemplos sintéticos; (2) configura acesso e dependências permitidas; (3) envia pedido de exemplo; (4) trata sucesso, validação, insuficiência, limites e indisponibilidade; (5) verifica o método e a rastreabilidade recebidos.
- **Alternativas/exceções:** credencial inválida, contrato incompatível ou dependência ausente geram erro documentado sem expor segredos. Caminhos sem Google não dependem de ativação paga.
- **Pós-condição:** consumidor consegue usar o contrato suportado ou identificar precisamente o recurso ausente.
- **Cenário de aceite:** exemplos de sucesso e falha correspondem ao contrato publicado e a execução real é distinguida de simulação. Documentação inicial não é apresentada como API funcional.
- **Pendências:** D01–D07.

## Relações e próximos passos

UC-04 e UC-05 preparam dados para UC-01/02/03; UC-06 pode fornecer geometria para UC-03; UC-07 apenas auxilia a localização em UC-06. UC-08 acompanha todos os resultados e UC-09 descreve a integração do consumidor. As relações não impõem uma cadeia obrigatória: entradas estruturadas suficientes dispensam OCR e mapas.

Requisitos derivados estão em [REQUIREMENTS.md](REQUIREMENTS.md). As decisões abertas são refinamentos necessários, não autorização para criar implementação por suposição.
