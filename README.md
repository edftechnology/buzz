# Como instalar/configurar/usar o `Buzz` no `Linux Ubuntu`

## Resumo

Este guia descreve como instalar, verificar, usar e remover o `Buzz` no
`Linux Ubuntu` pelo `Snap`. O pacote do aplicativo é distribuído na
`Snap Store`; `apt` é usado somente para instalar dependências de 
integração gráfica e áudio indicadas pelo projeto _upstream_.

## _Abstract_

_This guide describes how to install, verify, use, and remove Buzz on
`Linux Ubuntu` through `Snap`. The application is distributed through
the `Snap Store`; `apt` is used only to install audio and graphical 
integration dependencies listed by the upstream project._

## Descrição

### `Buzz`

O `Buzz` é um aplicativo de transcrição e tradução de áudio e vídeo
baseado em mecanismos `Whisper`. O projeto informa suporte a arquivos de
áudio e vídeo, gravação pelo microfone e exportação de transcrições; os
formatos e recursos disponíveis podem variar conforme a versão instalada.

## Pré-requisitos

- `Linux Ubuntu` com `apt` funcional.

- Permissão para usar `sudo` caso seja necessário instalar dependências do sistema.

- Conexão com a _internet_ para consultar repositórios ou obter o aplicativo.

- `snapd` instalado e ativo; verificar com `snap version`.

## Instalação

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```text
    Ctrl + Alt + T
    ```

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. 
    Especificamente, ele remove todos os arquivos de pacotes (`.deb`) 
    baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`.
    Digite o seguinte comando:

    ```bash
    sudo apt clean
    ```

    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local.
    É útil para liberar espaço, pois remove apenas os pacotes que não
    podem mais ser baixados (ou seja, versões antigas de pacotes que
    foram atualizados). Digite o seguinte comando:

    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para
    satisfazer as dependências de outros pacotes e que não são mais
    necessários. Digite o seguinte comando:

    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizações disponíveis para os pacotes que estão
    instalados em seu sistema. Digite o seguinte comando e pressione
    `Enter`:

    ```bash
    sudo apt update
    ```

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de
    pacotes disponíveis e tentará corrigir pacotes quebrados ou com
    dependências ausentes:

    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar o `cache` do gerenciador de pacotes `apt` novamente:

    ```bash
    sudo apt clean
    ```

    2.7 Para ver a lista de pacotes a serem atualizados, digite o
    seguinte comando e pressione `Enter`:

    ```bash
    sudo apt list --upgradable
    ```

    2.8 Realmente atualizar os pacotes instalados para as suas versões
    mais recentes, com base na última vez que você executou
    `sudo apt update`. Digite o seguinte comando e pressione `Enter`:

    ```bash
    sudo apt full-upgrade -y
    ```

Os comandos de manutenção do item 2 são separados da instalação do
`Buzz` e não foram executados. Em particular, `apt autoremove` pode
remover dependências de outros aplicativos, e `apt full-upgrade` pode
atualizar ou remover pacotes do sistema; revisar as propostas do `apt`
antes de confirmá-las.

3. Atualizar os índices de pacotes e instalar as dependências de
áudio/gráficas indicadas pelo projeto:

    ```bash
    sudo apt update
    sudo apt-get install libportaudio2 libcanberra-gtk-module libcanberra-gtk3-module -y
    ```

4. Instalar o aplicativo Buzz pela Snap Store:

    ```bash
    sudo snap install buzz
    ```

5. Confirmar a instalação:

    ```bash
    snap list buzz
    ```

### Código completo para configurar/instalar/usar

1. Abrir o `Terminal Emulator` com `Ctrl + Alt + T`.
2. Copiar e colar o bloco abaixo. O `apt` instala somente dependências;
o `Buzz` é instalado pelo `Snap`.

    ```bash
    sudo apt update
    sudo apt-get install libportaudio2 libcanberra-gtk-module libcanberra-gtk3-module -y
    sudo snap install buzz
    snap list buzz
    ```

## Verificação da instalação

1. Verificar se o `Snap` está instalado e consultar a revisão instalada:

    ```bash
    snap list buzz
    ```

    A saída deve identificar o pacote `buzz` e sua revisão; não presumir
    um número de versão específico. Para abrir o aplicativo,
    selecioná-lo no menu de aplicativos do ambiente gráfico.

## Configuração e utilização

A documentação _upstream_ descreve a importação de arquivos de áudio e
vídeo, seleção de um mecanismo/modelo de reconhecimento e exportação do
texto. As opções concretas dependem da versão e do formato instalado.
Consultar a documentação oficial antes de processar arquivos
confidenciais ou configurar serviços de nuvem: o projeto também
documenta uso opcional da API OpenAI, que envia áudio ao serviço remoto.

## Desinstalação

1. Verificar a instalação e confirmar que o aplicativo veio do Snap:

    ```bash
    snap list buzz
    ```

2. Remover o aplicativo pelo mesmo gerenciador:

    ```bash
    sudo snap remove buzz
    ```

3. Verificar a remoção:

    ```bash
    snap list buzz
    ```

   Após a remoção, o `Snap` deve informar que não há pacote `buzz`
   instalado. A remoção do `Snap` não garante a exclusão de todos os
   dados pessoais ou modelos eventualmente baixados; revisar esses dados
   separadamente antes de apagá-los. `apt remove` e `apt purge` não se
   aplicam ao aplicativo instalado como Snap.

### Código completo para desinstalar

1. Abrir o `Terminal Emulator`:

    ```bash
    Ctrl + Alt + T
    ```

2. Copiar e colar o bloco abaixo. A primeira consulta permite confirmar
o pacote antes da remoção; a última confirma o estado posterior.

    ```bash
    snap list buzz
    sudo snap remove buzz
    snap list buzz
    ```

## Compatibilidade

O sistema inspecionado é `Linux Ubuntu 22.04.5 LTS` (`Jammy`). O projeto
_upstream_ e a `Snap Store` documentam a distribuição do `Buzz` para
`Linux Ubuntu` pelo `Snap`. As dependências do sistema são instaladas
via `apt`, mas o aplicativo em `si` é o Snap `buzz`.

## Licença

O projeto upstream do Buzz declara licença MIT. A licença deste
repositório de documentação está no arquivo `LICENSE.txt`; são escopos
distintos.

## Contato e suporte

Consultar o [repositório oficial do Buzz](https://github.com/chidiwilliams/buzz) e a [documentação do Buzz](https://chidiwilliams.github.io/buzz/).

## Referências

[1] CHIDI WILLIAMS.
**Buzz**.
Disponível em: <https://github.com/chidiwilliams/buzz>.
GitHub.
Acessado em: 30/10/2026.

[2] CANONICAL.
**Install Buzz on Linux**.
Disponível em: <https://snapcraft.io/buzz>.
Snap Store.
Acessado em: 30/10/2026.

[3] OPENAI.
**Como instalar o Buzz no Linux Ubuntu pelo Terminal Emulator**.
Disponível em: <https://chatgpt.com/g/g-p-6980caf949648191ad6acfcdbe590f9e-instalar/c/6ae4b306-4f84-83e9-b3e4-61a025034ba3>.
ChatGPT. Conteúdo não acessado: a página não foi recuperada nesta sessão.
Acessado em: 30/10/2026.
