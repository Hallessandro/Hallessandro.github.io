---
layout: post
title: "JavaScript - var vs let"
author: "Hallessandro D´villa"
categories: journal
tags: [documentation,sample]
#image: javascript.jpeg
---

Olá terráqueos, nesse post vamos entender melhor quando usar var ou let na declaração das suas variáveis JavaScript. Logo de cara vamos começar com um exemplo, que vai fazer você entender por qual motivo não se deve declarar todas as variáveis com var.

Execute o código abaixo e veja o resultado.
```javascript
for(int i=0; i<=10; i++){
    console.log(i);
}
console.log(i);
``` 
Se você assim como eu já programou em Java, deve saber que um código como o apresentado acima não funcionaria por lá, afinal o **console.log(i+1)** está fora do escopo do bloco for. Porém para nossa surpresa o código acima funciona em JavaScript, imprimindo os valores até 11. :confused:

Isos acontece devido ao fato de que no mundo JavaScript não existe escopo de bloco para variáveis, ou seja, declarar uma variável dentro de um bloco não vai de forma alguma restringir seu escopo apenas ao bloco, pelo contrário.
## Getting Startedsad
lalllasdldadsadsdasd
## Example Content

## Questions?

This theme is completely free and open source software. You may use it however you want, as it is distributed under the [MIT License](http://choosealicense.com/licenses/mit/). If you are having any problems, any questions or suggestions, feel free to [tweet at me](https://twitter.com/intent/tweet?text=My%question%about%Lagrange%is:%&amp;via=paululele), or [file a GitHub issue](https://github.com/lenpaul/lagrange/issues/new).

## More Jekyll!

### Millennial

Millennial is a minimalist Jekyll blog theme that I built from scratch. The purpose of this theme is to provide a simple, clean, content-focused publishing platform for a publication or blog.

Feel free to check out <a href="https://lenpaul.github.io/Millennial/" target="_blank">the demo</a>, where you’ll also find instructions on <a href="https://lenpaul.github.io/Millennial/documentation/getting-started.html">how to use install</a> and use the theme.
