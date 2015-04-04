---
layout: post
title: "Apps Híbridas com Cordova e Ionic"
date: 2015-03-14 23:44:22 +0000
subject: apps híbridas
comments: true
read_time: 10 min
---

Uma mobile app **nativa** é aquela desenvolvida com as linguagens padrão da SDK do dispositivo. No caso do Android o Java e no caso do iOS o Objective-C, e mais recentemente o Swift. Já uma app **híbrida** é aquela que é toda desenvolvida com html, css e javascript e que mesmo assim pode ser empacotada e distribuída nas app stores como uma app nativa.

 Nesse artigo vamos entender mais a fundo o que é uma app híbrida e onde o cordova e o ionic se encaixam na desenvolvimento delas.

## Desenvolvimento híbrido mais de perto ##

O desenvolvimento híbrido consiste em utilizar html, css e javascript para a construção de uma mobile app que depois será instalada e executada do mesmo modo de uma app nativa. Isso só é possível pois, assim que a app é aberta pelo usuário, todo esse código roda dentro de algo chamado **webview**.

Webview é o nome dado a um tipo especial de browser que começa a rodar assim que a app híbrida é aberta pelo usuário. É dentro desse browser que a app é executada. É claro que o usuário não sabe que está dentro de um browser pois essa webview não contém componentes característicos de um, como a barra de endereço e barra de favoritos, por exemplo. A webview contém apenas o necessário para que o html, css e javascript funcionem. Ela se comporta como a engine de renderização da app.

Por isso o nome híbrido: uma parte da app é feita em código nativo para ser empacotada e distribuída nas app stores, e a outra parte é feita de código não nativo (html, css e javascript) que implementa todo o visual e o comportamento da app.

Talvez a grande sacada de uma webview é que ela não se limita à renderização da app. Ela também consegue acessar recursos nativos do dispositivo como a **camera, microfone, acelerômetro**, etc... Isso é possível graças a uma interface javascript que torna a webview apta a executar código nativo nos dispositivos.

 Ou seja, no desenvolvimento híbrido é possível usar apenas **javascript** para acessar os **recursos nativos** do dispostivo, coisa que nenhum browser comum instalado no aparelho seria capaz de acessar.

## Cordova e Phonegap ##

Atualmente o desenvolvimento híbrido possui 2 plataformas principais, o **cordova** e o **phonegap**. Os dois servem ao mesmo propósito, que é de um modo transparente para o desenvolvedor, criar uma app nativa capaz de abrir uma webview para a execução do html, css e javascript criados pelo desenvolvedor. Paralelo a isso, eles também tem o conceito de **plugins** que são usados para acessar os recursos do dispositivo.

É chamado de **build** o processo de colocar o código não nativo dentro de uma app nativa. O input do build são os arquivos html, css e javascript além de alguns arquivos de configuração do seu projeto, e o output é uma app nativa que, ao ser executada, abre a webview que vai renderizar a app.

Mas se tanto o cordova quanto o phonegap servem para a mesma coisa, qual a diferença? Tudo começou quando uma empresa chamada Nitobi criou o **phonegap** em 2009. Em 2011 a Adobe comprou a Nitobi e pouco tempo depois doou para a Apache o core desse projeto. Entre outros motivos a Adobe queria se certificar que outras empresas pudessem contribuir com o projeto. A Apache então foi uma escolha natural para a Adobe pois muitas grandes empresas já confiavam na Apache e estavam confortável com as suas licenças. Por fim, para evitar problemas com o nome phonegap que é uma marca registrada da Adobe, debaixo da Apache o projeto recebeu o nome de **cordova**.

Dessa forma, o phonegap pode ser considerado uma distribuição do cordova. Tanto um quanto o outro são projetos opensource, mas ao redor do phonegap a Adobe já lançou e deve continuar lançando alguns serviços, como o Phonegap Build. Uma boa maneira de entender isso é enxergar o phonegap como sendo o cordova cercado por alguns serviços extras (e possivelmente pagos) da Adobe.

Como não utilizo os serviços da Adobe, eu escolho o cordova para desenvolvimento híbrido. Como veremos mais a frente, por motivos semelhantes as bibliotecas open source como ionic que de alguma maneira constroem algo para apps híbridas também costumam se basear no cordova.

Independente da plataforma escolhida, grande parte do trabalho de construir de uma app híbrida se concentra na construção da interface. Em uma mobile app é necessário não só construir componentes como menus, tabs e formulários responsivos, mas também é necessário garantir a performance e o bom comportamento desses componentes diversos em sistemas, dispositivos e tamanhos de tela diferentes.

A complexidade na construção desses componentes se tornou um sério problema. Tempo e dinheiro que deveriam estar centralizados nas funcionalidades do modelo de negócios estavam indo para na construção dos componentes mais básicos da app.

## Ionic ##

Para resolver esse problema, surgiu no final de 2013 um projeto chamado **ionic**. O ionic é uma SDK de componentes visuais focados em mobile apps híbridas. Seus diversos componentes html e css e funcionalidades javascript são bastante simples de usar e livram o desenvolvedor de ter que codificar tudo apartir do zero.

O ionic precisa do cordova instalado para conseguir rodar nos dispositivos. Como o ionic é uma SDK javascript, sem o cordova o ionic também funciona, mas o resultado só pode ser visto através de um browser de um desktop ou do próprio dispositivo. O cordova é necessário para que a app consiga ser instalada e executada nos dispositivos.

O que diferencia o ionic de seus rivais mais populares como o [jQuery Mobile](https://jquerymobile.com/) e o [Sencha Touch](https://www.sencha.com/products/touch/) é que o ionic é totalmente voltado para **performance**, o que torna a fluidez e a responsividade da app híbrida algo mais próximo possível de uma app nativa.

Um grande apelo do ionic é fato dele ser baseado no **angular**, que é um framework javascript aplamente adotado pela comunidade e que traz um enorme ganho de produtividade para os desenvolvedores. Ser baseado em angular também signfica que quem já trabalha com ele vai conseguir reutilizar no ionic todo o conhecimento previamente adquirido.

O ionic também conta com uma excelente [documentação](http://www.ionicframework.com/docs) e com um [fórum próprio](http://www.ionicframework.com/docs) bastante ativo onde perguntas são respondidas em até poucos dias. Recentemente o ionic começou a oferecer também alguns serviços que no momento em que escrevo esse post ainda estão em beta, como o [Ionic Creator](http://creator.ionic.io/), [Ionic View](http://view.ionic.io/) e as [Push Notifications](https://apps.ionic.io/landing/push).

Um último recurso do ionic que faltou falar é o **[ngCordova](http://www.ngcordova.com)**. O objetivo do ngCordova é empacotar os plugins do cordova para dentro de serviços angular, facilitando assim a utilização desses plugins dentro de um projeto ionic. É importante entender que o ngCordova não é obrigatório para o uso de plugins, ele é apenas um facilitador para integrar melhor com o angular os plugins do cordova.

Caso queira ver uma app híbrida feita com ionic e cordova no mundo real, recentemente trabalhei em um projeto para a Vivo onde ela queria criar o aplicativo para o evento Vivo Open Air que aconteceu em Belo Horizonte. O projeto foi todo construído com ionic e está disponível na [App Store](https://itunes.apple.com/us/app/vivo-open-air/id940039537?mt=8) e no [Google Play](https://play.google.com/store/apps/details?id=com.vivoopenair) para download.

Baseado nesse projeto da Vivo, compilei as técnicas que aprendi em um projeto starter que você pode usar para começar suas apps em ionic. Entre elas temos testes e2e com **protractor** e um build system com **gulp**. Esse projeto se chama ionic-starter-app e [está disponível no meu github](https://github.com/vasconcelloslf/ionic-starter-app).
