---
layout: post
title: Variáveis de Instância da Classe
date: 2014-05-21 03:13:54 -0200
comments: true
read_time: 2 min
subject: ruby
---

Em ruby, classes são instâncias da classe Class. Além das variáveis de classe padrão @@var, no ruby também é possivel definir variáveis de classe que se comportam internamente como variavéis de instância dessa classe Class. Entenda melhor como isso funciona.

O modo padrão de se definir variaveis de classe em ruby é usando a sintaxe @@my_var, como mostrado a seguir:

```ruby
class MyClass
  @@my_var = "My class variable !"

  def self.my_class_method
    puts @@my_var
  end
end

MyClass.my_class_method
# My class variable !
```

Note que o método é necessario para acessar a variavel, já que toda variavel de classe ou instância em ruby é privada, ou seja, só é possivel accessá-la de fora da classe através de um método.

Esse modo de criar variaveis de classe, porém, pode trazer consequencias indesejaveis. Ao se definir uma variavel de classe usando a sintaxe @@my_var, toda subclasse dela poderá alterar essa variavel, fazendo tanto a super classe quanto todas as outras subclasses dela apontarem para esse novo valor !

```ruby
class MyClass
  @@my_var = "My class variable !"

  def self.my_class_method
    puts @@my_var
  end
end

MyClass.my_class_method
# My class variable !
# => nil

class OtherClass < MyClass
  @@my_var = "A new value..."
  def self.other_class_method
    puts @@my_var
  end
end

MyClass.my_class_method
# A new value...
# => nil

OtherClass.other_class_method
# A new value...
# => nil
```

A modo de contornar esse problema é lembrar que em ruby tudo é um objeto, logo... uma classe também é. De fato, toda classe é uma instância da classe Class.

```ruby
class MyClass; end
MyClass.class
# Class
```

Já que toda classe é um objeto, é razoavel então quere definir uma variavel de instância nesse objeto:

```ruby
class MyClass
  @my_var = "Some class instance variable..."
  def self.my_method
    puts @my_var
  end
end

MyClass.my_var
# Some class instance variable...
```

Desse modo, uma subclasse de MyClass não seria capaz de alterar o valor de @my_var como era o caso do exemplo anterior,
o que torna esse modo o mais seguro para se criar variaveis de classe, ou nesse caso, variaveis de instância da classe.

O exemplo dado foi o mais didático possivel, no mundo real você provavelmente iria abrir a singleton class do objeto e usar o attr_accessor para definir os métodos de leitura e escrita:

```ruby
class MyClass
  class << self
    attr_accessor :my_var
  end
end

MyClass.my_var
# Some class instance variable...
```
