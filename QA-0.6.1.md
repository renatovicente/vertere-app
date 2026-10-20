# QA do instalador Vertere 0.6.1

Data: 20 de outubro de 2026. Build 11, Apple Silicon arm64. Ensaio local em M4 Pro com 24 GiB.

## Resultado

**Regressões do pacote aprovadas; distribuição experimental, não notarizada.** O instalador foi gerado a partir de uma nova compilação local e extraído novamente para validação. A proteção contextual de nomes está incluída em `Engine/proper_names.pyc`. O teste exige que o módulo seja importado desse arquivo no pacote, antes da descoberta dos testes, evitando um falso resultado positivo com o código-fonte do workspace.

| Verificação | Resultado |
|---|---|
| Versão do bundle | 0.6.1, build 11 |
| Pipeline com Python e módulos extraídos do pacote | 81 testes aprovados |
| Preparação, opções e formatação com módulos do pacote | 17 testes aprovados |
| Controlador Swift de apresentação | Cenários aprovados; compilados das fontes compartilhadas com o app |
| Assinatura ad hoc do app extraído | Válida, verificação deep/strict |
| Binários e dependências | arm64; nenhuma dependência dinâmica de Homebrew ou diretório de usuário |
| Runtime Python, llama.cpp e CLI do motor | Carregamento aprovado; idiomas iguais rejeitados como esperado |
| Helper ASR sem argumentos | Erro de uso esperado; não executa inferência |
| Ícone ICNS e imagens no instalador | Presentes; verificação automática aprovada |
| SHA-256 | Confere com o pacote final |
| Developer ID Installer, Gatekeeper e ticket de notarização | Ausentes/reprovados; pendência conhecida |

Os 98 testes Python foram repetidos nos módulos distribuídos. Os testes Swift exercitam o controlador compartilhado, não automatizam uma sessão do aplicativo instalado. Não houve novo teste de áudio, tradução com modelos, memória, instalação em outro Mac ou projeção em tela cheia. O M4 com 16 GB continua sem homologação.

## Alterações incluídas desde a distribuição 0.3.2

- Opção de números em algarismos em português.
- Prévias cautelosas FR→PT, cache e reutilização exata de prévias concluídas nos finais.
- Exibição em até duas linhas, tempo reservado para leitura, três ritmos e agrupamento de fragmentos curtos.
- Proteção contextual restrita para Barthes e preservação da grafia Claudia. Não substitui Bart indiscriminadamente.

A origem do relato real “Barthes → Bart” continua sem confirmação: os trechos gravados não contêm a ocorrência. A proteção foi validada com exemplos sintéticos e replay sem alterações das respostas anteriores. Consulte [o relatório de nomes](https://github.com/renatovicente/vertere/blob/main/docs/nomes-proprios-fr-pt.md) e [o relatório de exibição](https://github.com/renatovicente/vertere/blob/main/docs/controle-exibicao-fr-pt.md).

## Artefato

- Arquivo: `Vertere-0.6.1-Apple-Silicon.pkg`.
- Tamanho: 37.052.115 bytes.
- SHA-256: `fcab1a406210cbafd30b778498b656a240c788282386435454681402a05253ff`.
- Download: https://github.com/renatovicente/vertere-app/releases/tag/v0.6.1

Os pesos não estão no pacote; a preparação inicial baixa cerca de 6,3 GB. A inferência permanece local.

Auditoria detalhada local: `results/qa-0.6.1/audit.json`. Comandos:

```sh
.local/venv/bin/python Native/scripts/build.py
.local/venv/bin/python Native/scripts/package.py
.local/venv/bin/python Native/scripts/qa.py 0.6.1
```
