---
layout: post
title: "Desenvolvimento híbrido com Cordova e Ionic"
date: 2015-03-14 23:44:22 +0000
subject: ionic
comments: true
read_time: 10 min
---

## A disputa Híbrido vs Nativo ##

Vamos começar falando um pouco sobre significa um aplicativo mobile ser híbrido ou nativo. Um aplicativo nativo é aquele desenvolvido com as linguagens padrão da SDK de um dispositivo. No caso do Android a linguagem temos o Java e no caso do iOS o Objective-C . Já um aplicativo híbrido é aquele que é desenvolvidocom HTML/CSS/JS mas que mesmo assim pode ser empacotado e distribuído nas app stores da mesma maneira que é feito com um aplicativo nativo.

Aplicativos híbridos são aqueles que não são desenvolvidos em código nativo. Um aplicativo nativo para android por exemplo deve ser desenvolvido em Java. Um aplicativo nativo para iOS deve ser desenvolvido em Objective-C ou Swift. Um aplicativo híbrido porém funciona de uma forma diferente. Um aplicativo híbrido é desenvolvido utilizando as conhecidas tecnologias web: HTML, CSS e Javascript.

Embora utilize as mesmas tecnologias da web, um aplicativo híbrido não é acessado pelo navegador dos dispositivos. Um aplicativo híbrido é acessado da mesma maneira que um aplicativo nativo, através do download pelas app stores da Apple, Google, Windows, etc... Isso é possível pois um aplicativo híbrido roda dentro de uma webview que é então empacotada dentro de um projeto com código nativo. E é esse projeto nativo que por sua vez sofre o build para as plataformas de destino, seja android, ios ou qualquer outra. Esse projeto nativo é o mesmo criado quando o desenvolvedor cria um projeto Android ou iOS.

Ou seja, você desenvolve tudo dentro de um projeto web, que por sua vez passa por um processo onde ele é colocado dentro de um projeto nativo, que por sua vez sofre o build para finalmente surigirem os aplicativos que serão instalados nos dispositivos.

## Mas devo usar Cordova ou Phonegap? ##

O cordova entra para transformar esse projeto web em um projeto nativo. O cordova coloca o seu projeto web dentro de um projeto nativo, que por sua vez sofre o build e é instalado nos dispositivos como um aplicativo nativo. Além de permitir que aplicativos sejam escritos em HTML, CSS e Javascript. Ou seja, o cordova é quem empacota uma aplicação web dentro de um aplícativo híbrido.

Além de fazer esse empacotamento, o cordova também permite ao desenvolvedor acessar os recursos do aparelho como a camera, microfone, a operadora do celular, os contatos, etc... Isso seria impossivel de fazer utilizando somente o navegador. O cordova permite que o desenvolvedor acesse tudo isso através de plugins para cada uma dessas funcionalidades.

Porém, assim que voce instalar o cordova, ele não vai vir com nenhum desses recursos. Mas no momento em que voce precisar usar a camera do aparelho por exemplo, voce pode adicionar esse plugin de maneira independente. Essa arquitetura de plugins foi introduzida apartir da versão 3.x do cordova, e o maior beneficio dela é evitar que o build do seu aplicativo fique muito pesado com plugins que você não vai utilizar

Uma duvida comum que surge ao entrar nesse mundo é por qual plataforma devo começar: pelo cordova ou pelo phonegap? Na verdade os dois acabam dando na mesma coisa. Tudo quando uma empresa chamada Nitobi criou o Phonegap em 2009. O objetivo deles era, com o de hoje, permitir que uma webview embedada dentro de um aplicativo nativo pudesse acessar o ambiente ao seu redor. Dessa forma eles foram os primeiros a viablizar que aplicações em html/css/js rodando dentro de uma webview conseguissem acessar os recursos do dispositivo como camera, microfone, entre outros. Em 2011 a Adobe comprou a Nitobi e doou para a Apache o core desse projeto, que recebeu o nome de Cordova. Resumidamente o phonegap é o cordova com os serviços extras que a Adobe oferece. Um desses primeiros serviços criados foi o Phonegap Build.

O fato é, independente de qual plataforma você for escolher, voce certamente terá bastante trabalho com o design e a ux do seu aplicativo. Em um aplicativo mobile é comum termos componentes como menus que podem ser arrastados, formulários e barras de navegação em geral. Ao desenvolver um aplicativo híbrido, você a principio teria que se preocupar com todos esses componentes, não apenas para desenvolve-los mas também para se assegurar de que todos eles funcionarão de modo homogêneo e performático nos diversos dispositivos, plataformas, fabricantes, etc... Parece muito trabalho, e é mesmo. Eis que surge o Ionic.

## Ionic, uma luz no fim do túnel ##

bla bla bla...

## A lib do Ionic ##

bla bla bla...

## A CLI (command line interface) do Ionic ##

bla bla bla...

## Os serviços de plataforma e o futuro do Ionic ##

bla bla bla...
