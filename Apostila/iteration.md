#Iterações

Para realização de iterações, existem as diretivas @for, @each e @while.

##@for

A diretiva @for pode ser utilizada de duas formas:

```
@for $var from <start> through <end>
```
Ou

```
@for $var from <start> to <end>
```
A diferença entre as duas é a palavra _through_ ou _to_, no caso da _through_ o loop irá iniciar e finalizará até o número indicado, no caso da _to_ o loop não incluirá a última iteração.

Exemplos:

through 

```
@for $i from 1 through 3 {
  .item-#{$i} { width: 2em * $i; }
}
```

Será compilado para:

```
.item-1 {
  width: 2em; 
}
.item-2 {
  width: 4em; 
}
.item-3 {
 width: 6em;
}
```

to

```
@for $i from 1 to 3 {
  .item-#{$i} { width: 2em * $i; }
}

```
Será compilado para:

```
.item-1 {
  width: 2em; 
}
.item-2 {
  width: 4em; 
}
```

##@each

A diretiva @each trabalha com [listas](https://github.com/Webschool-io/Curso-CSS-SASS/blob/master/Apostila/variables.md#lista).

A estrutura da diretiva @each é: 

```
@each $var in <lista>
```

$var pode ser qualquer variável e < list > é uma lista. Quando processado, $var é atribuido para cada item na lista.

Exemplo:

```

@each $animal in puma, sea-slug, egret, salamander {
  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
  }
}

```

Todos os itens da lista serão percorridos atribuídos à variável $animal, em seguida será impressa a variável $animal interpolada com o termo icon contendo a propriedade background com o valor também interpolado com a variável $animal.

Será compilado para:

```

.puma-icon {
   background-image: url('/images/puma.png'); 
}
.sea-slug-icon {
   background-image: url('/images/sea-slug.png'); }
.egret-icon {
   background-image: url('/images/egret.png');
}
.salamander-icon {
   background-image: url('/images/salamander.png'); 
}

```

##@while

A diretiva @while recebe uma expressão e imprime um o bloco de estilos até que a expressão seja falsa. Esta diretiva é muito parecida com a diretiva @for, é possível criar instruções de loop muito complexos "enquanto" uma condição específica é avaliada como verdadeira.

Exemplo:

```

$i: 6;

@while $i > 0 {
  .item-#{$i} { 
	width: 2em * $i; 
  }
  $i: $i - 2;
}

```
Enquanto $i for maior que 0, será impressa a classe item interpolada com o valor de $i com o with de 2em*$i.
Em seguida o valor de $i é subtraído de 2.

Será compilado para:

```

.item-6 {
  width: 12e
}

.item-4 {
  width: 8em; 
}

.item-2 {
  width: 4em;
}

```
