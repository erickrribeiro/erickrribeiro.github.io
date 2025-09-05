---
title: "Mutirão: Revisão do Python Fluente Vol. 1"
date: 2025-09-01T00:00-03:00
last_modified_at: 2025-09-01T00:00:00-03:00
categories:
  - python
  - comunidade
  - livros
  - revisão
permalink: /comunidade/python-fluent-review
classes: wide
excerpt: Participe do mutirão para revisar o volume 1 da segunda edição do Python Fluente, de Luciano Ramalho. Ajude na revisão do preprint, reportando erros, links quebrados e problemas de formatação até o prazo de 8 de setembro.
tags:
  - python
  - python fluente
  - livro
  - revisão
  - comunidade
  - github
---

O Luciano Ramalho anunciou em seu blog um **mutirão para revisão do volume 1 da segunda edição do _Python Fluente_**, que será publicado em português, impresso, dividido em **3 volumes** (8 capítulos cada, cerca de 400 páginas por volume).  

Atualmente, ele está trabalhando no **Volume 1 — Dados + Funções**.  

📄 O preprint (`pre2`) já está disponível para leitura e revisão:  
👉 [pythonfluente.com/pyfl-vol1-pre2.pdf](https://pythonfluente.com/pyfl-vol1-pre2.pdf)


## Como ajudar

A revisão consiste em encontrar e reportar problemas como:  

- palavras erradas ou grudadas;  
- linhas quebradas em lugares errados nos códigos Python;  
- links quebrados;  
- problemas de formatação;  
- qualquer coisa que pareça estranha.  


## Prazo

📌 O prazo para enviar contribuições é até **8 de setembro de 2025**.  


## Sorteio do capítulo

Para evitar concentração de revisões apenas no capítulo 1, Ramalho sugere um "sorteio" simples. Basta executar no Python o seguinte código com o seu ano de nascimento:

```python
>>> ano = 1995
>>> ano % 8 + 1
5
```

O resultado indica o capítulo a revisar.  


## Como enviar correções

Existem três formas de colaborar:  

1. **Por e-mail**:  
   - Use o formato `<primeiro_nome_do_LR>@<ultimo_nome_do_LR>.org`  
   - Coloque `[ERRATA]` no assunto  
   - Inclua: versão do preprint (ex: `pre2`), número da página lógica (rodapé) e descrição do problema.  

2. **Abrindo um issue no GitHub**:  
   - [Repositório de issues](https://github.com/pythonfluente/pythonfluente2e/issues)  
   - Clique em **[New issue]** → template *Revisão pre-print*  
   - Use `[ERRATA]` no título + tag `(impresso)`.  

3. **Enviando um PR**:  
   - Diretório: [/vol1](https://github.com/pythonfluente/pythonfluente2e/tree/main/vol1)  
   - Prefixe o título do PR com `[ERRATA]`.  
   - Não é obrigatório abrir issue antes.  


> 💡 Toda ajuda é bem-vinda para que a segunda edição do **Python Fluente** seja publicada com a máxima qualidade!  

📌 Fonte: [ramalho.org — Python Fluente: mutirão para revisar o vol. 1](https://ramalho.org/posts/python-fluente-rev-vol1/)  


### Tags
`Python` · `Livro` · `Comunidade` · `GitHub`
