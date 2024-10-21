---
title: "PyCharm com Django: Erro ao executar o PyCharm no modo de debugger"
date: 2024-01-01T00:00-00:00
last_modified_at: 2024-10-21T00:00:00-00:00
categories:
  - pycharm
  - python
permalink: /vscode/pycharm-com-django-erro-no-debugger
classes: wide
excerpt: Neste tutorial, mostramos como resolver o problema "Unknown command", que acontece durante a execução de um script ou projeto no modo debugger do PyCharm.
---

Ao trabalhar com projetos Django no PyCharm, pode ser que você receba a seguinte mensagem de erro ao tentar executar o debugger:

```
D:\prog\python\toolStorage\venv\Scripts\python.exe -X pycache_prefix=C:\Users\Admin\AppData\Local\JetBrains\PyCharm2023.2\cpython-cache C:/PyCharm/plugins/python/helpers/pydev/pydevd.py --multiprocess --qt-support=auto --client 127.0.0.1 --port 28102 --file D:\prog\python\toolStorage\manage.py runserver 8011 
Connected to pydev debugger (build 232.10300.41)
Unknown command: 'C:\\PyCharm\\plugins\\python\\helpers\\pydev\\pydevd.py'
Type 'manage.py help' for usage.

Process finished with exit code 1
```

Esse cenário de erro é curioso, embora a execução normal do projeto ou script funcione sem problemas, o debugger não inicia. Infelizmente, esse problema pode ocorrer devido a vários motivos, incluindo configurações incorretas ou incompatibilidades entre as versões do PyCharm com as bibliotecas do Python. Por não ser um problema com soluçáo única, a seguir é listado algumas ações que eu já executei e resolveu esse problema:

**1. Atualizar o PyCharm para a versão mais recente**

Se a tua versão do PyCharm é antiga, começar atualizando o PyCharm para a versão 2024 é a alternativa mais simples, e resolve muitos problemas. Portanto, a solução mais recomendada é baixar e instalar a versão mais recente do [PyCharm](https://www.jetbrains.com/pycharm/download/).

**2. Verificar a existência do arquivo `pydevd.py`**

Se mesmo com a versão mais recente, o problema continua. Certifique-se de que o arquivo `pydevd.py` realmente existe no caminho especificado na mensagem de erro. Caso contrário, reinstale o PyCharm ou tente reconfigurar o ambiente virtual do projeto, sendo ele um ambiente pip ou conda.

# Conclusão

Estas duas etapas devem ajudar a solucionar o erro de uso do debugger. Porém se o problema persistir, envie um relatório de bug para a empresa JetBrains, dona do PyCharm. Para enviar os logs geradas, vá até a opção **Help > Collect Logs and Diagnostic Data**, na aba superior do PyCharm. Esta ação, ajudará a equipe de suporte da JetBrains a entender e solucionar o problema. Lembre-se que o PyCharm é uma ferramenta paga. Então, entre em contato a equipe de suporte sempre que necessário.
