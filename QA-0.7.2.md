# QA do instalador Vertere 0.7.2

Data: 21 de outubro de 2026. Build 14, arm64, macOS 15 ou posterior. Ensaio em M4 Pro com 24 GiB.

## Resultado

**Regressões do pacote aprovadas; distribuição experimental, não notarizada.** O aplicativo foi recompilado após a inclusão da versão na interface, empacotado e extraído novamente para testar os módulos distribuídos.

| Verificação | Resultado |
|---|---|
| Bundle | 0.7.2, build 14 |
| Versão na interface | “Versão 0.7.2 · build 14”, confirmada pela árvore de acessibilidade do app empacotado aberto |
| Pipeline extraído | 92 testes aprovados |
| Preparação, opções e formatação extraídas | 19 testes aprovados |
| Apresentação Swift | Cenários aprovados, incluindo palavras isoladas, contexto, negação, leitura e finais |
| Três velocidades | CLI aceita faithful, balanced e fast; testes verificam políticas e escopo FR→PT |
| Assinatura ad hoc do app | Verificação deep/strict aprovada |
| Arquitetura e dependências | arm64; nenhuma dependência dinâmica de Homebrew ou diretório de usuário |
| Runtimes e CLI | Python, llama.cpp, helper ASR e erros esperados conferidos |
| Ícones e recursos do instalador | Verificação automática aprovada |
| SHA-256 | Confere com o pacote final |
| Developer ID Installer, Gatekeeper e notarização | Assinatura de distribuição e ticket ausentes; Gatekeeper reprova |

Os 111 testes Python pré-carregam o bytecode extraído antes da descoberta. Os cenários Swift usam as fontes compartilhadas pelo app, sem automatizar uma sessão de tradução instalada.

## Preferências e mudanças

**Equilibrado permanece padrão para novas preferências.** Preferências salvas são preservadas; a opção cautelosa antiga migra para Mais fiel. A inspeção de interface usou as preferências existentes, sem alterá-las; o padrão foi conferido na inicialização em `SessionModel.swift`.

O modo Rápido inclui espera gramatical limitada a 6,4 s e orientação para a expressão temporal “au lendemain de”. Agrupa finais curtos disponíveis e reapresenta contexto literal quando uma palavra chega durante a leitura anterior. Mantém finais e tempo de leitura. Versão e build são lidos do Info.plist e exibidos junto ao nome do app.

Nos mesmos trechos, a apresentação ajustada teve início mediano/p95 de 5,07/6,33 s, contra 5,09/6,25 s na 0.7.1, com zero páginas de uma palavra. Foram preservadas as correções “não são apenas institucionais”, “isso não muda o jogo” e “ou dos parlamentos”. A leitura completa p95 foi de 6,96 s, contra 6,41 s: há custo em alguns blocos. Permanecem erros de reconhecimento e tradução fora dos casos monitorados.

## Limites

Esta rodada de empacotamento não repetiu inferência, áudio ou memória. A comparação anterior usa inferência gravada e replay determinístico. Não houve instalação em outro Mac ou sessão de microfone/projetor. A abertura do app confirmou a versão na interface, sem iniciar sessão. Recursos do instalador foram verificados automaticamente; não houve nova inspeção visual do Installer. M4/16 GB permanece sem homologação. Assinatura ad hoc, sem Developer ID Installer nem notarização.

## Artefato

- Arquivo: `Vertere-0.7.2-Apple-Silicon.pkg`.
- Tamanho: 37,061,454 bytes.
- SHA-256: `095b2ec8dd28a1d4b352db562dbdb9cda74bed7fc8582af3ba5041e5dae8a893`.
- [Download e checksum](https://github.com/renatovicente/vertere-app/releases/tag/v0.7.2).

Os modelos são baixados separadamente na primeira preparação; inferência local.

Auditoria detalhada local: `results/qa-0.7.2/audit.json`. A auditoria registra o commit anterior e a árvore com as alterações de release antes do commit final.

```sh
.local/venv/bin/python Native/scripts/build.py
.local/venv/bin/python Native/scripts/package.py
.local/venv/bin/python Native/scripts/qa.py 0.7.2
```
