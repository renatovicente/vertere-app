# Vertere

**Sua apresentação, em outras línguas.**

Aplicativo nativo macOS de legendas sobre PDF, PowerPoint e outras apresentações, com reconhecimento de voz e tradução locais. Interface com design PSKR.

Este repositório distribui somente o instalador compilado, instruções e avisos de licença. O código-fonte do Vertere não é publicado aqui.

## Download

[Baixar Vertere 0.3.2 para Apple Silicon (.pkg)](https://github.com/renatovicente/vertere-app/releases/download/v0.3.2/Vertere-0.3.2-Apple-Silicon.pkg)

[Todos os arquivos da versão e checksum SHA-256](https://github.com/renatovicente/vertere-app/releases/tag/v0.3.2)

**Versão experimental, sem notarização Apple.** O aplicativo tem assinatura local ad hoc; o pacote não tem assinatura Developer ID Installer. O macOS pode bloquear ou solicitar autorização para a instalação/abertura. Se você decidiu instalar esta versão, use as opções apresentadas pelo macOS em Ajustes do Sistema → Privacidade e Segurança. Não é necessário desativar globalmente as proteções do sistema.

## Requisitos e limites

- Mac Apple Silicon (arm64), voltado ao M4; não funciona em Macs Intel.
- macOS 15 ou posterior como alvo de compilação.
- Reserve 8 GB de armazenamento livre para os modelos, além do aplicativo.
- Internet na primeira preparação: aproximadamente 6,3 GB de download dos modelos pelo Hugging Face. Não exige conta ou serviço de inferência pago.
- Ensaios anteriores dos modelos foram realizados em M4 Pro com 24 GB. **M4 com 16 GB ainda não homologado.**
- O pacote foi gerado localmente; instalação em outro Mac, captura real e apresentação em tela cheia ainda precisam de avaliação. Compilação não equivale a homologação.

## Instalação e primeiro uso

1. Encerre qualquer versão anterior do Vertere.
2. Abra o `.pkg` e conclua a instalação. O aplicativo fica em `/Applications/Vertere.app`.
3. Abra o Vertere, selecione os idiomas e clique em **Iniciar sessão**. Autorize o microfone quando solicitado.
4. Na primeira sessão, aguarde a preparação dos modelos indicada na interface. O aplicativo confere SHA-256 dos arquivos. Se interromper, inicie novamente para retomar o download.
5. Quando o status indicar que está ouvindo, fale no microfone padrão do Mac. A captura só começa após o carregamento dos modelos.
6. Escolha o monitor/projetor, abra seu PDF ou apresentação e ajuste posição, fonte, cores e fundo das legendas.

Python, Core ML e llama.cpp/Metal estão incluídos no aplicativo. Não é necessário instalar Homebrew, Python, Xcode ou clonar o projeto. Os modelos ficam em `~/Library/Application Support/Vertere/Models`. Depois da preparação, a sessão funciona offline; áudio e transcrições não são enviados a serviços de tradução.

Os menus oferecem francês, português, inglês, espanhol, alemão, italiano, neerlandês e polonês como origem e destino. Apenas francês → português foi avaliado nos benchmarks; outros pares são experimentais.

## Modelos e licenças

- [Nemotron 3.5 ASR 0.6B Core ML INT8](https://huggingface.co/aufklarer/Nemotron-3.5-ASR-Streaming-0.6B-CoreML-INT8), revisão `447095fe87b480b5e6a15367f135303d479de8ac`.
- [Qwen3.5 9B Q4_K_M](https://huggingface.co/unsloth/Qwen3.5-9B-GGUF), revisão `3885219b6810b007914f3a7950a8d1b469d598a5`.

Os pesos são baixados das fontes acima, não estão no instalador. Os avisos de licença das dependências estão em `Vertere.app/Contents/Resources/Licenses`, incluindo fontes Inter e Space Mono, Python, llama.cpp e bibliotecas Swift. A publicação deste binário não concede uma licença de código aberto ao código proprietário do Vertere; os direitos e licenças dos componentes de terceiros são preservados.

## Remoção

Encerre o Vertere e remova o aplicativo de Aplicativos. Para liberar o espaço dos modelos, remova também `~/Library/Application Support/Vertere/Models` pelo Finder. As preferências de aparência e idiomas são armazenadas pelo macOS separadamente.
