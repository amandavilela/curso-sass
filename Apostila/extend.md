# @extend

Com a diretiva @extend é possível herdar estilos de outras classes, sua utilização evita a duplicação de estilos no arquivo final.

Alguns exemplos de utilização:

Temos dois tipos de erro que possui características iguais, porém algumas exceções de cor de acordo com a gravidade do erro.

```
.msg {
  border: 1px solid;
  padding: 4px;
  text-align: center;
}

.msg-error {
  @extend .msg;
  border-color: #ff0000de;
  color: #ff0000de;
}

.msg-alert {
  @extend .msg ;
  border-color: #ff8e00de;
  color: #ff8e00de;
}
```

Será compilado para:

```
.msg, .msg-error,  .msg-alert{
 border: 1px #f00;
 background-color: #fdd;
}

.msg-error {
 border-color: #ff0000de;
 color: #ff0000de;
}

.msg-alert {
 border-color: #ff8e00de;
 color: #ff8e00de;
}
```

Também é possível herdar estilos de pseudo-elementos:

```
a:hover {
  text-decoration: underline;
}

.hoverlink {
  @extend a:hover;
}
```

Será compilado para:

```
a:hover, .hoverlink {
  text-decoration: underline;
}
```
