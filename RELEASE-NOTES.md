# Vertere 0.10.5 — Apple Silicon

Build 22. Versão experimental compilada localmente. **Equilibrado permanece como padrão**; preferências salvas são respeitadas.

## Incluído desde a última publicação (0.7.2)

- Fonte de áudio selecionável: microfone ou áudio do sistema, para acompanhar vídeos e outros sons do Mac. A captura do sistema depende da autorização do macOS.
- Registro de sessão e exportação em PDF bilíngue lado a lado, SRT e WebVTT. A exportação pode ser feita ao encerrar a sessão; salve os registros antes de fechar o aplicativo.
- Modo Incremental opcional para francês → português, com prévias confirmadas e prioridade dos finais. Não garante atraso de até 2 segundos.
- Paginação adaptada a fontes grandes e legendas estreitas, até duas linhas e tempo de leitura preservado.
- Proteção de números por extenso na paginação e nas prévias. Sequências maiores que uma página continuam exigindo mais páginas.
- Correção contextual do provérbio “à quelque chose malheur est bon” no Incremental, inclusive com continuação, e da expressão de agressão “se fichent sur la gueule”.
- Menos fragmentos nos layouts estreitos, incluindo eliminação da palavra isolada “pactuar” nos casos avaliados. Contexto repetido precisa estar confirmado pelo final e não pode começar no meio de um número.

## Evidências e limites

No replay mais recente dos cinco trechos, os ajustes finais reduziram fragmentos de 15 para 14 em 600/60 e de 17 para 16 em 450/48, sem aumentar o p95 agregado de primeira exibição nessa gravação. Na gravação anterior, houve até aproximadamente 0,10 s adicional no p95. Todos os finais e o tempo de leitura foram preservados. São comparações controladas da apresentação, não medição ao vivo de microfone ou tela.

A proteção numérica anterior trouxe custo de até 0,24 s no p95 em relação ao paginador sem essa proteção. Persistem fragmentos e erros de reconhecimento/tradução fora dos casos avaliados. A espera experimental de números/complementos e o parser spaCy dos benchmarks **não estão ativados nos perfis do app** e não são dependências da distribuição.

## Distribuição

- Apple Silicon arm64; macOS 15 ou posterior.
- Ensaios locais em M4 Pro com 24 GB. M4 com 16 GB ainda não homologado.
- Python e motores incluídos; primeira preparação baixa cerca de 6,3 GB de modelos. Reserve 8 GB livres, além do aplicativo. Depois da preparação, inferência local sem serviço pago.
- Assinatura ad hoc; sem Developer ID Installer ou notarização Apple. O macOS pode bloquear a instalação ou abertura.
- QA do pacote não substitui avaliação de captura real, projeção em tela cheia ou instalação em outro Mac.
