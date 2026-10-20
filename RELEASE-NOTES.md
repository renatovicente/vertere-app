# Vertere 0.3.2 — correções de instalação

- Retomada de download calcula apenas os bytes restantes, sem contar novamente o parcial já armazenado.
- Arquivos completos válidos são aproveitados mesmo com pouco espaço livre; arquivos corrompidos continuam rejeitados.
- Ícone incluído no pacote e declarado para as aparências clara e escura do Installer; renderização em modo escuro confirmada.
- Verificação automática dos recursos do `.pkg` passa a fazer parte do build.
- QA: 30 testes do pipeline e 10 de preparação passaram no código e nos módulos extraídos do instalador.

Versão experimental. Pacote ainda sem assinatura Developer ID Installer e sem notarização Apple. Não houve nova avaliação de inferência, microfone ou M4 com 16 GB.
