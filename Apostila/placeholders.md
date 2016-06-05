#Placeholders

A declaração de placeholders é semelhante a de classes e ids, o # ou . são substituídos por %, a grosso modo pode-se dizer que placeholders são classes que não aparecem no CSS compilado.

Declaração de um placeholder:

```
%center {
    display: block;
    margin: 0 auto;
}
```

Os placeholders são utilizados juntamente com a diretiva <a href=https://github.com/Webschool-io/Curso-CSS-SASS/blob/master/Apostila/extend.md target=”_blank”>@extend</a> que tem como objetivo herdar as propriedades de um seletor CSS.

Utilizando um placeholder:

```
div {
    @extend %center;
}
```

O Sass aplicará o conteúdo do placeholder %center na div.
Isso será compilado para:

```
div {
   display: block;
   margin-left: auto;
   margin-right: auto;
}
```
**Se o reaproveitamento de código pode ser feito com mixins, quais são as reais vantagens de se utilizar o placeholder?**

O mixin é utilizado para blocos de estilo que embora tenham propriedades iguais, os valores são diferentes.

O placeholder é utilizado para reaproveitamento de blocos estáticos.

A principal diferença está na forma como o Sass compila placeholders e mixins, e a chave disso é o **agrupamento de seletores**. O Sass duplica a saída de um mixin toda vez que ele é utilizado, o que resulta em um CSS duplicado e consequentemente uma folha de estilo maior. Já na compilação dos placeholders, ocorre o agrupamento de seletores.

Exemplo:

```
@mixin center {
    display: block;
    margin: 0 auto;
}

div {
    @include center;
}

.container {
    @include center;
}
```
Será compilado para:

```
div {
    display: block;
    margin: 0 auto;
}

.container {
    display: block;
    margin: 0 auto;
}
```
Observe que os seletores não foram agrupados.

Vamos ver o mesmo exemplo utilizando um placeholder:

```
%center {
    display: block;
    margin: 0 auto;
}

div {
    @extend %center;
}

.container {
    @extend %center;
}
```
Será compilado para:

```
div, .container {
    display: block;
    margin: 0 auto;
}
```
Os seletores foram agrupados e isso ocorre devido ao objetivo do mixin que é ter conteúdo dinâmico, portanto raramente vão ter seletores com propriedades iguais para serem agrupados. Como o propósito do placeholder é reaproveitar blocos estáticos, que sempre terão o mesmo conteúdo, ocorre o agrupamento de seletores.

___

<p align="center"><a href="functions.md"  title="Anterior"><< Funções</a> | <a href="conditions.md" title="Próximo">Condições >></a></p>
