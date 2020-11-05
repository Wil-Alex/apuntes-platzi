# Maquetación Mobile First

- [Maquetación Mobile First](#maquetación-mobile-first)
  - [Setup inicial](#setup-inicial)
  - [Diseño del sitio Web](#diseño-del-sitio-web)
    - [Estándar BEM](#estándar-bem)
    - [CSS](#css)
    - [Elemento flotante](#elemento-flotante)
    - [Tablas](#tablas)
    - [Scroll](#scroll)
    - [Media Queries](#media-queries)

## Setup inicial

Cuando tenemos un archivo de figma, este nos genera código CSS recomendado, sin
embargo no debemos utilizarlo y solamente debe servirnos como base para tomar las
medidas y de este código unicamente tomaremos la fuente y los colores.

El mobile first tiene la ventaja de que es mas fácil añadir elementos al escalar
el documento que eliminarlos, por lo que crear la vista mas simple en primer
lugar facilita la creación de las vistas de mayor dimensión.

Ademas diseñar el sitio mobile-first ayuda a mejorar el SEO de la pagina web.

Es importante realizar la estructura inicial del proyecto en el archivo HTML, es
decir los elementos: header, main, section y footer.

Es importante que todos los nombres de mis archivos deben de ir en minúsculas,
debemos crear una estructura de carpetas similar a la siguiente:

```text
/
├── css/
├── assets/
│   ├── icons/
│   └── img/
└── index.html
```

Cuando escribimos nuestra hoja de estilos es importante tener un orden en el cual
vamos a declarar nuestras reglas de CSS, el orden recomendado es:

1. Posicionamiento: static, absolute, display, etc.
2. Modelo de Caja: margin, border, padding, etc.
3. Tipografías: tipos de letra, tamaños de letra, etc.
4. Estilos visuales: border-radius, shadow, etc.
5. Otros.

Lo primero que vamos a declarar en la hoja de estilos va a ser el elemento `:root`
el cual va a contener todas las variables que vamos a usar en el documento, esto
se hace de esta manera:

```css
:root { /* Cada uno de los colores que se usan en el sitio web */
  --bitcoin-orange: #f7931a;
  --soft-orange: #ffe9d5;
  --secondary-blue: #1a9af7;
  --soft-blue: #e7f5ff;
  --warm-black: #282623;
  --black: #201e1c;
  --grey: #bababa;
  --off-white: #faf8f7;
  --just-white: #fff;
}
```

Si un estilo de fuente es usado en la mayor parte del proyecto lo podemos colocar
en el elemento `html` y sobre-escribir la propiedad en los elementos individuales
cuando sea requerido, es importante no usar una gran cantidad de tipografías, ya
que esto afecta al rendimiento de la pagina, debemos procurar solo traer la menor
cantidad de fuentes y variantes posibles, asi mismo limitar la cantidad de tipos
de fuente a 2.

## Diseño del sitio Web

### Estándar BEM

Por motivos de SEO un sitio web solamente puede tener 1 elemento `h1`, el cual
debe estar ubicado en la sección de `header`.

Cuando necesitamos colocar elementos al lado de textos, que pueden estar a su vez
dentro de otra etiqueta podemos usar el elemento `span` ya que este utiliza por
defecto el display `inline`, por ejemplo:

```html
<a href="">Conoce Nuestros Planes <span>i</span> </a>
```

Para nombrar las clases que usaremos en el HTML para darle estilos desde CSS,
podemos usar ciertos estándares, por ejemplo:

[Estándar BEM](https://en.bem.info/methodology/quick-start/)

La metodologia BEM funciona basicamente asi:

```html
<!-- header: es el bloque principal -->
<!-- title-container: es el elemento -->
<!-- utilizaremos '--' para unir el bloque con el elemento -->
<header>
  <div class="header--title-container">
</header>
```

### CSS

Cuando utilizamos como ancho de un contenedor principal (header, main y footer)
medidas relativas, lo mas recomendable es fijar un `min-width` en 320px, esto es
porque esta medida es el tamaño de los dispositivos mas pequeños que existen.

Asi mismo también si un elemento requiere tener una altura que cambie de forma
dinámica, pero también requiera ser de un tamaño mínimo podemos fijar la altura
como `min-height` para que escale a partir de ese tamaño base.

```css
header {
  /* Esto nos permite utilizar gradientes de color en el archivo CSS */
  background: linear-gradient(207.8deg, #201E1C 16.69%, #F7931A 100%);
}

header h1 {
  /* Esto nos permite indicar el interlineado del texto */
  line-height: 2.6rem;
}
```

Esta permitido colocar elementos `section` dentro de otros elementos `section` si
es requerido por semántica.

Para ver el estado de la implementación de un estándar Web podemos consultar esta
pagina: [Can I Use](https://caniuse.com/)

### Elemento flotante

Un elemento flotante es aquel que visualmente aparenta no estar dentro de ninguna
sección especifica sino parecer estar flotando en la intersección de 2 o mas
secciones.

```css
.header--title-container .header--button {
  position: absolute; /* Nos permite usar left, top, right y bottom */
  left: calc(50% - 114.5px); /* La función calc nos permite calcular de manera
  dinámica ciertas medidas, en este caso toma el tamaño del contenedor, obtiene
  el 50% y le resta 114.5px, que es la mitad de la medida del elemento */
  box-shadow: 0 4px 8px rgba(89, 73, 30, 0.16); /* Sirve para darle el efecto de
  sombra al elemento, para que tenga apariencia de flotabilidad */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.16); /* box-shadow para elementos sobre
  uun fondo oscuro */
}
/* Alternativamente */
.header--title-container .header--button {
  position: absolute;
  top: 100%; /* Lo mueve al final de su elemento contenedor */
  left: 0; /* Elimina cualquier desplazamiento a al izquierda */
  right: 0; /* Elimina cualquier desplazamiento a al derecha */
  display: block;
  margin: 0 auto; /* Esto permite centrar el elemento, es importante realizar los
  pasos anteriores, ya que de lo contrario no funcionara correctamente */
  transform: translateY(-24px); /* Hace retroceder en sentido vertical el
  elemento, en concreto 24px ya que esto es la mitad de la altura del elemento
  como tal, por lo que el elemento queda centrado en el borde de su contenedor */
}

.header--button span {
  display: inline-block; /* Esto es para poder colocar la flecha como background
  ya que span por defecto traer el display 'inline' y debido a esto no se le
  puede colocar background, por lo que debemos utilizar 'inline-block' */
  width: 13px;
  height: 8px;
  margin-left: 10px;
  background-image: url('../assets/icons/down-arrow.svg'); /* Con url(), podemos
  indicar rutas dentro de nuestro proyecto */

  /* Esto permite solucionar algunos bugs que puedan aparecer, es recomendable
  utilizarlo siempre que se introduzca una imagen como background */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
```

Cuando usamos position `absolute` siempre va a buscar el elemento padre mas
cercano que tenga una propiedad position en `relative`, por lo que es importante
ver cual es ese elemento para evitar conflictos posteriormente.

### Tablas

Antes de HTML5 para realizar la maquetación de sitios web, se utilizaban tablas,
si embargo era muy poco practico y a partir de HTML5 se puede estructurar datos
utilizando CSS Grid Layout, ahora bien, para mostrar información es recomendable
utilizar tablas, esto se hace de esta forma:

```html
<table>
  <tr> <!-- Table Row -->
    <td></td> <!-- Table Data -->
  </tr>
</table>
```

[Documentación de Tablas](https://developer.mozilla.org/es/docs/Web/HTML/Elemento/table)

Para diseñar correos electrónicos, se debe utilizar las tablas, ya que solo esta
permitido utilizar HTML4.

Cuando queremos que la tabla tenga un color de fondo, o bordes redondeados,
debemos aplicar el estilo no a la tabla sino a cada una de las celdas de la tabla,
de esta forma:

```css
.currency-table--container table td {
  width: 50%; /* Cada celda ocupa la mitad */
  color: var(--grey); /* Color de fuente */
  background-color: var(--just-white); /* Color de fondo de la celda */
}

.currency-table--container .table__top-left { /* Marca la celda superior izquierda */
  border-radius: 15px 0 0 0; /* Aplica el redondeado a esa celda */
  border-top-left-radius: 15px; /* Esto es equivalente a lo anterior */
}
```

Esto se debe a que el elemento `table` no es visual, por lo que no se le puede
modificar sus propiedades visuales.

### Scroll

Podemos implementar de manera nativa un scroll horizontal, unicamente utilizando
CSS, para esto vamos a usar el siguiente código:

```css
.plans--card {
  /* Diseñamos nuestra tarjeta para el slide */
  margin: 50px 25px 0; /* El segundo valor indica el espacio entre cada tarjeta */
  scroll-snap-align: center; /* Esto permite que el slide centre automáticamente
  los elementos cuando movemos el slide */
}

.plans--slider {
  display: flex; /* Usamos flex para que los elementos queden en horizontal */
  height: 316px;
  overflow-x: scroll; /* Define que acción realizar cuando el contenido se 
  desborde de manera horizontal, en este caso aplica un 'scroll' */
  overscroll-behavior-x: contain;
  scroll-snap-type: x proximity; /* Indica como el navegador debe tomar los
  puntos de snap en un contenedor */
  margin: 0 25px; /* Para tener los espacios en blanco en las tarjetas inicio y
  final */
}
```

### Media Queries

Una vez que nuestro sitio web esta completado para una interfaz movil, podemos
empezar a escalarlo a tamaños mas grandes, utilizando los media queries, podemos
observar que al realizar el sitio mobile-first, realizar la transición a tamaños
mayores es sumamente facil, por ejemplo:

```css
/* media: min-width: 768px */
.product-cards--container {
  display: flex; /* Cambia el comportamiento del contenedor a flex */
  flex-wrap: wrap; /* Habilita wrap para poder visualizarlo a 2 columnas */
  max-width: 1024px; /* Evita que el contenedor crezca demasiado */
  margin: 0 auto; /* Lo mantiene centrado */
}

.plans--slider {
  justify-content: center; /* Mantiene el slider centrado */
  overflow-x: hidden; /* Oculta la barra de desplazamiento ya que no es necesaria */
}

```