---
title: "Depurando Aplicativo feito com Streamlit no VSCode"
date: 2023-12-01T00:00-00:00
last_modified_at: 2024-10-21T00:00:00-00:00
categories:
  - vscode
  - python
  - streamlit
permalink: /vscode/depurando-aplicativo-streamlit-no-vscode
classes: wide
excerpt: Neste tutorial, mostramos como usar o VSCode para depurar um aplicativo feito com o Streamlit. Abordamos desde a configuração básica até a definição de pontos de interrupção, tornando a depuração mais intuitiva e integrada ao seu ambiente de desenvolvimento.
---

Neste tutorial, vou mostrar como usar o VSCode para [depurar](https://www.hostgator.com.br/blog/debug-desenvolvimento-web) (ou debugar) um aplicativo feito com [Streamlit](https://docs.streamlit.io/). 

## Aplicativo

Primeiro, vamos utilizar o Streamlit para escrever um aplicativo simples, que soma dois números:

{% gist 8de5c309caafa9e1ee9664bcc69df03a app.py%}

Agora que temos um aplicativo feito com Streamlit, bora configurar o VSCode.

## Configurando a Depuração

![Configurando a depuraçao no VSCode](/images/create_launch.png)

No VSCode, vá até a aba **Run and Debug** no painel lateral esquerdo. Em seguida, clique em **create a launch.json file**. Quando solicitado, escolha a opção **Python** e depois  **Python file**. O VSCode deve gerar automaticamente um arquivo no caminho **.vscode/launch.json**.

Abra o arquvio **.vscode/launch.json**, apague o conteúdo existe e adicione o texto a seguir:

{% gist 8de5c309caafa9e1ee9664bcc69df03a launch.json%}

Pronto! Agora é possível realizar a depuração de um código Python que usa a biblioteca Streamlit.

## Depurando o código 


![Executando a depuração](/images/debugger-running.gif)

Depois de configurar o arquivo **.vscode/launch.json** e preparar o seu ambiente no VSCode, é hora de começar a depurar o código do aplicativo feito com Streamlit. Para isso, siga as instruções:


1. **Adicionar Pontos de Interrupção (Breakpoints)**
   - Abra o arquivo **app.py** no VSCode.
   - Clique na margem esquerda ao lado do número da linha onde você deseja adicionar um ponto de interrupção. Um ponto vermelho aparecerá indicando o ponto de interrupção. Por exemplo, você pode adicionar um ponto de interrupção na linha onde o resultado da soma é calculado:

   {% gist 8de5c309caafa9e1ee9664bcc69df03a breakpoints.py%}

2. **Iniciar a Depuração**
   - Clique no ícone de **Run and Debug** (Executar e Depurar) na barra lateral esquerda.
   - Selecione a configuração **Python: Streamlit** e clique no botão de **play** para iniciar a depuração. Isso iniciará o servidor do Streamlit e abrirá um terminal integrado no VSCode.
   - O aplicativo feito com Streamlit será executado e estará acessível no navegador, no endereço [localhost:2000](http://localhost:2000).

3. **Interagir com o Aplicativo**
   - Navegue para o endereço onde o aplicativo com Streamlit está sendo executado.
   - Insira valores nos campos **Informe um número** e **Informe outro número**.
   - Clique no botão **Somar**.

4. **Execução e Interrupção:**
   - Quando a execução do código atingir o ponto de interrupção que você configurou, o VSCode interromperá a execução. O editor mudará para o modo de depuração.
   - No painel de depuração, você poderá ver o valor das variáveis locais, a pilha de chamadas e outras informações úteis.

5. **Explorar Variáveis:**
   - No painel **Variables** (Variáveis), você pode inspecionar os valores atuais de **num1**, **num2** e **result**.
   - Você pode também adicionar expressões no painel **Watch** (Assistir) para monitorar variáveis específicas ou expressões durante a execução do código.

6. **Controlar a Execução:**
   - Use os botões de controle de execução na parte superior da tela para continuar a execução (**Continue**), avançar para a próxima linha (**Step Over**), entrar em uma função (**Step Into**) ou sair de uma função (**Step Out**).

Com esses passos, você estará apto a depurar seu aplicativo feito com Streamlit utilizando o VSCode, permitindo identificar e corrigir erros de forma eficiente. 

## Conclusão

Isso é tudo! Após ler este tutorial, espero que a depuração dos seus códigos fique mais intuitiva e integrada diretamente com o VSCode, melhorando a produtividade e a qualidade do código. Lembre-se de que apenas arranhamos a superfície dos recursos de depuração do VSCode. Portanto, experimente e explore mais para aproveitar ao máximo essa poderosa ferramenta!