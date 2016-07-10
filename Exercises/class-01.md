# Exercício 1 - Seletores

Escreva um arquivo Sass que tenha como output o CSS abaixo.

Use seletores e propriedades aninhadas.

```
* {
  margin: 0;
  padding: 0;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

html {
  font-size: 16px;
}

ul {
  padding: 0;
  margin: 0;
}

img {
  border: 0;
}

a {
  text-decoration: none;
}

body {
  background: #fafafa;
}

main {
  width: 90%;
  max-width: 935px;
  margin: 0 auto;
}

header {
  display: flex;
  margin: 30px 0;
  flex-flow: column;
}

header .avatar {
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border-radius: 50%;
  margin: 0 auto;
}

header .desc {
  text-align: center;
}

header h1, h2 {
  display: inline-block;
  margin: 10px 0;
}

header h1 {
  font-size: 28px;
}

header h2 {
  font-size: 24px;
}

header .links {
  list-style: none;
  margin: 10px 0;
}

header .links li {
  list-style: none;
  margin: 0 20px 0 0;
  display: inline-block;
}

.btn-follow {
  margin: 0 20px;
  padding: 6px 14px;
  border-width: 1px;
  border-style: solid;
  border-color: #3897f0;
  color: #3897f0;
  -webkit-border-radius: 4px;
  -moz-border-radius: 4px;
  border-radius: 4px;
}

.btn-follow:hover {
  background: #3897f0;
  color: #fff;
}

.photos {
  list-style: none;
  flex-wrap: wrap;
  justify-content: space-between;
  display: flex;
}

.photos li {
  width: 100%;
  margin: 20px 0;
  position: relative;
}

.photos li img {
  width: 100%;
}

.photos li .img-hover {
  opacity: 0;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.3);
  transition: all 0.3s linear;
}

.photos li:hover .img-hover {
  opacity: 1;
}


@media (min-width: 768px ) {

  header {
    flex-flow: row;
  }

  header .avatar {
    margin: 0 40px;
  }

  header .desc {
    text-align: left;
  }

  .photos li {
  	  width: 30%;
  }

}

```
