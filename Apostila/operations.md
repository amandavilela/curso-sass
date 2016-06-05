# Operações

Através do Sass é possível realizar os seguintes tipos de operações: operações numéricas, operações com cores e operações com strings.
A seguir veremos detalhadamente cada tipo de operação.

## Number Operations

Sass suporta os seguintes tipos de operações:

- adição +
- subtração -
- multiplicação *
- divisão /
- modulo %

### Adição e Multiplicação

Ao realizar as operações, o Sass preserva unidades, ou seja, não é possível trabalhar em números com unidades incompatíveis e dois números com a mesma unidade que são multiplicados juntos produzirão unidades quadradas (10px * 10px == 100px * px). Esteja ciente de que px * px é uma unidade inválida no CSS, e você obterá um erro do Sass para tentar usar unidades inválidas no CSS.

```
h1 {
    font-size: 2em + 22px; // unidades incompatíveis

    font-size: 5px + 2; // 7px

    font-size: 5px * 2px; // unidade inválida
}
```

### Subtração, números negativos e -

O - pode significar muitas coisas em CSS e em Sass:

- Um operador de subtração (como na 5px - 3px)
- O início de um número negativo (como em -3px)
- Um operador de negação unária (como em - $var)
- Parte de um identificador (fonte-size)

Na maioria das vezes, está claro qual é qual, mas existem algumas boas práticas para assegurar a utilização correta do - :

- Sempre inclua espaços em ambos os lados - quando subtraindo. (4px - 2px)
- Inclua um espaço antes - mas não depois de um número negativo ou de uma negação unária. (4px + -2px)
- Colocar uma negação unária entre parênteses caso ela esteja em uma lista separada por espaço, como em 10px (- $ var).

Os diferentes significados de - têm prioridade na seguinte ordem:

- - como parte de um identificador. Isto significa que o a-1 é uma sequência e não a operação "a-1". A única exceção são as unidades, Sass permite que qualquer identificador válido possa ser utilizado como um identificador, mas os identificadores não podem conter um hífen seguido por um dígito, ou seja 5px-3px é o mesmo que 5px - 3px.
- - entre dois números com nenhum espaço em branco. Isto indica subtração, de modo 1-2 é o mesmo que 1 - 2.
- - no início de uma série literal. Isto indica um número negativo, então 1 -2 é uma lista contendo um e -2.
- - entre dois números, independentemente do espaço em branco. Isto indica subtração, de modo 1 - $var são o mesmo que 1 - $var.
- - antes de um valor. Isso indica que o operador de negação unário; o operador que leva um número e retorna o seu negativo.

### Divisão e /

No CSS é possível utilizar / como uma maneira de separar os números, como o Sass é uma extensão do CSS, também é possível realizar este tipo de declaração, só que  ao mesmo tempo, é possível que o / seja utilizado para a divisão. A seguir serão apresentadas as três situações onde o / é interpretado como divisão.

- Se o valor ou qualquer parte dele é armazenado em uma variável ou retornado por uma função.

```
p {
	$width: 1000px;
	width: $width/2;
}

```

- Se o valor estiver entre parênteses, os parênteses devem estar fora de uma lista.

```
p {
	font-size: (16px / 24px);
}
```

- Se o valor é usado como parte de outra expressão aritmética.

```
p {
	font-size: 2px / 4px + 3px;
}
```

Exemplos de utilização do / :

```
$width: 1000px;
$base-size: 20px;
$line-height: 22px;

p {
  font: 10px/8px bold italic serif; // Imprime CSS
  width: $width/2; // Divisão pois usa uma variável
  width: round(1.5)/2; // Divisão pois usa uma função
  height: (500px/2); // Divisão pois usa parênteses
  margin-left: 5px + 8px/2px;  // Divisão pois usa uma expressão aritimética
  font: (italic bold 10px/8px); Imprime um erro, pois o parênteses estão em volta de uma lista
  font-size: #{$base-size} / #{$line-height}; // Usa interpolção e imprime CSS 
}
```
Será compilado para:
```
p {
  font: 10px/8px;
  width: 500px;
  height: 250px;
  margin-left: 9px; 
  font-size: 20px/22px;
}
```

### Módulo

O operador módulo é o %, como na maioria das linguagens.

Exemplo:

```
$font-size: 27px; 

p {
	font-size: $font-size % 2;
}
```
Será compilado para:
```
p {
	font-size: 1px;
}
```

### Precedência de operadoradores

- Expressões em parênteses são avaliadas primeiro;
- Operadores de multiplicação (*) e divisão (/) tem uma prioridade mais alta em comparação com a adição (+) e os operadores de subtração (-).

## Color Operations
Todas as operações aritméticas são suportadas para valores de cor (hexadecimal, rgb e rgba), onde trabalham por partes. 

Exemplos:

Adição

```
p {
  color: #010203 + #040506;
}

```

01 + 04 = 05, 02 + 05 = 07 e 03 + 06 = 09

Será compilado para:

```
p {
  color: #050709; 
}
```

Multiplicação

```
p {
  color: #010203 * 2;
}
```

01 * 2 = 02, 02 * 2 = 04, and 03 * 2 = 06

Será compilado para:

```
p {
  color: #020406;
}
```

RGBA

```
p {
  color: rgba(255, 0, 0, 0.75) + rgba(0, 255, 0, 0.75);
}
```
Será compilado para:

```
p {
  color: rgba(255, 255, 0, 0.75);
}
```
* Observe que as cores em RGB e RGBA devem ter o mesmo valor de alfa para que a as operações sejam realizadas com eles
* Muitas vezes é mais útil para usar as funções de cor do que tentar operações de cor para conseguir alguns efeitos.

## Operações com String

O sinal de + pode ser utilizado para concatenar strings.

Exemplos:

```
p {
  cursor: e + -resize;
}
```

Será compilado para:

```
p {
  cursor: e-resize;
}
```

A concatenação pode ser realizada com strings entre aspas ou sem aspas, o resultado é sempre uma string.

```
p:before {
  content: "Teste " + Teste;
  font-family: sans- + "serif";
}
```

Será compilado para:

```
p:before {
  content: "Teste Teste";
  font-family: sans-serif;
}
```

Dentro de uma string, a interpolação pode ser utilizada para incluir valores dinâmicos dentro da string:

```
p:before {
  content: "Eu tenho #{2 + 10} moedas.";
}
```

Será compilado para:

```
p:before {
  content: "Eu tenho 12 moedas.";
}
```

Null é tratado como uma string vazia dentro da interpolação.

```
$value: null;
p:before {
  content: "Eu tenho #{$value} moedas.";
}
```

Será compilado para:

```
p:before {
  content: "Eu tenho  moedas.";
}
```

## Operadores Relacionais
Os operadores relacionais (<,>, <=,> =) são suportados para todos os números. Os operadores de igualdade (==,! =) são suportados para todos os tipos.

___

<p align="center"><a href="extend.md"  title="Anterior"><< @extend</a> | <a href="mixins.md" title="Próximo">Mixins >></a></p>
