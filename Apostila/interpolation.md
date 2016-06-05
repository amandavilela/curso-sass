# Interpolation

É possível usar variáveis ​​Sass em seletores e nomes de propriedade com o recurso de interpolação. A interpolação é um recurso que está presente em várias linguagens de programação e permite que valores sejam encaixados dentro de outros valores.
<br><br>
Veja alguns exemplos a seguir.

Utilizando interpolação em nomes de seletores:

```
$name: destaque;
$attr: border;


p.#{$name} {
  #{$attr}-color: blue;
}

```

Será compilado para:

```

p.destaque {
  border-color: blue;
}

```
Utilizando interpolação em nomes de propriedades:
```
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
```
Será compilado para:
```
p {
  font: 12px/30px;
}
```

A interpolação pode ser muito bem utilizada dentro de funções e mixins. Serão exibidas outras formas de utilizar interpolação agregadas com recursos que serão vistos nos próximos tópicos.

___

<p align="center"><a href="variables.md"  title="Anterior"><< Variáveis</a> | <a href="extend.md" title="Próximo">@extend >></a></p>
