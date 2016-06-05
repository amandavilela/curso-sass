#Funções

O Sass possui algumas funções nativas e também possibilita que sejam criadas novas funções.

##Criando uma função

A declaração de uma função começa com @function, em seguida vem o nome da função, que pode conter qualquer combinação de caracteres alfabéticos e numéricos sem espaços, os argumentos entre parênteses e a definição da função entre chaves.

As funções podem acessar quaisquer variáveis definidas globalmente. Uma função pode ter várias declarações contidas dentro dela, é necessário utilizar o @return para definir o valor de retorno da função.

```
@function calc-fluid($target, $container) {
  @return ($target / $container) * 100%;
}
```

##Utilizando uma função

Para utilizar uma função basta colocar o nome e passar os argumentos:

```
div {
  width: calc-fluid(650px, 1000px);
}
```

Será compilado para:

```
div {
  width: 65%;
}
```

##Funções Nativas

Nesta apostila serão mostradas algumas das principais funções nativas do Sass. É possível consultar uma lista com todas as funções nativas no site do <a href="http://sass-lang.com/documentation/Sass/Script/Functions.html" target="_blank">Sass</a>.

###Funções de cor

- rgb($red, $green, $blue)
Retorna uma cor de acordo com os valores passados para o vermelho, verde e azul.

- rgba($red, $green, $blue, $alpha)
Retorna uma cor de acordo com os valores passados para o vermelho, verde, azul e alpha.

- lighten($color, $amount)
Retorna a cor mais clara de acordo com a cor e porcentagem de claridade passada como argumento.

- darken($color, $amount)
Escurece a cor de acordo porcentagem passada como argumento.

###Funções com strings

- unquote($string)
Remove as aspas de uma string

- quote($string)
Adds quotes to a string.
Adiciona aspas em uma string

- str-length($string)
Retorna a quantidade de caracteres de uma string

- to-upper-case($string)
Retorna a string em letras maiúsculas

- to-lower-case($string)
Retorna a string em letras minúsculas

###Funções com números

- percentage($number)
Converte um número sem unidade a uma percentagem

- round($number)
Arredonda um número para o número inteiro mais próximo

- ceil($number)
Arredonda um número até o próximo número inteiro

- floor($number)
Arredonda um número para baixo para o número inteiro anterior

###Funções com listas

- length($list)
Retorna a quantidade de itens de uma lista

- nth($list, $n)
Retorna um item específico em uma lista

- join($list1, $list2, [$separator])
Junta duas listas em uma

- append($list1, $val, [$separator])
Acrescenta um valor único no fim da lista

###Funções com maps

- map-merge($map1, $map2)
Une dois maps em um só map

- map-keys($map)
Retorna uma lista de todas as chaves de um map

- map-values($map)
Retorna uma lista de todos os valores de map

___

<p align="center"><a href="mixins.md"  title="Anterior"><< Mixins</a> | <a href="placeholders.md" title="Próximo">Placeholders >></a></p>
