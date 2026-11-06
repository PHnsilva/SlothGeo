# Arquitetura inicial

Direção de planejamento, ainda sem implementação. Monólito modular Python com API HTTP (FastAPI/Pydantic), contratos OpenAPI e portas/adaptadores. Versões só serão escolhidas após inventário e compatibilidade do ambiente no início.

```text
Consumidor / demonstração de mapa
  → API HTTP: autenticação, limites e contratos
  → ingestão: números, coordenadas, GeoJSON, documento/imagem
  → preparação geoespacial: referência, escala, geometria e proveniência
  → orquestração de medição
      → cliente MCP → Sofiee Agente de Cálculo → motor matemático
      → adaptadores locais GIS para validação/transformação/preparação
      → adaptador Google, somente quando necessário e configurado
  → resposta: método, valores/unidades, referência, origem e limitações
```

## Fronteiras

- SlothGeo é a API especializada no fluxo de terreno e cliente MCP do Cálculo. Não expõe servidor MCP próprio por padrão; só adicionar se houver consumidor e caso aprovado.
- O agente de Cálculo mantém as operações matemáticas/geodésicas reutilizáveis. Contrato deve definir quais transformações/preparações ficam no SlothGeo e quais operações ficam no agente para evitar duplicação.
- Bibliotecas GIS podem preparar/validar geometrias no produto; a fórmula e a computação da medição de domínio passam pela ferramenta apropriada do Cálculo. Não usar IA para adivinhar o resultado numérico.
- Google Maps JavaScript é usado no consumidor/demonstração web, não como biblioteca Python de servidor. A geometria enviada à API precisa ser validada independentemente do cliente. Places/Geocoding/Elevation são adaptadores separados e opcionais.
- Não tratar medição esférica do mapa e medição elipsoidal do backend como métodos idênticos; registrar método e tolerância na comparação.
- Arquivos do usuário são dados não confiáveis: limites de tamanho/pixels/páginas e tempo, tipos aceitos, identificação segura e descarte controlado. Não receber URL/caminho livres para leitura de disco/rede.
- Chaves de servidor não vão para o frontend. Chaves de navegador são separadas e restritas conforme o provedor. Não registrar conteúdo privado nem coordenadas completas por padrão.
- Persistência começa mínima; necessidade de retenção, banco e auditoria é decidida por RF/RNF, com prazo de descarte e acesso.
- Sem microserviços, fila, containers ou modelo de IA obrigatório por antecipação. Processos pesados futuros precisam justificar isolamento e capacidade.
