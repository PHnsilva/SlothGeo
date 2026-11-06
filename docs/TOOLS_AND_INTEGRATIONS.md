# Ferramentas, bibliotecas e APIs — catálogo para retomada

Nenhum item está instalado ou integrado por este bootstrap. Revalidar documentação, versões, compatibilidade no Windows, licenças, limites e necessidade em 21/11/2026. Não instalar todo o catálogo indiscriminadamente.

| Item | Papel e localização planejada | Situação / referência oficial |
| --- | --- | --- |
| Python + FastAPI + Pydantic | API HTTP, contratos, validação de entrada e OpenAPI no SlothGeo | Direção inicial. https://fastapi.tiangolo.com/features/ e https://docs.pydantic.dev/latest/ |
| Cliente MCP / SDK oficial Python | Consumir operações do agente de Cálculo, com timeout e schemas | Contrato ainda precisa ser definido. https://github.com/modelcontextprotocol/python-sdk |
| SymPy | Álgebra, fórmulas, derivadas e integrais simbólicas no agente de Cálculo | Reutilizar por MCP, não copiar o motor. https://docs.sympy.org/latest/tutorial/calculus.html |
| NumPy / SciPy | Cálculo numérico e integração quando justificados, no agente de Cálculo | Não são necessários para toda área poligonal. https://numpy.org/doc/ e https://docs.scipy.org/doc/scipy/reference/integrate.html |
| Shapely / GEOS | Polígonos, validade e preparação geométrica; computação reutilizável com fronteira definida no contrato | Geometria plana; não presumir área em m² ao receber graus. https://shapely.readthedocs.io/en/stable/manual.html |
| pyproj / PROJ | CRS, transformação e geodesia conforme o dado | Definir ordem de eixos, datum e grids necessários. https://pyproj4.github.io/pyproj/stable/ e https://proj.org/ |
| GeographicLib | Áreas/perímetros geodésicos no agente de Cálculo | Evitar dois motores concorrentes sem necessidade; escolher estratégia com avaliação. https://geographiclib.sourceforge.io/html/python/code.html#module-geographiclib.polygonarea |
| GDAL / Rasterio | Leitura de imagens georreferenciadas, transformações e referência de pixels | Adotar apenas para entradas realmente incluídas e compatibilidade comprovada. https://gdal.org/en/stable/user/raster_data_model.html e https://rasterio.readthedocs.io/en/stable/ |
| Tesseract OCR | Extrair texto, números e unidades de imagens/documentos | Não reconstrói sozinho a geometria; confirmar ambiguidade. https://tesseract-ocr.github.io/tessdoc/ |
| OpenCV | Pré-processamento e calibração assistida de imagens, se necessário | Sem inferir escala ou limites ausentes. https://docs.opencv.org/ |
| Google Maps JavaScript API | Mapa no consumidor/página demonstrativa e seleção de vértices | Seleção deve usar APIs atuais suportadas; não assumir bibliotecas de desenho antigas disponíveis. https://developers.google.com/maps/documentation/javascript/overview |
| Google Maps Geometry | Comparação/apresentação de medidas no consumidor, método esférico declarado | Resultado exibido no mapa não substitui contrato/verificação do servidor. https://developers.google.com/maps/documentation/javascript/geometry |
| Google Geocoding / Places | Localização e busca de referência quando incluídas | Endereço não é limite de propriedade. https://developers.google.com/maps/documentation/geocoding/overview e https://developers.google.com/maps/documentation/places/web-service/overview |
| Google Elevation | Elevações como dado complementar, se o requisito justificar | Não equivale a levantamento nem produz superfície 3D precisa sozinho. https://developers.google.com/maps/documentation/elevation/overview |

## Custos e credenciais

Nenhuma conta, chave, faturamento ou chamada remota foi habilitada. A diretriz atual é custo adicional zero. Desenhar e testar adaptadores com casos locais e fixtures identificadas; uma integração real dependente de chave/cota só pode ser declarada validada quando executada e documentada. Se exigir faturamento ou recurso não autorizado, registrar bloqueio e condição de liberação; não contratar por conta própria.

Conferir as políticas atuais do provedor antes de armazenar, redistribuir ou usar imagens/dados em processamento. Preservar atribuição e restrições de chave, respeitar limites e não fazer scraping para contornar APIs. Não assumir autorização para extrair limites de propriedades de imagens Google.

Fontes de retomada: https://developers.google.com/maps/documentation e https://developers.google.com/maps/documentation/tile/policies . Documentar APIs efetivamente usadas e condições aplicáveis, sem presumir que uma política de um produto serve para todos.
