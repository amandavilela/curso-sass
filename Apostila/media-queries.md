# @media

A diretiva @media funciona no Sass da mesma forma que funciona no CSS, porém há possibilidade de encaixá-las em regras CSS, desta forma é possível declarar dentro do seletor qual será o comportamento dele de acordo com cada @media.

Exemplo:

```

.sidebar {
  width: 30%;
  @media screen and (orientation: landscape) {
     width: 40%;
  }
}

.container {
  width: 90%;
  @media screen and (orientation: landscape) {
     width: 100%;
  }
}

```
A @media é declarada para cada seletor. No momento de compilação todas as regras da mesma @media são unificadas:

```

.sidebar {
   width: 30%; 
}

.container {
   width: 90%; 
}

@media screen and (orientation: landscape) {
 .sidebar {
    width: 40%; 
 } 
 
 .container {
    width: 90%;
 } 

}

```
### mixins + media + interpolation + @content

A seguir será apresentado um exemplo utilizando mixins, media, interpolação e content, cujo objetivo é simplificar a chamada das diferentes diretivas @media que podem existir em seu CSS.

Primeiramente será explicado o funcionamento da diretiva **@content** em mixins:

A diretiva **@content** serve para incluir blocos de estilo que são passados para o mixin.

Exemplo:

```

$color: white;

@mixin colors($color: blue) {
  background-color: $color;
  @content;
  border-color: $color;
}

.colors {
  @include colors { color: $color; }
}

```
Será compilado para:

```

.colors {
  background-color: blue;
  color: white;
  border-color: blue;
}

```
Exemplo de media + mixin + interpolação + content

```

$tablet-width: 768px;
$desktop-width: 1024px;


@mixin landscape {
   @media screen and (orientation: landscape) {
       @content;
   }
}

@mixin tablet {
   @media (min-width: #{$tablet-width}) {
       @content;
   }
}

@mixin desktop {
   @media (min-width: #{$desktop-width}) {
       @content;
   }
}

```
Foram criadas duas variáveis com as medidas dos dispositivos, logo abaixo foram criados mixins com nomes simplificados, dentro destes mixins é declarada a diretiva @media, observe que quando a @media envolve medidas as variáveis declaradas acima são interpoladas. 
Dentro da media é utilizada uma outra diretiva chamada @content que incluíra os blocos de estilo passados para o mixin.

Exemplo de utilização dos mixins:

```

header {

    padding: 3em;	
  
    @include tablet {
        padding: 2em;
    }

}

```

Será compilado para:

```

header {
  padding: 3em;	
}


@media (min-width: 768px ) {
  header {
		padding: 2em;	
  }
}

```

___

<p align="center"><a href="iteration.md" title="Anterior"><< Iterações</a> | <a href="import.md" title="Próximo">@import >></a></p>
