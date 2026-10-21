# QA do instalador Vertere 0.7.1

Data: 21 de outubro de 2026. Build 13, arm64, macOS 15 ou posterior. Ensaio em M4 Pro com 24 GiB.

## Resultado

**Regressões do pacote aprovadas; distribuição experimental, não notarizada.** O aplicativo foi recompilado, empacotado e extraído novamente para testar os módulos efetivamente distribuídos.

| Verificação | Resultado |
|---|---|
| Bundle | 0.7.1, build 13 |
| Pipeline nos módulos extraídos | 84 testes aprovados |
| Preparação, opções e formatação nos módulos extraídos | 19 testes aprovados |
| Três velocidades | CLI aceita faithful, balanced e fast; testes verificam as políticas e o escopo FR→PT |
| Novo rápido | Testes verificam fechamento antecipado, ausência de prévias e cobertura contínua das palavras |
| Apresentação Swift | Cenários aprovados, incluindo tempo de leitura e agrupamento de finais sem perda |
| Assinatura ad hoc do app | Verificação deep/strict aprovada |
| Arquitetura e dependências | arm64; nenhuma dependência dinâmica de Homebrew ou diretório de usuário |
| Runtimes e CLI | Python, llama.cpp, helper ASR e erros de uso esperados conferidos |
| Ícones e recursos | Verificação automática aprovada |
| SHA-256 | Confere com o pacote final |
| Developer ID Installer, Gatekeeper e notarização | Assinatura de distribuição e ticket ausentes; Gatekeeper reprova |

Os testes Python pré-carregam o bytecode extraído antes da descoberta dos testes. Os cenários Swift usam as fontes compartilhadas pelo app; não automatizam uma sessão do aplicativo instalado.

## Preferências e alterações

**Equilibrado permanece como padrão para novas preferências.** Escolhas já salvas são respeitadas; usuários da antiga opção cautelosa migram para Mais fiel. O instalador não apaga preferências.

O rápido agora traduz diretamente grupos de até 4 s, sem prévias intermediárias, e aproveita melhor o espaço entre finais. Mantém duas linhas, o ritmo de leitura escolhido e todos os finais. No ensaio anterior, a mediana/p95 de início de exibição foi de 5,03/6,40 s no rápido, contra 7,01/8,38 s no Equilibrado. O teste combinou inferência local nova com replay determinístico da exibição.

O ganho tem custo: houve “não são justas” no lugar de “não são apenas”, além de outros erros por falta de contexto. A distribuição não implica qualidade semântica equivalente entre os modos. [Método, resultados e exemplos](https://github.com/renatovicente/vertere/blob/main/docs/rapido-atraso-tela-fr-pt.md).

## Limites do QA

Esta rodada não repetiu os ensaios de áudio, memória ou inferência. Não houve instalação em outro Mac, sessão de microfone/projetor ou nova inspeção visual do Installer. Recursos de imagem foram conferidos automaticamente. O M4 com 16 GB continua sem homologação. O aplicativo usa assinatura ad hoc; o instalador não é assinado com Developer ID Installer nem notarizado.

## Artefato

- Arquivo: `Vertere-0.7.1-Apple-Silicon.pkg`.
- Tamanho: 37.054.922 bytes.
- SHA-256: `f50c2668eed99ab0aed2b176469b9c187d4c0bf4825c9f7f81949db08c5105cc`.
- [Download e checksum](https://github.com/renatovicente/vertere-app/releases/tag/v0.7.1).

Os modelos são baixados separadamente na primeira preparação. A inferência permanece local.

Auditoria detalhada local: `results/qa-0.7.1/audit.json`.

```sh
.local/venv/bin/python Native/scripts/build.py
.local/venv/bin/python Native/scripts/package.py
.local/venv/bin/python Native/scripts/qa.py 0.7.1
```
