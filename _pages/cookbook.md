---
title: "Códigos para tarefas repetitivas"
permalink: /cookbook/
date: 2024-06-15T00:00:00-00:00
last_modified_at: 2024-07-29T00:00:00-00:00
excerpt: Trechos de código para tarefas repetitivas
toc: true
toc_sticky: true
---

Esta é uma coleção pessoal de comandos e trechos repetitivos que eu utilizo diariamente.

# Git

- O comando `git branch -m <nome_antigo> <nome_novo>` permite renomear uma branch local;
- O comando `git stash list` exibirá uma lista de todos os stashes que o você possui;
- O comando `git stash show` exibirá os arquivos que mudaram, comparado com o seu stash mais recente. Também é possível adicionar a opçãp `-p` para mostrar o diff, linha a linha.

```sh
git stash show -p
```

Se o stash que você está interessado não for o mais recente, adicione o nome do stash ao final do comando:

```sh
git stash show -p stash@{2}
```