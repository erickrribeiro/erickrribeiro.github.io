---
title: "Como incorporar imagens do Google Drive em Markdown"
date: 2025-07-28T00:00-03:00
last_modified_at: 2025-07-28T00:00:00-03:00
categories:
  - markdown
  - produtividade
permalink: /markdown/como-incorporar-imagens-google-drive
classes: wide
excerpt: Aprenda como incorporar imagens hospedadas no Google Drive em seus arquivos Markdown, com opções usando Markdown simples ou HTML personalizado.
---

![Como incorporar imagens do Google Drive em Markdown](https://raw.githubusercontent.com/erickrribeiro/erickrribeiro.github.io/a550abfbebf84a899ba8c29b7ed8cc2b8705b62d/images/google-drive-imgs-to-markdown.png)
# Como incorporando Imagens do Google Drive em Markdown

a. Faça upload da sua imagem no Google Drive.  
b. Altere o modo de compartilhamento de **Restrito** para **Qualquer pessoa com o link**.  
c. Clique em **Copiar link**. O link gerado terá o seguinte formato:  
`https://drive.google.com/file/d/<ID da imagem>/view?usp=sharing`

d. Extraia o `<ID da imagem>` desse link e construa um novo link no seguinte formato para incorporação:  `https://drive.google.com/thumbnail?sz=w1920&id=<image_id>` 

## Para incorporar uma imagem usando Markdown, utilize:

```
![texto alternativo](https://drive.google.com/thumbnail?sz=w1920&id=<image_id>)
```

O uso do Markdown é bastante simples, porém oferece poucas opções de personalização para o ajuste das imagens. Por isso, quando necessário, você pode optar pelo código HTML abaixo, que permite adicionar sombra ou redimensionar a imagem conforme suas necessidades.

## (Opcional) Incorporando com HTML para mais flexibilidade

```
<img src="https://drive.google.com/thumbnail?sz=w1920&id=<image_id>" width="90%" style="box-shadow: 2px 2px 10px #888888;" />
```

- A opção em HTML oferece maior controle sobre o tamanho e o estilo da imagem, como a adição de sombras e a definição da largura.
- A visualização da imagem será ajustada conforme as configurações do código HTML utilizado.

## Passo a passo resumido

1. Gere um link compartilhável para a sua imagem no Google Drive. Por exemplo: 

```
https://drive.google.com/file/d/1rJIMCvX1XsyB0PLOI0swRAV3cYjNFEt0/view?usp=sharing
```

2. Utilize o `<ID da imagem>` do link para exibir a imagem via Markdown.

```
![Example Image](https://drive.google.com/thumbnail?sz=w1920&id=1rJIMCvX1XsyB0PLOI0swRAV3cYjNFEt0)
```

3. (Opcional) Utilize o código HTML para personalizar o tamanho e o estilo da imagem.

```
<img src="https://drive.google.com/thumbnail?sz=w1920&id=1rJIMCvX1XsyB0PLOI0swRAV3cYjNFEt0"
     alt="sample image"
     style="display: block; margin-right: auto; margin-left: auto; width: 90%;
     box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19)" />
```

O resultado final será:
<img src="https://drive.google.com/thumbnail?sz=w1920&id=1rJIMCvX1XsyB0PLOI0swRAV3cYjNFEt0"
     alt="sample image"
     style="display: block; margin-right: auto; margin-left: auto; width: 60%;
     box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19)" />

