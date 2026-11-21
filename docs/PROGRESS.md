# Continuidade do SlothGeo

## Rodada de 21/11/2026 — preparação inicial

- **Orientação vigente:** Pedro pediu primeiro UC, requisitos derivados, Projects inicial e issues; dará orientações posteriores para melhorar a base. Esta rodada não inclui implementação do produto.
- **Rastreabilidade:** issue #1, M = 4, pré-planejamento; branch `docs/1-casos-uso-requisitos-iniciais`. Commit/PR e verificações finais ainda serão registrados.
- **Inventário inicial:** SlothGeo público, branch principal `main`, HEAD remoto e local `38f9ffe43ed2263f7721510f628a36b94d10b805`; nenhuma issue ou PR antes desta rodada; cópia local limpa antes da criação da branch.
- **Ambiente observado:** Windows, Git 2.56.0.windows.4 e Node 24.22.3 disponíveis no C:. `python` no PATH aponta para alias do Windows. Há ambientes existentes do Cálculo e MCP em `C:\DevData\Codex\agents\venvs`, somente localizados; nenhum foi executado ou alterado. Nenhum ambiente Python do SlothGeo foi criado/verificado e nenhuma instalação foi realizada.
- **Conta e acesso:** conector GitHub identificado como PHnsilva, com leitura/escrita no SlothGeo. Projects não é suportado pelas ferramentas disponíveis do conector; token local não dispõe de `read:project`. A sessão do navegador foi conferida como PHnsilva; não foi ampliada nenhuma permissão.
- **Rotina:** automação existente deste chat convertida de início único para diária às 04h30 de São Paulo, preservando prompt e destino; configuração observada do agendador usa 07h30 UTC. Nenhuma rotina de outro projeto foi alterada. A agenda não substitui a orientação atual de foco no planejamento.
- **Preparação:** 9 UC, 16 RF, 10 RNF e 8 decisões de refinamento em documentos separados. São uma versão inicial, não aceite nem implementação.
- **Backlog inicial:** issues #1–#7 abertas, com exatamente uma label de tamanho cada, critérios de aceite, validação e dependências. #1–#5 e #7 são M=4; #6 é P=2. A estimativa de 26 unidades do backlog não representa entrega realizada. #7 tem bloqueios nativos e textuais por #2–#6, conferidos pela API.
- **Projects:** [SlothGeo — Planejamento inicial, nº 14](https://github.com/users/PHnsilva/projects/14), privado. Conferidos os seis estados em ordem e a presença das sete issues sem duplicatas após recarregar o quadro. Estado final da #1 será registrado depois da abertura do PR; as demais permanecem no Backlog aguardando refinamento.
- **Verificação documental executada:** 8 arquivos conferidos, 25 links locais válidos, 9 UC com oito elementos descritivos cada, IDs únicos de 16 RF/10 RNF/8 decisões e referência individual de todos os UC/RF/RNF na matriz. `git diff --check` passou. Auditoria do GitHub confirmou as sete issues abertas, os campos obrigatórios e os cinco bloqueios nativos de #7. Não há teste de API, OCR, GIS, Google ou integração MCP executado nesta rodada.
- **Dependência externa:** contrato principal do Cálculo v1.0.0 não expõe operações geoespaciais; suas issues #19/#20 registram a direção. Nenhuma chamada MCP geoespacial foi realizada e a cópia local existente do Cálculo foi preservada.
- **Pontos:** ainda não contabilizados; só registrar entrega validada e enviada para revisão. Consulta ao GitHub, diagnóstico e mudança de agenda não contam como entrega de produto.
- **Próxima ação desta rodada:** configurar/conferir Projects, criar backlog de refinamento, completar os vínculos e abrir PR documental.
- **Condição para a próxima etapa:** receber as orientações de Pedro, resolver decisões afetadas e definir todas as issues/sprints de produto antes de qualquer implementação.
