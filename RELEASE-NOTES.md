# Vertere 0.7.2 — sentido e agrupamento no modo Rápido

- Equilibrado permanece como padrão para novas preferências. Escolhas salvas são respeitadas; a antiga opção cautelosa migra para Mais fiel.
- O app mostra versão e número do build junto ao nome Vertere: **Versão 0.7.2 · build 14**.
- Rápido francês → português aguarda continuações gramaticais, com limite de 6,4 s, para reduzir cortes como “pas juste institutionnelles” e “ça change pas la donne”. Desambigua também a expressão temporal “au lendemain de”.
- Agrupa finais curtos e reapresenta contexto literal quando uma palavra chega durante a leitura anterior. Preserva finais, até duas linhas e o tempo de leitura, incluindo o contexto repetido.
- Nos três trechos avaliados, zero páginas de uma palavra; início mediano/p95 de 5,07/6,33 s, contra 5,09/6,25 s na 0.7.1. A comparação de apresentação usa replay dos eventos de inferência gravados; não é medição ao vivo pelo microfone.
- As correções “não são apenas institucionais”, “isso não muda o jogo” e “ou dos parlamentos” foram preservadas. Ainda existem erros de reconhecimento e tradução fora dos casos monitorados.
- A repetição de contexto tem custo em alguns blocos: p95 de conclusão da leitura de 6,96 s, contra 6,41 s na 0.7.1. Respostas autônomas curtas permanecem separadas.
- QA: 111 testes Python nos módulos extraídos do instalador e cenários Swift de apresentação; ícones, arquitetura arm64, dependências e checksum conferidos.

Versão experimental, com assinatura ad hoc, sem Developer ID Installer e sem notarização Apple. O macOS pode bloquear a instalação. M4 com 16 GB ainda não homologado; ensaios anteriores em M4 Pro com 24 GB. Instalação em outro Mac e sessão real de microfone/projetor continuam pendentes.

O pacote inclui os runtimes; a primeira preparação baixa cerca de 6,3 GB de modelos. A inferência permanece local. O QA de empacotamento não repete a inferência de áudio.
