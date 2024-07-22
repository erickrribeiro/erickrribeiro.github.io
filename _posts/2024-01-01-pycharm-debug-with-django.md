---
title: "PyCharm com Django: Erro ao executar no modo de Debugger"
date: 2024-01-01T00:00-00:00
last_modified_at: 2024-01-01T00:00:00-00:00
categories:
  - pycharm
  - python
permalink: /vscode/depurando-aplicativo-streamlit-no-vscode
classes: wide
excerpt: Neste tutorial, mostramos como resolver o problema "Unknown command", que acontece durante a execução do modelo Degubber no PyCharm.
---

Ao trabalhar com projetos Django no PyCharm, pode ser que você receba a seguinte erro ao tentar executar o debugger:
```
D:\prog\python\toolStorage\venv\Scripts\python.exe -X pycache_prefix=C:\Users\Admin\AppData\Local\JetBrains\PyCharm2023.2\cpython-cache C:/PyCharm/plugins/python/helpers/pydev/pydevd.py --multiprocess --qt-support=auto --client 127.0.0.1 --port 28102 --file D:\prog\python\toolStorage\manage.py runserver 8011 
Connected to pydev debugger (build 232.10300.41)
Unknown command: 'C:\\PyCharm\\plugins\\python\\helpers\\pydev\\pydevd.py'
Type 'manage.py help' for usage.

Process finished with exit code 1
```