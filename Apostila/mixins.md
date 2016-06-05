#Mixins

A diretiva @mixin permite definir estilos que podem ser reutilizados em toda a folha de estilo. Os mixins funcionam como uma função que retorna CSS em vez de um único valor.
Muitas vezes temos declarações repetidas várias vezes no arquivo CSS, para corrigir isso, pode-se criar um mixin.

##Como declarar

A declaração do mixin começa com @mixin, em seguida vem o nome do mixin, que pode conter qualquer combinação de caracteres alfabéticos e numéricos sem espaços e os argumentos entre parênteses. O mixin border-radius utilizado como exemplo, só possui um argumento $radius, mas pode-se utilizar vários argumentos desde que eles estejam separados por vírgulas. Por fim, entre chaves vem a definição do mixin que conter qualquer combinação de atributos CSS.


```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}
```` 

Com este mixin criado, não será mais necessário repetir as 4 linhas de código utilizadas para que o border-radius funcione em todos os navegadores.

##Como utilizar

Para utilizar o mixin, basta utilizar a palavra @include, o nome do mixin e os argumentos na ordem utilizada na declaração.

Sass

```
.box { 
   @include border-radius(10px); 
}
```

Será compilado para:

```
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```

##Default Arguments

Na criação do mixin é possível especificar valores padrão para os argumentos, caso o argumento seja passado um argumento diferente o argumento será utilizado, caso contrário o valor padrão será utilizado.

Exemplo:

```
@mixin titulo($size, $color: blue) {
  color: $color;
  font-size: $size;
}

h1 {
  @include titulo(14px);
}

h1 {
  @include titulo(14px, green);
}
```

Será compilado para:

```
h1 {
  color: blue;
  font-size: 14px;
}

h1 {
  color: green;
  font-size: 14px;
}
```

##Keyword Arguments

Keyword Arguments existem a partir Sass 3.1, com os Keyword Arguments, os argumentos ficam explicitos na chamada do mixin e é possível utilizar os argumentos em qualquer ordem.

Exemplos:

```
@mixin titulo($size, $color) {
  color: $color;
  font-size: $size;
}


h1 {
  @include titulo($color: green, $size: 14px);
}
```

Será compilado para:

```
h1 {
  color: green;
  font-size: 14px;
}
```

Embora fique redundante, esta forma pode facilitar a leitura dos mixins, o que é importante para ter um código de fácil manutenção.

##Variable arguments

Às vezes é necessário criar um mixin mais flexível, por exemplo, o padding por exemplos pode ter de um a quatro argumentos. Neste caso pode-se criar um mixin de argumentos variáveis, desta forma os argumentos são empacotados como uma lista.

Exemplo:

```
@mixin pad ($values...) {
  padding: $values;
}

p {
  @include pad(20px);
}

p {
  @include pad(10px 20px);
}

p {
  @include pad(10px 20px 40px);
}

p {
  @include pad(10px 20px 30px 20px);
}

```

Será compilado para:

```
p {
  padding: 20px;
}

p {
  padding: 10px 20px;
}

p {
  padding: 10px 20px 40px;
}

p {
  padding: 10px 20px 30px 20px;
}

```

___

<p align="center"><a href="operations.md"  title="Anterior"><< Operações</a> | <a href="functions.md" title="Próximo">Funções >></a></p>
