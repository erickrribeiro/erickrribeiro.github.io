---
title: "As Novidades da OpenAI em Março de 2025"
date: 2025-03-31T00:00-00:00
last_modified_at: 2025-03-31T00:00-00:00
categories:
  - openai
  - llms
  - genai

permalink: /noticias/openai-novas-ferramentas-para-agentes
classes: wide
excerpt: OpenAI apresenta a Responses API, ferramentas de busca e um SDK open source voltado para agentes. As atualizações fortalecem a tendência de agentes baseados em GenAI como principal forma de uso de modelos de linguagem.
---

![Novo conjunto de ferramentas da Openai 2025](/images/openai-updates-march-2025.png)

Em março, a OpenAI apresentou um [novo conjunto de ferramentas](https://openai.com/index/new-tools-for-building-agents/) voltado ao desenvolvimento e à escalabilidade de agentes baseados em inteligência artificial generativa (GenAI). As novidades incluem APIs mais simples, recursos integrados de busca e um SDK para orquestração, tudo pensado para tornar mais fácil a criação de agentes úteis, eficientes e alinhados com tarefas do mundo real.

Se você está explorando esse campo ou pensando em construir soluções com GenAI, essas atualizações podem representar um avanço importante no seu fluxo de desenvolvimento.

## O que é a Responses API?

A principal novidade é a [**Responses API**](https://platform.openai.com/docs/api-reference/responses), uma nova interface que combina o melhor das APIs Chat Completions e Assistants. Ela é mais simples de usar e já vem com ferramentas embutidas que executam chamadas e adicionam os resultados diretamente no contexto da conversa. Isso reduz a complexidade no código e abre espaço para construções mais dinâmicas e poderosas. 

Logo no lançamento, a Responses API já suporta ferramentas nativas como [**Web Search](https://platform.openai.com/docs/guides/tools-web-search?api-mode=responses)** e [**File Search**](https://platform.openai.com/docs/guides/tools-file-search). Essas ferramentas foram projetadas para funcionar de forma coordenada, conectando os modelos ao mundo real. Para começar, você pode conferir o [guia rápido da Responses API](https://platform.openai.com/docs/api-reference/responses).

### Web Search

![Exemplo de código do recurso Web Search da Openai 2025](/images/code-web-search-openai.png)

A [**Web Search**](https://platform.openai.com/docs/guides/tools-web-search?api-mode=responses) permite integrar buscas na web com apenas algumas linhas de código. Ela entrega respostas precisas, com fontes citadas, e entende bem o contexto de conversas e perguntas de acompanhamento.

Essa ferramenta está disponível na Responses API para os modelos `gpt-4o` e `gpt-4o-mini`. Também pode ser usada como modelo separado na Chat Completions API, sob os nomes `gpt-4o-search-preview` e `gpt-4o-mini-search-preview`.

### File Search

![Exemplo de código do recurso File Search da Openai 2025](/images/code-file-search-openai.png)

A [**File Search**](https://platform.openai.com/docs/guides/tools-file-search) é uma ferramenta de busca em arquivos simples e poderosa. Ela suporta múltiplos formatos, reranking, filtros por atributo e reescrita de consultas. É uma ótima opção para quem precisa incorporar busca em documentos nos agentes. Está disponível tanto na Responses API quanto na Assistants API.

### Agents SDK

![Exemplo de código do recurso Agents SDK da Openai 2025](/images/code-agents-sdk-openai.png)

O [**Agents SDK**](https://platform.openai.com/docs/guides/agents) é um framework de orquestração que abstrai a complexidade envolvida na construção e escalabilidade de agentes. Ele oferece ferramentas de observabilidade integradas para visualizar e analisar o desempenho dos agentes em tempo real. Inspirado no Swarm, é open source e compatível com diferentes modelos e ferramentas de rastreamento.

### Por que isso importa?

Desde o final de 2024, uma grande aposta vem ganhando força no ecossistema de inteligência artificial: a construção de agentes baseados em GenAI. Ao longo de 2025, essa abordagem tem se consolidado como a principal forma de aplicação prática de modelos de linguagem — saindo do uso pontual de prompts para sistemas mais robustos, capazes de executar tarefas de ponta a ponta com autonomia.

Construir agentes realmente úteis vai muito além de gerar respostas com IA. É preciso coordenar chamadas a ferramentas externas, interpretar resultados, tomar decisões baseadas em contexto e manter um histórico consistente da interação. As novas ferramentas lançadas pela OpenAI tornam esse processo significativamente mais acessível, oferecendo a base necessária para quem quer desenvolver soluções mais inteligentes, escaláveis e voltadas para o uso real.