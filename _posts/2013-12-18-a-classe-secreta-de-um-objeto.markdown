---
layout: post
title: A Classe Secreta de um Objeto
date: 2014-05-22 23:41:12 -0200
comments: true
read_time: 2 min
subject: ruby
---

Em ruby tudo é um objeto. Inclusive classes. O ruby consegue dizer a você a classe de qualquer objeto. Mas ele não conta a história toda...

## Um outro tipo de método ##

Em orientação a objetos, comportamento é descrito através de métodos. Toda linguagem orientada a objetos oferece 2 maneiras para se definir um método: se for um comportamento específico da classe, é usado um método de classe; caso contrario, é usado um método de instância. Em ruby isso não é diferente:

```ruby
class Developer
  def initialize(name)
    @name = name
  end

  def say_my_name
    puts "My name is #{@name}"
  end

  def self.know_how_to_code?
    true
  end
end
```

Porém, existe ainda uma terceira maneira. Em ruby é possível criar métodos diretamente em um objeto. Um método que é definido em um objeto recebe o nome de **singleton method**.

Digamos que em um ponto específico do código um objeto developer tenha que saber falar japonês. Se em nenhum outro lugar esse comportamento for útil, pode-se querer defini-lo pontualmente para aquele objeto:

```ruby
>> matz = developer.new("matz")
>> def matz.speak_japanese
     puts "domo arigato."
   end
>> matz.speak_japanese
=> "domo arigato."

>> dhh = Developer.new("katz")
>> dhh.respond_to?(:speak_japanese)
=> false
>> matz.respond_to?(:speak_japanese)
=> true
```

Um ponto interessante é que, em ruby, métodos de classe nada mais são do que um tipo especial de *singleton method*. O exemplo abaixo mostra a semelhança entre os dois:

```ruby
# método de classe
class Developer
  def self.know_how_to_code?
    true
  end
end

# singleton method
matz = Developer.new("matz")
def matz.speak_japanese;
  "Domo arigato."
end
```

Observe que um método de classe é sempre definido no self da classe, que nada mais é do que a referência para um objeto que na verdade é a própria classe. Logo, definir um método de classe é equivalente a definir um método em um objeto.

## Um outro tipo de classe ##

Quando um singleton method é criado, o ruby o guarda em uma classe especial do objeto chamada de **singleton class**, ou ainda **eigenclass**. Todo objeto em ruby possui sua própria *eigenclass*. A única maneira de se acessar a *eigenclass* de um objeto é através da sintaxe *class*, como mostra o código abaixo:

```ruby
>> developer = Developer.new
>> def developer.speak_japanese
     puts "Domo arigato."
   end
>> eigenclass = class << developer
     self
   end
=> #<Class:#<Developer:0x007fdeb182c778>>

>> Developer.instance_methods.grep /speak/
=> []
>> Developer.methods.grep /speak/
=> []
>> developer.singleton_methods
=> [:speak_japanese]

>> eigenclass.instance_methods.grep /speak/
=> [:speak_japanese]
```

Esse código resume tudo que vem sido dito até agora. O método *speak_japanese* não é um método de instância (linha 10) e nem um método de classe (linha 12) da classe Developer, e sim um singleton method (linha 14) do objeto developer. Além disso, o *singleton method* speak_japanese está realmente definido na *eigenclass*  do objeto developer (linha 17).

## Conclusão ##

A natureza dinâmica do ruby oferece a ele recursos únicos entre as outras linguagens. Os *singleton methods* e a *eigenclass* são exemplos disso. Juntos eles ajudam a formar o quebra cabeça completo do modelo de objetos do ruby.
