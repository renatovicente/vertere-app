# Vertere 0.6.1 — legendas e proteção contextual de nomes

- Até duas linhas por bloco, tempo reservado para leitura e agrupamento de fragmentos curtos.
- Ritmos Mais tempo, Equilibrado e Mais ágil.
- Opção de números em algarismos para português.
- Prévias cautelosas FR→PT com cache e reaproveitamento exato de prévias concluídas.
- Proteção contextual de Barthes e da grafia Claudia; Bart não é substituído indiscriminadamente.
- QA do pacote: 81 testes do pipeline e 17 do motor, executados com o Python e módulos extraídos do instalador. Cenários Swift de exibição também aprovados.

O erro real “Barthes → Bart” ainda não foi localizado no áudio. As regras de nomes foram testadas com exemplos sintéticos; o replay dos trechos anteriores preservou todas as respostas. Não houve nova inferência nesta rodada de empacotamento.

Versão experimental, com assinatura ad hoc e sem notarização Apple ou Developer ID Installer. M4 com 16 GB ainda não homologado; ensaios em M4 Pro com 24 GB. Instalação em outro Mac, microfone e projeção em tela cheia continuam pendentes.

Os modelos são baixados na primeira preparação (cerca de 6,3 GB); a inferência é local. Consulte o README antes de instalar.
