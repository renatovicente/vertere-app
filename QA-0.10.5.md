# QA do pacote Vertere 0.10.5

22/10/2026 · build 22 · Apple Silicon arm64.

**Resultado: pacote e regressões aprovados para distribuição experimental. Sem notarização Apple.**

## Artefato

- `Vertere-0.10.5-Apple-Silicon.pkg`
- Tamanho: 37.125.046 bytes.
- SHA-256: `b3daecc870a1a5bd0974bbd7af81ec9891ffe8e7460c90fe4ba59cdfd3b2dd45`
- Modelos baixados separadamente: 6.322.719.407 bytes.

## Verificações aprovadas

- Extração completa do pacote; uma aplicação Vertere, versão 0.10.5/build 22.
- Assinatura ad hoc do app válida com `codesign --verify --deep --strict`.
- Ícone do aplicativo e imagens/referências de boas-vindas do instalador presentes.
- Python embutido funcional, incluindo SSL; carregamento do llama-server e CLI do motor.
- Modos Mais fiel, Equilibrado, Rápido e Incremental aceitos pela CLI; argumentos de algarismos e prévias cautelosas reconhecidos.
- **158 testes do pipeline e 19 testes nativos**, executados usando os módulos compilados extraídos do instalador; suíte Swift de apresentação aprovada.
- **24 arquivos Mach-O, todos arm64**, sem dependências locais de `/Users` ou Homebrew. Alvo mínimo do app macOS 15; componentes Python compatíveis também contêm alvo mínimo 11.
- Checksum do instalador confere com `SHA256SUMS.txt`.
- Equilibrado permanece padrão; o Incremental continua opcional. Experimentos de parser/espera seletiva dos benchmarks não foram ativados no app.

## Limites e resultados esperados

- O pacote não possui assinatura Developer ID Installer. Gatekeeper rejeita com `no usable signature`; não há ticket de notarização. Esses resultados são conhecidos, não aprovação pela Apple.
- A chamada do ASR sem argumentos retorna erro de uso esperado; a CLI é carregável, mas isso não testa microfone real.
- Este QA não instala o pacote em outro Mac, não repete a inferência nem homologa captura real de microfone/áudio do sistema, projeção em tela cheia ou exportação em sessão de cliente.
- Compilação local em M4 Pro com 24 GB. M4 de 16 GB ainda não homologado.
- A melhoria de fragmentos foi validada anteriormente em replays dos cinco trechos e três layouts. Finais e leitura foram preservados; houve custo de até ~0,10 s no p95 em uma das gravações. Não é promessa de tradução com atraso máximo de 2 s.

Auditoria bruta local em `results/qa-0.10.5/audit.json`. As notas de versão descrevem as funções acumuladas desde a última publicação, 0.7.2. O QA foi executado antes do commit de release; a auditoria registra esse estado de trabalho.
