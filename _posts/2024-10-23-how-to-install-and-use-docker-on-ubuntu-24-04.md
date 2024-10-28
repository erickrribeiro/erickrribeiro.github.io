---
title: "Como instalar o Docker no Ubuntu 24.04"
date: 2024-10-23T00:00-00:00
last_modified_at: 2024-10-23T00:00-00:00
categories:
  - docker
  - linux

permalink: /seo/guia-de-instalacao-do-docker-no-ubuntu-24-04
classes: wide
excerpt: Aprenda a instalar e usar o Docker para criar ambientes isolados em containers, facilitando a execução de aplicações. O guia cobre a instalação do Docker CE no Ubuntu 24.04, com e sem permissões de administrador.
---

# Introdução

Docker é uma plataforma de software que facita a criação, o teste e a implantação de aplicações rapidamente. Sua proposta é simplificar e modularizar o empacotamento 
de aplicações, tornando o processo mais prático e direto. Com o uso do Docker, as aplicações e todas as suas dependências são isoladas em containers, que funcionam 
de maneira semelhante a máquinas virtuais. Dentro de um container, uma aplicação tem acesso a tudo que precisa para ser executada, incluindo bibliotecas, variáveis 
de ambiente e o próprio código-fonte da aplicação.

Para uma introdução detalhada sobre os diferentes componentes de um container Docker, recomendo o livro [Docker para desenvolvedores](https://leanpub.com/dockerparadesenvolvedores). É gratuito e está disponível em português.

Neste tutorial, você irá aprender a como instalar e utilizar o Docker Community Edition (CE) no Ubuntu 24.04, tanto com permissões do administrador (sudo) quando sem elas.

# Pré-requisitos

Para seguir este tutorial, você vai precisar de:
- Uma máquina com o sistema operacional **Ubuntu 24.04** instalado, incluindo um usuário sudo.
- Acesso à **internet**
- Um **script para instalação do Docker**

Se você já instalou o Docker anteriormente e está apenas buscando uma maneira rápida de reinstalá-lo, basta executar o comando abaixo para automatizar o processo:

```bash
$ wget -O - https://gist.githubusercontent.com/erickrribeiro/d67cdbe13b7593aec777214ed6df9aeb/raw/62e5fb6639ed778e87e4717b7a8f54078ac2de4c/install-docker-on-ubuntu-18-via-script.sh | bash
```

O script anterior facilita a instalação ao eliminar a necessidade de realizar cada etapa manualmente, garantindo que o Docker seja instalado corretamente no seu ambiente Ubuntu 24.04. Se você quer realizar o processo de instalação passo a passo, continue a leitura.

## Passo a passo de como instalar o Docker 

Normalmente, o repositório oficial de instalação de pacotes do Ubuntu não possui a versão mais recente do Docker. Para garantir que você utilize a versão mais atualizada, é recomendável instalá-lo diretamente do repositório oficial do Docker.

### Passo 1: Atualize a lista de pacotes do Ubuntu.

Comece atualizando a lista de pacotes disponíveis no APT (Advanced Package Tool). O APT é o gerenciador de pacotes padrão para distribuições baseadas em Debian, 
como o Ubuntu. Ele facilita a instalação, atualização e remoção de pacotes de software, gerenciando automaticamente as dependências. Para atualizar os pacotes, 
abra o terminal e execute o comando a seguir:

```bash
sudo apt update
```

### Passo 2: Instale pacotes de apoio

Em seguida, instale alguns pacotes necessários para que o APT utilize pacotes via HTTPS. Execute o comando a seguir: 

```bash
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

### Passo 3: Adicione a chave GPG 

Para garantir a segurança, execute o comando a seguir. Adicionar a chave GPG oficial do Docker permite que o APT verifique a autenticidade dos pacotes baixados. Isso porque, a chave GPG usa criptografia assimétrica, com uma chave pública e uma chave privada para proteger as transferências.

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

### Passo 4: Adicione o repositório oficial do Docker no APT

Para garantir que você tenha acesso às versões mais recentes do Docker, é necessário adicionar o repositório oficial do Docker ao APT, já que os repositórios padrão do Ubuntu podem não conter as versões mais recentes. Ao adicionar o repositório oficial do Docker, você assegura que o APT buscará as versões mais estáveis e atualizadas diretamente da fonte oficial.
Para o Ubuntu 24.04, adicione o repositório executando o comando abaixo:

```bash
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu noble stable"
```

Mais detalhes sobre comando:

- **deb**: Indica que estamos adicionando um repositório de pacotes pré-compilados no formato `.deb`.
- **[arch=amd64]**: Especifica a arquitetura do sistema, no caso, 64 bits. Certifique-se de ajustar esse parâmetro se estiver usando uma arquitetura diferente.
- **https://download.docker.com/linux/ubuntu**: URL do repositório oficial do Docker.
- **noble**: Codinome do Ubuntu 24.04. Para outras versões do Ubuntu, ajuste este campo para o nome correspondente da sua versão.
- **stable**: Optamos pelo canal estável do Docker, o que significa que você instalará versões testadas e prontas para uso em produção.

Agora, o APT estará quase preparado para buscar e instalar a versão mais recente do Docker diretamente do repositório oficial. Antes de seguir para a instalação, 
atualize a lista de pacotes novamente para que o sistema reconheça os pacotes mais recentes do Docker:

```bash
sudo apt update
```

### Passo 5: Instale o Docker

Agora que você adicionou o repositório oficial do Docker, pode instalar a versão mais recente do Docker Community Edition (CE) diretamente do repositório. Para isso, execute o seguinte comando:

```bash
sudo apt install docker-ce
```

Isso instalará o Docker CE e suas dependências diretamente do repositório oficial, garantindo que você tenha a versão mais atualizada e estável do software. Após 
a instalação, é importante verificar se o Docker Engine foi instalado corretamente. Para isso, o comando a seguir:

```bash
sudo docker run hello-world
```

O comando anterior faz o download de uma pequena imagem de teste e a executa dentro de um container. Quando o container for executado, ele imprimirá uma mensagem de confirmação no terminal e, em seguida, será encerrado. Se você visualizar a mensagem de sucesso semelhante a esta:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

Isso indica que o Docker foi instalado com sucesso e está funcionando corretamente em seu sistema.


### Configuração Opcional

Por padrão, o comando `docker` só pode ser executado pelo usuário root ou por um usuário que faça parte do grupo `docker`, criado automaticamente durante a instalação. Se você tentar rodar o Docker sem as permissões adequadas, verá uma mensagem de erro como esta:

```
docker: Cannot connect to the Docker daemon. Is the docker daemon running on this host?.
See 'docker run --help'.
```

Para evitar a necessidade de usar o `sudo` toda vez que executar o comando `docker`, você pode adicionar seu usuário ao grupo `docker`. Isso permitirá que você execute comandos do Docker diretamente, sem precisar de permissões de superusuário.

Execute o seguinte comando para adicionar seu usuário ao grupo `docker`:

```bash
sudo usermod -aG docker $(whoami)
```

Após isso, é necessário fazer logout e login novamente ou reiniciar a sessão para que as alterações tenham efeito. Depois de reiniciar, teste o Docker novamente, desta 
vez sem usar `sudo`, para garantir que a configuração foi aplicada corretamente:

```bash
docker run hello-world
```

Se a imagem de teste `hello-world` rodar com sucesso e você visualizar a mensagem de confirmação, isso significa que a configuração foi bem-sucedida, e você pode utilizar o Docker sem precisar de `sudo` para cada comando.

# Conclusão
Neste tutorial, você aprendeu duas maneiras de instalar o Docker no Ubuntu 18.04. A primeira, utilizando um script bash, é rápida e conveniente, ideal para quem busca praticidade e agilidade. Já a segunda forma, mais detalhada, foi desenvolvida em formato de tutorial para guiá-lo no processo passo a passo.

Como sugestão para aprofundar seus conhecimentos, recomendo a leitura do livro Docker para desenvolvedores, onde você pode aprender desde os fundamentos até conceitos avançados do Docker

