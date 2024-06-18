---
title: "Para que serve o Robots.txt"
date: 2023-01-15T00:00-00:00
last_modified_at: 2023-01-15T00:00:00-00:00
categories:
  - seo
permalink: /seo/para-que-serve-o-robots-txt
classes: wide
excerpt: O arquivo robots.txt serve para informar aos mecanismos de pesquisa (Google, Bing, Yahoo! e outros) quais URLs podem ser acessadas no site.
---

Ter o próprio site aparecendo nos resultados de buscas é gratificante. Para conquistar este objetivo é importante aprender sobre estratégias de SEO, Marketing de Conteúdo e uma série de outras ações capazes de atrair a atenção das ferramentas de busca e, com isso, aumentar o tráfego do seu site. Porém, antes de partir para técnicas avançadas é prudente começar pelo simples. Comece configurando o arquivo `robots.txt`.

## O que é o arquivo robots.txt?

O arquivo `robots.txt` é um arquivo usado em sites para informar aos motores de busca (Google, Bind e outros) quais páginas ou seções do site devem ser indexadas ou não. Ele é colocado na raiz do site e os motores de busca o consultam automaticamente antes de indexar as páginas. Isso permite que os donos dos sites proíbam a indexação de páginas sensíveis, como páginas de administração, ou evitem que páginas desnecessárias sejam incluídas nos resultados de busca. 

## Como usar o robots.txt no Jekyll

Para adicionar o arquivo robots.txt no Jekyll é bastante simples. Siga os seguintes passos:

1. Crie um novo arquivo chamado `robots.txt` na raíz do seu projeto Jekyll.
2. Adicione as instruções desejadas ao arquivo. Por exemplo:

```
User-agent: *
Sitemap: https://erickrribeiro.github.io/sitemap.xml
```

3. Faça o build do seu site Jekyll com o comando `jekyll build` ou `jekyll serve`
4. Faça o deploy do seu site, incluindo o arquivo `robots.txt` gerado, para o seu servidor.
5. Teste se o seu arquivo robots.txt está funcionando corretamente visitando `http://seusite.com/robots.txt`. 

Caso tenha curiosidade, neste site [https://erickrribeiro.github.io](https://erickrribeiro.github.io), o arquivo robots.txt aparece como [https://erickrribeiro.github.io/robots.txt](https://erickrribeiro.github.io/robots.txt).

<div class="notice--warning">
<strong>Mais detalhes:</strong>
<p>
Para mais informações sobre o uso e configurações avançados do arquivo `robots.txt`, leia o material (Introdução ao robots.txt)[https://developers.google.com/search/docs/crawling-indexing/robots/intro]
</p>
</div>

## References
- Central da Pesquia Google, ["Introdução ao robots.txt - Documentação"](https://developers.google.com/search/docs/crawling-indexing/robots/intro)
