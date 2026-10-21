# Vertere 0.7.1 — menor atraso no modo rápido

- Equilibrado continua como padrão para novas preferências. Escolhas já salvas são respeitadas; a antiga opção cautelosa migra para Mais fiel.
- O modo rápido traduz diretamente grupos de até quatro segundos, sem prévias intermediárias redundantes.
- Melhor aproveitamento de espaço entre finais, mantendo duas linhas e o tempo de leitura escolhido. Nenhum final é descartado para acelerar a fila.
- No ensaio anterior, a mediana de início de exibição caiu de 7,01 s (Equilibrado) para 5,03 s (rápido); p95 de 8,38 para 6,40 s. Foram novas execuções locais dos modelos seguidas de replay da exibição, não uma medição pelo microfone.
- Há custo de qualidade: “não são justas” reapareceu no lugar de “não são apenas”, além de outros erros de contexto. Equilibrado permanece recomendado como padrão.
- QA de distribuição: 103 testes Python nos módulos extraídos do instalador e cenários Swift de apresentação aprovados; ícones, dependências arm64 e checksum conferidos.

Versão experimental, com assinatura ad hoc, sem Developer ID Installer e sem notarização Apple. O macOS pode bloquear a instalação. M4 com 16 GB ainda não homologado; ensaios em M4 Pro com 24 GB. Instalação em outro Mac e sessão real de microfone/projetor continuam pendentes.

O pacote inclui os runtimes; a primeira preparação baixa cerca de 6,3 GB de modelos. A inferência permanece local. Esta rodada de empacotamento não repetiu os ensaios de áudio.
