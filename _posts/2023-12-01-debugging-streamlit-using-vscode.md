---
title: "Depurando Aplicativo Streamlit no VSCode"
date: 2023-12-01T00:00-00:00
last_modified_at: 2023-12-15T00:00:00-00:00
categories:
  - vscode
permalink: /vscode/depurando-aplicativo-streamlit-no-vscode
classes: wide
excerpt: Neste tutorial, mostramos como usar o VSCode para depurar um aplicativo Streamlit. Abordamos desde a configuração básica até a definição de pontos de interrupção, tornando a depuração mais intuitiva e integrada ao seu ambiente de desenvolvimento.
---

Neste tutorial, vou mostrar como usar o VSCode para [depuração](https://www.hostgator.com.br/blog/debug-desenvolvimento-web) de um aplicativo feito com [Streamlit](https://docs.streamlit.io/). 

## Aplicativo 
Primeiro, vamos utilizar o Streamlit para escrever um aplicativo simples, que soma dois números:

```python
# app.py
import streamlit as st

st.title("Streamlit com VSCode")

num1 = st.number_input("Informe um número")
num2 = st.number_input("Informe outro número")

if st.button("Somar"):
    result = num1 + num2
    st.write(f"O resultado é {result}")
```

## Configurando a Depuração

![Configurando a depuraçao no VSCode](/images/create_launch.png)

No VSCode, vá até a aba "Run and Debug" no painel lateral esquerdo. Em seguida, clique em "create a launch.json file". Quando solicitado, escolha o opção "Python" e depois  "Python file". O VSCode deve gerar automáticamente um arquivo no caminho `.vscode/launch.json`.

Abra o arquvio `.vscode/launch.json`, apague o conteúdo existe e adicione o texto a seguir:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python:Streamlit",
            "type": "debugpy",
            "request": "launch",
            "module": "streamlit",
            "args": [
                "run",
                "${file}",
                "--server.port",
                "2000"
            ]
        }
    ]
}
```

Pronto! Agora é possível realizar o depupração de um código python que usa a biblioteca Streamlit

## Depurando o código 


![Executando a depuração](/images/debugger-running.gif)

Depois de configurar o arquivo `.vscode/launch.json` e preparar o seu ambiente no VSCode, é hora de começar a depurar o código do aplicativo Streamlit. Vamos seguir os seguintes passos:


1. **Adicionar Pontos de Interrupção (Breakpoints)**
   - Abra o arquivo `app.py` no VSCode.
   - Clique na margem esquerda ao lado do número da linha onde você deseja adicionar um ponto de interrupção. Um ponto vermelho aparecerá indicando o ponto de interrupção. Por exemplo, você pode adicionar um ponto de interrupção na linha onde o resultado da soma é calculado:

   ```python
   result = num1 + num2
   ```

2. **Iniciar a Depuração**
   - Clique no ícone de "Run and Debug" (Executar e Depurar) na barra lateral esquerda.
   - Selecione a configuração "Python: Streamlit" e clique no botão de "play" para iniciar a depuração. Isso iniciará o servidor do Streamlit e abrirá um terminal integrado no VSCode.
   - O aplicativo Streamlit será executado e estará acessível no navegador no endereço padrão (geralmente `http://localhost:8501`).

3. **Interagir com o Aplicativo**
   - Navegue para o endereço onde o aplicativo Streamlit está sendo executado.
   - Insira valores nos campos "Informe um número" e "Informe outro número".
   - Clique no botão "Somar".

4. **Execução e Interrupção:**
   - Quando a execução do código atingir o ponto de interrupção que você configurou, o VSCode interromperá a execução. O editor mudará para o modo de depuração.
   - No painel de depuração, você poderá ver o valor das variáveis locais, a pilha de chamadas e outras informações úteis.

5. **Explorar Variáveis:**
   - No painel "Variables" (Variáveis), você pode inspecionar os valores atuais de `num1`, `num2` e `result`.
   - Você pode também adicionar expressões no painel "Watch" (Assistir) para monitorar variáveis específicas ou expressões durante a execução do código.

6. **Controlar a Execução:**
   - Use os botões de controle de execução na parte superior da tela para continuar a execução (`Continue`), avançar para a próxima linha (`Step Over`), entrar em uma função (`Step Into`) ou sair de uma função (`Step Out`).

Com esses passos, você estará apto a depurar seu aplicativo Streamlit utilizando o VSCode, permitindo identificar e corrigir erros de forma eficiente. 

## Conclusão

Isso é tudo! Após ler este tutorial, espero que a depuração dos seus códigos fique mais intuitiva e integrada diretamente com o VSCode, melhorando a produtividade e a qualidade do código. Lembre-se de que apenas arranhamos a superfície dos recursos de depuração do VSCode. Portanto, experimente e explore mais para aproveitar ao máximo essa poderosa ferramenta!