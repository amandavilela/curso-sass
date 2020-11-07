# Condições


As diretivas de controle do Sass permitem a utilização de operadores condicionais e iterações. Neste capítulo serão explicadas as diretivas condicionais @if e @else.

A diretiva @if recebe uma expressão e caso essa expressão seja diferente de falso algum comando será executado. Para complementar a diretiva @if, existe a diretiva @else que será executada caso as expressões da @if sejam falsas.

Exemplo:

```

$template: dark;

header {
  @if $template: == dark {
    color: #fff;
    background: #222;
  } @else if $template: == light {
    color: #333;
    background: #fff;
  } @else if $template: == sea {
    color: #1a8acd;
    background: #b1d3ff;
  } @else {
    color: #555;
    background: #f0f0f0;
  }
}

```
No exemplo acima, existe uma variável $template e o esquema de cores do seletor header será atribuído de acordo com o valor da variável $template. Neste caso, o esquema de cores atribuído será o primeiro, pois o valor da variável $template é igual a dark.

O CSS compilado será:

```
header {
  color: #fff;
  background: #222;
}
```

___

<p align="center"><a href="placeholders.md"  title="Anterior"><< Placeholders</a> | <a href="iteration.md" title="Próximo">Iterações >></a></p>
