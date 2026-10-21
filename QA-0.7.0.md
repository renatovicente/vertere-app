# QA do instalador Vertere 0.7.0

Data: 21 de outubro de 2026. Build 12, arm64, macOS 15 ou posterior. Ensaio em M4 Pro com 24 GiB.

## Resultado

Regressões do pacote aprovadas. Nova compilação, empacotamento e extração integral para testar os módulos distribuídos.

| Verificação | Resultado |
|---|---|
| Bundle | 0.7.0, build 12 |
| Pipeline nos módulos extraídos | 81 testes aprovados |
| Preparação, opções e formatação nos módulos extraídos | 19 testes aprovados |
| Modos faithful, balanced e fast | CLI aceita os três; testes conferem políticas e escopo FR→PT |
| Controlador Swift compartilhado com o app | Cenários aprovados, incluindo agrupamento, sufixos contextuais e preservação de finais |
| Assinatura ad hoc do app | Verificação deep/strict aprovada |
| Arquitetura e dependências | arm64; sem dependências dinâmicas de Homebrew ou diretório de usuário |
| Python, llama.cpp, helper e CLI | Carregamento e erros de uso esperados conferidos |
| Ícones e recursos do instalador | Verificação automática aprovada |
| SHA-256 | Confere com o pacote final |
| Developer ID Installer e notarização | Ausentes; Gatekeeper reprova, conforme esperado |

O QA pré-carrega o bytecode do pacote antes da descoberta dos testes, inclusive a proteção de nomes. Os cenários Swift são compilados das fontes compartilhadas; não automatizam uma sessão do aplicativo instalado.

## Padrão e comportamento

**Equilibrado é o padrão para novas preferências.** A velocidade já salva é respeitada. Usuários que haviam habilitado a antiga opção de prévias cautelosas migram para Mais fiel. O instalador não apaga preferências.

Velocidade das legendas é independente do ritmo de leitura. O modo rápido antecipa traduções, mas não garantiu menor atraso visível no ensaio. Os blocos são menores; fragmentos podem se juntar ao início de frases longas, e sufixos curtos podem reaparecer com contexto já lido. A proteção de nomes da versão 0.6.1 está incluída.

Na comparação anterior dos três trechos, o primeiro bloco exibido teve mediana/p95 de 7,05/9,67 s (Mais fiel), 7,03/8,40 s (Equilibrado) e 7,45/8,68 s (Mais rápido). Os cinco erros monitorados reapareceram nas saídas intermediárias do modo rápido; a regra de tela livre os ocultou naquele replay, sem garantia semântica para outros áudios. [Método e resultados](https://github.com/renatovicente/vertere/blob/main/docs/velocidade-legendas-fr-pt.md).

## Limites

Esta rodada repetiu o QA do pacote, sem nova inferência, medição de memória, instalação em outro Mac ou sessão de microfone/projetor. Não houve nova inspeção visual do Installer; os recursos foram conferidos automaticamente. M4 com 16 GB continua sem homologação. Distribuição experimental e não notarizada.

## Artefato

- Arquivo: `Vertere-0.7.0-Apple-Silicon.pkg`.
- Tamanho: 37.054.338 bytes.
- SHA-256: `a13559d5afe7245c18638b12de02fc41b95ce55d032b85016d1c8f2d2fb40191`.
- [Download e checksum](https://github.com/renatovicente/vertere-app/releases/tag/v0.7.0).

Os modelos são baixados separadamente na preparação inicial; não há inferência externa.

Auditoria detalhada local em `results/qa-0.7.0/audit.json`.

```sh
.local/venv/bin/python Native/scripts/build.py
.local/venv/bin/python Native/scripts/package.py
.local/venv/bin/python Native/scripts/qa.py 0.7.0
```
