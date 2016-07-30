# Variáveis

Um dos recursos mais importantes do Sass é a criação de variáveis, as variáveis permitem armazenar informações para reutilizar em todo o estilo.
<br><br>
Variáveis Sass começam com cifrão e são definidas como propriedades CSS:

```
$bg: #f0f0f3;
```

Recomenda-se que as variáveis Sass sejam nomeadas com hifens ou underlines.
<br>
Exemplo: $bg-azul, $bg_azul


## Tipos de dado
Sass suporta 7 tipos de dados principais:

- Números
- Strings com ou sem aspas
- Cores
- Boleanos
- Null
- Lista de valores
- Maps

### Números

É possível criar variáveis com valores numéricos, os valores podem ser números reais ou inteiros, pode-se colocar unidade ou não.

Exemplo:

```

$width-rem: 3.5rem;
$width-px: 300px;
$width: 300;

aside {
  width: $width-px;
}

```

Será compilado para:

```

aside {
  width: 300px;
}

```

### Strings

Da mesma forma que o CSS aceita uma cadeia de caracteres com aspas ("Lucida Grande"), apóstrofo ('Lucida Grande'), ou sem aspas (sans-serif), o Sass também aceita. O tipo de declaração utilizada no Sass aparecerá no CSS resultante.

Exemplo:

```

$font: "Lucida Grande";
$weight: bold;


section {
  font-family: $font;
  font-weight: $weight;
}

```

Será compilado para:

```

section {
  font-family: "Lucida Grande";
  font-weight: bold;
}

```


### Cores

As cores podem ser atribuídas à variáveis da mesma forma que são declaradas no CSS, o Sass aceita hexadecimais, rgb, rgba e as cores padrão.

Exemplo:


```

$bg: red;
$bg-section: rgba(0, 0, 0, 0.7);
$font-color: #ffffff;

body {
  background: $bg;
  color: $font-color;
}

section {
  background: $bg-section;
}

```

Será compilado para:


```

body {
  background: red;
  color: #ffffff;
}

section {
  background: rgba(0, 0, 0, 0.7);
}

```

### Boleanos e Null

Podem ser criadas variáveis booleanas com os valores true ou false. Também é possível criar uma variável vazia atribuindo a ela o valor null.
<br><br>
Estes tipos de dados não são utilizados diretamente no CSS, logo estas variáveis geralmente são utilizadas em funções e mixins do Sass, conteúdo que será visto mais a frente.

Exemplos:

```

$color-light: false;

$color-dark: true;

$color-dark: null;

```

### Lista

As listas são a forma como Sass representa os valores de algumas declarações CSS como margin: 10px 15px 0 0 ou font-face: Helvetica, Arial, sans-serif. As listas são apenas uma série de valores, separados por espaços ou vírgulas.
<br><br>
Por conta própria as listas não tem tanta utilidade, mas unindo com funções Sass  podem se tornar úteis. A directiva @each (será vista mais adiante) pode adicionar estilos para cada item em uma lista. Existem algumas funções para manipular listas como a função nth function que pode acessar itens em uma lista, a função join que junta múltiplas listas e a função append que adiciona itens a listas.
<br><br>
As listas podem ser separadas por vírgulas ou por espaços.
<br><br>
Exemplos:

```

$animals: puma, sea-slug, egret, salamander;

$animals: puma sea-slug egret salamander;

$animals: "puma", "sea-slug", "egret", "salamander";

```

### Maps

As listas são muito interessantes, porém se limitam a uma dimensão, por esta razão existem os maps que adicionam dimensões às listas, os maps podem ser comparados aos arrays em linguagens de programação, pois sempre estão ligadas à associação entre chaves e valores.
<br><br>
Ao contrário de listas, maps devem sempre estar entre parênteses e  separados por vírgulas. As chaves e valores nos maps podem ser qualquer objeto Sass. Um map só pode ter um valor associado a uma determinada chave (esse valor pode ser uma lista), um valor pode ser associado com várias chaves.
<br><br>
Assim como as listas, maps são na sua maioria manipulados usando funções Sass. A função map-get acessa os valores em um map e a função de map-merge adiciona valores a um map. A directiva @each pode ser usada para adicionar estilos para cada par chave/valor em um mapa.
<br><br>
Os maps não podem ser convertidos para CSS, caso seja usado como o valor de uma variável ou um argumento para uma função CSS irá causar um erro.
<br><br>
Os maps são utilizados como recurso para produzir o CSS, por isso sua utilização sempre vem junto com um loop, função ou mixim.
<br><br>
Exemplo:

```
$social: (
 facebook: #3b5998,
 flickr: #0063db,
 github: #4183c4,
 googleplus: #dd4b39,
 instagram: #517fa4,
 linkedin: #007bb6,
 pinterest: #cb2027,
 soundcloud: #f60,
 twitter: #00aced,
 youtube: #b00
);

```

___

<p align="center"><a href="selectors.md" title="Anterior"><< Seletores</a> | <a href="interpolation.md" title="Próximo">Interpolation >></a></p>
