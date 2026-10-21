# Vertere 0.7.0 — velocidade das legendas e agrupamento

- Novo ajuste de velocidade: Mais fiel, Equilibrado e Mais rápido, separado do ritmo de leitura.
- Equilibrado é o padrão para novas preferências. Escolhas salvas são respeitadas; prévias cautelosas anteriores migram para Mais fiel.
- Blocos menores, com até duas linhas, agrupamento com início de frase longa e contexto para sufixos curtos.
- Modo rápido aceita prévias somente com a tela livre; finais são preservados. Antecipa a tradução, mas não garantiu menor atraso de exibição nos testes e pode produzir erros de sentido.
- Proteção contextual de nomes e números em algarismos mantidos.
- QA: 100 testes Python aprovados nos módulos extraídos do instalador, além dos cenários Swift. Ícones, dependências arm64 e checksum conferidos.

Versão experimental, com assinatura ad hoc, sem Developer ID Installer ou notarização Apple. M4 com 16 GB ainda não homologado; ensaios em M4 Pro com 24 GB. Microfone/projetor em ambiente real e instalação em outro Mac continuam pendentes.

O pacote inclui os runtimes; a primeira preparação baixa cerca de 6,3 GB de modelos. A inferência é local.
