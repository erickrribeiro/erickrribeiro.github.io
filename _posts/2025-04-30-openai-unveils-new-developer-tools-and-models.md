---
title: "As Novidades da OpenAI em Abril de 2025"
date: 2025-04-30T00:00-00:00
last_modified_at: 2025-04-30T00:00-00:00
categories:
  - openai
  - llms
  - genai

permalink: /noticias/openai-lanca-gpt-4-1-modelo-o3-e-novos-modelos-de-audio
classes: wide
excerpt: OpenAI apresenta novos modelos de linguagem e áudio, incluindo o GPT-4.1, o modelo o3 e ferramentas para desenvolvedores. As novidades abrem caminhos para agentes mais autônomos e experiências multimodais mais naturais.
---

Ao longo do mês de abril, a OpenAI anunciou uma série de avanços importantes em seus modelos e ferramentas, com foco em desempenho, eficiência e suporte a agentes autônomos. A atualização apresenta novos modelos de linguagem, ferramentas para desenvolvedores e melhorias significativas na área de áudio. Confira as novidades.

### **1. Novos Modelos de Raciocínio: o3 e o4-mini**

![image.png](attachment:ec173cf2-28e8-4061-95e4-7c02d63eced7:image.png)

A OpenAI lançou os modelos [**o3** e **o4-mini**](https://platform.openai.com/docs/models/compare?model=o3), voltados para tarefas complexas como programação, matemática e visão computacional.

- **o3** é o modelo com o melhor desempenho em tarefas de codificação, liderando o benchmark SWE-Bench Verified com 69,1%.
- **o4-mini** oferece raciocínio avançado com mais velocidade e menor custo.

Ambos estão disponíveis na API via Chat Completions e Responses. Para quem busca mais controle e explicações detalhadas da IA, a **Responses API** é recomendada, com suporte a "[reasoning summaries](https://platform.openai.com/docs/guides/reasoning?api-mode=responses#reasoning-summaries)", onde você pode ver o raciocínio da IA em tempo real.

### **2. GPT-4.1: Mais Contexto, Melhor Raciocínio**

![image.png](attachment:e50a22be-6a94-425d-9341-872ccb84330d:image.png)

Três versões do GPT-4.1 foram lançadas:

- [**GPT-4.1**](https://platform.openai.com/docs/models/gpt-4.1)
- [**GPT-4.1 mini**](https://platform.openai.com/docs/models/gpt-4.1-mini)
- [**GPT-4.1 nano**](https://platform.openai.com/docs/models/gpt-4.1-nano)

Estes três novos modelos foram otimizados para tarefas como codificação, interpretação de instruções e chamadas de função. Destaque para a capacidade de lidar com até **1 milhão de tokens de contexto**, o que significa que conseguem manter coerência mesmo em interações longas ou complexas.

### **3. Codex CLI: IA Local Para Codificação**

![image.png](attachment:d0f1a3ec-df4a-42fd-8136-4873e2a9c382:image.png)

A OpenAI apresentou o [**Codex CLI**](https://github.com/openai/codex), uma ferramenta open source que transforma linguagem natural em código executável localmente. Com ela, basta dizer o que você quer fazer, corrigir ou entender, e a ferramenta traduz isso diretamente em código funcional.

Compatível com os modelos mais recentes da OpenAI, o Codex CLI é a ferramenta voltada para desenvolvedores que buscam maior controle e privacidade na programação assistida por Agentes de IA. [Assista à demonstração](https://www.youtube.com/watch?v=FUq9qRwrDrI) no Youtube.

---

### **4. Evals API: Avaliação Automatizada de Prompts**

Com a [**Evals API**](https://platform.openai.com/docs/guides/evals), agora é possível criar e rodar testes automatizados para avaliar a performance de modelos em tarefas específicas. Isso facilita a iteração rápida de prompts e ajustes em aplicações que usam IA.

---

### **5. Modelos de Áudio: Fala e Transcrição com Qualidade Superior**

![image.png](attachment:10a89fe7-8efa-4a63-838b-1969ffa2c9b7:image.png)

[Três novos modelos de áudio](https://platform.openai.com/docs/guides/audio) foram adicionados à API:

- Dois modelos de **transcrição de fala** que superam o Whisper em precisão: `gpt-4o-transcribe`, `gpt-4o-mini-transcribe`
- Um novo modelo de **síntese de voz (TTS)** com controle sobre o estilo da fala: `gpt-4o-mini-tts`

Esses avanços também foram integrados ao [**Agents SDK**](https://platform.openai.com/docs/guides/voice-agents), permitindo a criação de agentes de voz mais naturais e responsivos.

Essas novidades mostram como a OpenAI está avançando em várias frentes: modelos mais potentes e acessíveis, ferramentas que tornam o desenvolvimento com IA mais produtivo, e melhorias na forma como interagimos com os computadores, seja por texto, voz ou código. A direção é clara: modelos cada vez mais autônomos, integrados e capazes de operar em contextos complexos, com menos esforço humano na mediação. Para quem está construindo hoje, essas ferramentas são mais que melhorias técnicas — são blocos fundamentais para as experiências de IA que vão definir os próximos anos.
