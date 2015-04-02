---
layout: post
title: Vim e a Home Row
date: 2014-07-06 23:41:12 -0200
comments: true
tags: ruby
subject: vim
read_time: 3 min
---

A home row é a posição padrão em que as mãos ficam no teclado: mão esquerda nas teclas "asdf" e a mão direita nas teclas "jkl;". Apartir da home row é possível alcançar sem nenhuma dificuldade a maioria das teclas, porém, algumas como o esc, backspace e o up/down/left/right quebram o workflow de quem quer trabalhar no teclado de modo otimizado. Nesse artigo vou mostrar as soluções que encontrei no vim para não precisar mais deixar a home row.

## A home row ##

![Home Row ](/assets/images/home-row.jpeg)

Eu uso vim pois gosto de utilizar o mínimo de esforço para manipular toda linha de código e de texto que eu digito. Através dele eu consigo fazer todas as manipulações necessárias sem perder tempo alternando entre teclado e mouse.

Embora o vim tenha me permitido largar o mouse de vez, algo ainda me fazia perder tempo por quebrar meu workflow. Eu frequentemente precisava sair da home row para alcançar algumas teclas, entre elas:

* **ESC** para altenar entre os modos do vim
* **DELETE** para remover um caracter depois do cursor
* **BACKSPACE** para remover um caracter antes do cursor
* **UP/DOWN/LEFT/RIGHT** para navegar entre os intes de uma lista

Vou mostrar as soluções que encontrei para substituir essas teclas por teclas que eu consigo chegar sem sair da home row.

## ESC ##

Essa deve ser a solução mais fácil. Tudo que eu tive que fazer foi adicionar essa linha no .vimrc:

```ruby
map <C-c> <Esc>
```

Essa linha mapeia o **ESC** para o **CTRL + C**. Ela me torna capaz de sair de qualquer modo do vim (visual, insert, ex, etc...) sem ter que tirar as mãos da home row para chegar até a tecla esc.


## DELETE e BACKSPACE ##

Para remover palavras e caracteres no normal mode, não preciso usar o delete nem o backspace, mas no insert mode ou no ex mode eu era obrigado a ter que  tirar as mãos da home row para alcançar essas teclas.

A solução que encontrei envolve as chamadas **readline key bindings**. As readline key bindings são comandos que por padrão funcionam em diversos softwares diferentes, entre eles as shells do linux, as linhas de comando (REPL) do ruby, python e node, e até mesmo em programas GUI como o Google Chrome, Spotlight, Alfred, etc...

O vim tem suporte parcial para a maioria delas, mas para ter um suporte mais amplo eu estou utilizando [o plugin vim-rsi do tim pope](https://github.com/tpope/vim-rsi). Esses são os comandos que me fizeram aposentar o delete e o backspace:

```ruby
<C-h> # remove um caracter anterior ao ponteiro
<C-d> # remove um caracter posterior ao ponteiro
<C-w> # remove uma palavra posterior ao ponteiro
```

## UP/DOWN/LEFT/RIGHT ##

Mesmo que o vim permita mover o cursor com as famosas teclas "hjkl", ainda sim é necessário utilizar as setas do teclado de vez em quando. Dois casos comuns de uso para as setas são para selecionar itens do menu do autocomplete e para navegar no histórico do ex mode. Para esses e outros casos, é possível substituir o uso das setas do teclado pelos seguintes comandos:

```ruby
<C-n> # move o cursor para o próximo item
<C-p> # move o curosr para o item anterior
```

Esses dois comandos também são aceitos em diversos lugares fora do vim, e não precisam de nenhum plugin para funcionar nativamente no editor. Alguns outros lugares onde se pode usar esses dois são comandos são no autocomplete de url do google chrome e no histórico de comandos das shells do linux.

Outros comandos bem interessantes que se ganha ao usar o [vim-rsi](https://github.com/tpope/vim-rsi) se referem a manipulação da posição do cursor em relação a linha atual. Lembrando que cada um desses também funcionam nativamente nas shells do linux:

```ruby
<C-a> # move o cursor para o inicio da linha
<C-e> # move o cursor para o final da linha
<C-f> # move o cursor para frente
<C-b> # move o cursor para trás
```

Em combinação com os comandos **<C-h>** e **<C-d>** previamente apresentados, esses comandos são capazes de deixar o insert mode do vim com um nível de precisão similar ao que se tem no próprio normal mode.

## Conclusão ##

Através de um simples mapeamento para a tecla esc e da instalação de um plugin para tornar obsoleto o backspace, delete e as array keys, foi possível aumentar consideravelmente o poder de manipulação de texto que o vim por padrão oferece.
