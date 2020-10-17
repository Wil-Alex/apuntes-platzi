# CSS

- [CSS](#css)
  - [Uso basico de CSS](#uso-basico-de-css)
  - [Modelo de caja](#modelo-de-caja)
  - [Selectores en CSS](#selectores-en-css)
    - [Herencia de propiedades en CSS](#herencia-de-propiedades-en-css)
    - [Especifidad de selectores](#especifidad-de-selectores)
    - [Combinadores en CSS](#combinadores-en-css)
  - [Unidades de medida en CSS](#unidades-de-medida-en-css)
  - [Posicionamiento de elementos con CSS](#posicionamiento-de-elementos-con-css)

## Uso basico de CSS

El CSS (Cascade StyleSheet, hoja de estilos en cascada), sirve para introducir
estilos a nuestro sitio web, ya que con HTML unicamente definimos el contenido y
la estructura.

Para enlazar un archivo CSS a un documento HTML, lo hacemos de la siguiente forma:

```html
<head>
  <link rel="stylesheet" href="./style.css"><!-- Enlazar CSS desde un archivo externo -->
  <style>
    /* Estilos usando el elemento style, para introducirlo directamente en el HTML */
  </style>
</head>
<body>
  <p style="color: red;"><!-- Aplicar estilos dentro del propio elemento HTML, embebido --></p>
  <p class='parrafo'></p>
</body>
```

Descripción:

- Podemos introducir CSS desde un archivo externo con el elemento 'link' en el
  'head' del documento, al elemento 'link' le pasamos como atributo 'rel' el
  valor 'stylesheet' que indica que el archivo que estamos pasando es un CSS, y
  el atributo 'href' indica la dirección donde esta el archivo.
- Podemos introducir directamente el CSS al documento, usando el elemento 'style',
  solo es recomendable cuando no tenemos muchas reglas.
- Podemos aplicar estilos a un elemento directamente con el atributo 'style', no
  es recomendable utilizarlo.

La sintaxis de CSS consta de selectores y reglas, un selector apunta a 1 o mas
elementos, y las reglas aplican estilos a esos elementos.

```css
selector {
  propiedad: valor-propiedad; /* Declaración = propiedad: valor  */
}
```

En CSS podemos usar selectores de elemento, de clase y por id, utilizamos el '.'
para seleccionar clases y '#' para seleccionar 'id'.

```html
<head>
  <link rel="stylesheet" href="./style.css">
</head>
<body>
  <p class='parrafo'>Un texto</p>
  <p id='texto'>Otro texto</p>
</body>
```

```css
/* elemento */
p { /* Selector de un elemento 'p' */
  color: blue; /* Regla, aplica color azul */
  font-size: 30px;
}

/* class */
.parrafo { /* Selector de la clase 'parrafo', usamos '.' para las clases */
  color: red;
}

/* id */
texto { /** Selector del elemento con id, 'texto', usamos '#'para los id **/
  color: yellow;
  font-size: 24px;
}
```

## Modelo de caja

Cuando trabajamos con CSS simplemente trabajamos con cajas las cuales actúan como
contenedores donde colocamos nuestros elementos HTML, el modelo de caja es el
siguiente:

![Modelo de Caja](https://static.platzi.com/media/user_upload/Captura-46950aca-9335-48ab-8ef5-2f04c4f31683.jpg)

Descripción:

- El 'margin' es un espacio que existe externo al modelo de caja, es decir existe
  entre otros elementos.
- El 'border' indica el limite del modelo de caja.
- El 'padding' es un relleno o margen interno y nos ayuda a posicionar el
  contenido dentro de la caja.
- El 'content' es el contenido del elemento.
  - El 'width' indica el ancho del contenido.
  - El 'height' indica el alto del contenido.

Cada uno de estos elementos tiene algunas propiedades por defecto, las cuales son:

![Modelo de Caja 2](https://static.platzi.com/media/user_upload/Captura1-0fcf145d-42b2-4b2d-8560-0b1c25acf03e.jpg)

Todos los elementos por defecto tienen algunas propiedades, podemos anularlas con
el selector universal '*', para aplicarle a todos los elementos un 'padding' y
'margin' de 0, ademas para que el tamaño de caja tome en cuenta el contenido, el
relleno y el borde usamos la propiedad 'box-sizing' en 'border-box', esta regla
es importante ponerla en todos nuestros proyectos.

Ejemplo:

```css
* { /* el elemento '*' es el selector universal, aplica estas reglas a todo */
  padding: 0; /* Hace que todos los elementos no tengan margen interno o relleno */
  margin: 0; /* Hace que todos los elementos no tengan margen o espacio entre elementos */
  box-sizing: border-box; /* Toma como tamaño de caja content + padding + border, por defecto solo se tomaría el content */
}

main {
  width: 100%; /* Por defecto toma el content como tamaño*/
  height: 500px;
  border: 10px solid blue;
  padding: 20px 35px;
}
```

Tomar en cuenta que cuando una propiedad recibe tamaños si este es 0 no debe de
tener unidad de medida.

## Selectores en CSS

### Herencia de propiedades en CSS

En CSS definimos reglas a elementos que contienen otros elementos, estos otros
elementos hijos, pueden heredar propiedades de su elemento padre, o romper la
herencia con sus propias reglas de CSS, existen 3 modos de herencia en CSS:

- **'inherit'**: Intenta aplicar la regla de su elemento padre, si este no tiene
  la regla definida explora los elementos hasta el elemento superior, si este no
  tiene la regla definida aplica el valor por defecto.
- **'initial'**: Aplica el valor por defecto.
- **'unset'**: Busca la regla en el elemento padre y si no existe aplica el valor
  por defecto.

### Especifidad de selectores

Cuando existen conflictos entre reglas de CSS, es decir cuando a un elemento le
es aplicado varias veces la misma regla con valores distintos, el algoritmo del
navegador sigue en este orden las siguientes reglas:

1. Importancia: El navegador aplica en este orden las reglas
   1. Estilos del navegador
   2. Hoja de CSS (nuestros archivos CSS)
   3. Declaraciones !important en nuestro CSS, (usar !important es mala practica)
2. Especifidad: Es un valor asociado según como se le están aplicando los estilos
   a un elemento en especifico, el peso de cada una de estas formas es la
   siguiente.
   - !important (1,0,0,0,0)
   - Estilos embebidos en el elemento (0,1,0,0,0)
   - #id (0,0,1,0,0)
   - .class (0,0,0,1,0)
   - etiquetas (0,0,0,0,1)
3. Orden de las fuentes: Carga desde la primera linea a la ultima, por lo que una
   regla posterior puede sobre-escribir una regla definida posteriormente, esto
   aplica también cuando tenemos múltiples archivos CSS, ya que un archivo que es
   cargado después de otro, puede sobre-escribir reglas del primero.

![Algoritmo de CSS](https://static.platzi.com/media/user_upload/Captura%20de%20pantalla%20%2863%29-212a5cb5-2d4c-49a0-98a2-d33b54457211.jpg)

Es importante destacar que no se pueden repetir 'id' a lo largo del documento, es
decir es único, y que tampoco un elemento puede tener mas de un 'id', en cambio
un elemento si puede tener mas de una clase, es decir son genéricas.

Los estilos embebidos, tienen mayor importancia que los estilos definidos en una
hoja de estilos CSS, sin embargo se debe evitar su uso en la medida de lo posible,
por ultimo los selectores de etiqueta son los últimos en ser aplicados.

Es una mala practica usar estilos embebidos, estilos marcado con '!important' y
utilizar los 'id' como selectores, en su lugar es recomendable utilizar la
especifidad con los selectores de etiqueta y clase.

### Combinadores en CSS

Con esto podemos modificar la especifidad de nuestros selectores al combinar
varios selectores, los combinadores de CSS son:

```css
 div + p {/* Elementos hermanos cercanos */}
 div ~ p {/* Elementos hermanos generales */}
 div > p {/* Elemento hijo */}
 div p {/* Elemento descendiente */}
```

En este caso el selector de elemento hermano cercano (div + p) aplica el
selector a todos los elementos 'p' que estén inmediatamente después de un
elemento 'div' y que sean elementos hermanos en el árbol de elementos.

El selector de elemento hermano general (div ~ p) aplica el selector a todos los
elementos 'p' que tengan un elemento hermano 'div', sin importar donde se ubique
este elemento 'div'.

El selector de elemento hijo (div > p) selecciona todos los elementos 'p' que
sean hijos directos del elemento 'div', si no son elemento hijos directos del
elemento 'div' no se aplica.

El selector de elemento descendiente (div p) selecciona cualquier elemento 'p'
que este dentro de un elemento 'div' ya sea de manera directa o indirecta.

Todos estos selectores funcionan también con id's y clases de HTML.

[Para practicar los combinadores de CSS](https://flukeout.github.io/)

## Unidades de medida en CSS

Dentro de CSS podemos utilizar varias unidades de medida, las cuales pueden ser
absolutas, es decir son siempre iguales o relativas, las cuales están en función
de otro parámetro para establecer su valor.

Medidas relativas:

**Em**: Esta unidad determina el tamaño basándose en la propiedad 'font-size' del
elemento padre directo, si este no lo tiene, busca en el elemento padre anterior
y asi sucesivamente, si el elemento padre esta definido con otra medida relativa
primero calcula la medida del elemento padre y luego sobre esa medida calcula la
medida del elemento hijo, por ejemplo:

```html
<main class="text-container">
  <p>Soy un texto de ejemplo</p>
    <div>
      <p>Lorem ipsum dolor sit.</p>
    </div>
</main>
```

```css
body{
  font-size: 20px;
}

.text-container {
  font-size: 1.5em;
}

.text-container div {
  font-size: 1.5em;
}
```

**Rem**: Esta unidad de medida relativa toma como base el atributo 'font-size'
de la raíz del documento, normalmente la etiqueta 'html', se comporta como 'em',
es una buena practica utilizar pixeles para las fuentes y luego utilizar 'rem'
para todo lo demás.

```css
html {
  font-size: 62.5%; /* Haciendo esto hacemos que 1 rem sea equivalente a 10px  */
}

p {
  font-size: 1.6rem;  /* 16px */
}
```

**min/max - width/height**: Podemos definir valores mínimos y máximos para los
elementos utilizando las propiedades:

- min-width: Ancho mínimo
- min-height: Altura mínima
- max-width: Ancho máximo
- max-height: Altura máxima

Cuando utilizamos min/max width, debemos utilizar un 'width' como base dado en
unidades de porcentaje.

Cuando utilizamos '%', toma como base su elemento padre y si queremos usar como
base el tamaño de la pantalla del dispositivo que estamos usando podemos usar el
viewport, 'vh' para viewport height y 'vw' para viewport width.

## Posicionamiento de elementos con CSS

Dentro de CSS tenemos la regla 'position' la cual nos permite indicar la manera
en la que los elementos serán posicionados utilizando las reglas de CSS.

Existen varios tipos de posicionamientos en CSS, los cuales son:

- static (default)
- absolute: Tiene una posición fija respecto a los otros elementos y puede ser
  movido de manera independiente a los otros elementos.
- relative: Tiene una posición relativa a su elemento contenedor.
- fixed
- sticky

[Guia de flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[Flexbox froggy](https://flexboxfroggy.com/#es)
