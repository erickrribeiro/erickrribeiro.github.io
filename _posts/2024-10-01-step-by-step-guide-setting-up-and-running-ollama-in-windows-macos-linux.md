---
title: "Guia de instalação e uso do Ollama"
date: 2024-10-01T00:00-00:00
last_modified_at: 2024-10-21T00:00:00-00:00
categories:
  - ollama
  - llm
  - genai

permalink: /guia/guia-de-instalacao-uso-do-ollama-windows-macos-linux
classes: wide
excerpt: Neste guia de instalação, aprenda como configurar utilizar a ferramenta Ollama, para ter seu próprio ChatGPT na máquina local.
---

![alt text](/images/ollama-logo.png)

# Introdução

Hoje em dia, a inteligência artificial está cada vez mais presente na vida dos profissionais de desenvolvimento de software, e a capacidade de executar os Modelos de Linguagem Grandes (no inglês, Large Language Models - LLMs) localmente pode ser um diferencial para quem deseja testar os últimos lançamentos da comunidade científica e empresarial, sem pagar pelo processamento dos tokens e vincular o cartão de crédito. Nesta guia vamos explorar como configurar e utilizar a ferramenta Ollama.

# O que é Ollama?

O Ollama é uma ferramenta e plataforma que simplifica o uso de modelos LLMs localmente. Esta ferramenta é projetada para simplificar configurações complexas que anteriormente eram necessárias para instalar um LLM localmente. O uso da ferramenta Ollama permite que desenvolvedores e entusiastas de Inteligência Artificial (IA) utilizem os LLMs de maneira mais acessível e eficiente, facilitando a integração e experimentação em projetos.

A seguir, algumas vantagens da ferramenta: 
- Executar um LLM localmente, **sem acesso a internet**;
- Total controle sobre os dados, garantindo **privacidade e segurança**;
- Acesso à LLMs que acabaram de ser lançados;
- Integração por meio de **API**.

Em contrapartida, a desvantagem é o hardware. Para executar um LLM com a ferramenta Ollama é necessário possuir um hardware bom, sendo recomendável um hardware com GPU. Caso contrário, quanto pior o hardware mais lenta será a resposta do LLM.

## Requisitos de Hardware e Software

Para o uso eficiente da ferramenta Ollama, é recomendável ter um hardware robusto. O uso de uma GPU dedicada melhora significativamente a performance do modelo utilizado. No entanto, também é possível utilizar apenas CPUs, as CPUs modernas com instruções AVX/AVX2 suportam a maioria dos modelos disponíveis na plataforma Ollama. Atualmente, o Ollama é compatível com os sistemas operacionais Windows, MacOS e Linux.

# Instalação da ferramenta Ollama

Ollama é compatível com os sistemas operacionais Windows, MacOS e Linux. Logo, utilize as instruções de acordo com o seu sistema operacional:

## Windows

1. Baixe  o instalador no [site oficial](https://ollama.com/download/windows);
2. Execute o arquivo .exe e siga as instruções do assistente de instalação;
3. Após a instalação, abra o terminal (cmd ou PowerShell) e verifique se a Ollama está instalado corretamente com o comando `ollama --version`.

## MacOS

1. Baixe o instalador no [site oficial](https://ollama.com/download/mac);
2. Execute o arquivo .dmg e siga as instruções do assistente de instalação;
3. Verifique a instalação abrindo o terminal e digitando `ollama --version`.

## Linux

1. Abra o terminal e execute o comando `curl -fsSL https://ollama.com/install.sh | sh`;
2. Verifique a instalação com o comando `ollama --version`.

# Seleção do Modelo

Após instalar a ferramenta Ollama, você pode baixar e configurar um LLM usando o comando `ollama pull <nome-do-modelo>`. Por exemplo, para baixar o modelo [Llama 2](https://llama.meta.com/llama2/), utilize o comando:

```bash
ollama pull llama2.
```

Além do Llama2, também existem muitos [outros modelos disponíveis para download](https://ollama.com/library?sort=popular).

# Execução do Modelo

Para executar um LLM com a Ollama, utilize o comando `ollama run <nome-do-modelo>`. Por exemplo, com o comando a seguir, exucata o LLM LLama 2 no seu ambiente de desenvolvimento local.

```bash
ollama run llama2
```

Após executar o comando anterior, o modelo ficará disponível para uso em dois formatos: terminal e API.

## Interação via terminal

Após iniciar o modelo, já é possível enviar e receber respostas. Como ilustrado na figura a seguir:

![Executando o modelo LLama 2 localmente com Ollama](/images/ollama-run-llama2.png)

## Interação via API

A ferramenta Ollama também permite que outras aplicações façam uso do LLM, por meio de API. Para mais detalhes, consulte a [documentação da API](https://github.com/ollama/ollama/blob/main/docs/api.md#list-local-models).

![alt text](/images/olla-run-api.png)

## Dicas e Melhores Práticas

Como otimizar a performance do modelo

- **Hardware**: utilize uma GPU dedicada para melhor performance;
- **Drivers**: mantenha os drivers da GPU atualizados;
- **Recursos do sistema**: feche aplicativos desnecessários para liberar recursos.

Resolvendo problemas comuns

- **Instalação**: certifique-se de que seu sistema está atualizado e que você tem permissões adequadas;
- **Carregamento de modelos**: Verifique se o nome do modelo está correto e se há - atualizações disponíveis;
- **Conectividade da API**: Certifique-se de que o Ollama está rodando e que a porta padrão não está em uso por outro aplicativo.

## Conclusão

Nesta guia, exploramos como instalar e configurar a ferramenta Ollama, baixar e executar os LLMs. A modelos de liguagem podem ser utilizados no terminal ou via API. Com esta ferramenta, você está pronto para explorar o mundo da IA na sua máquina local.