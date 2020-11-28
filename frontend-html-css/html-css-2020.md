# Curso Definitivo de HTML y CSS

- [Curso Definitivo de HTML y CSS](#curso-definitivo-de-html-y-css)
  - [Desarrolladores Web](#desarrolladores-web)
  - [Tipos de paginas Web](#tipos-de-paginas-web)
  - [Composición de un elemento HTML](#composición-de-un-elemento-html)
  - [Estructura de un sitio web](#estructura-de-un-sitio-web)
    - [Estructura básica](#estructura-básica)
    - [El head del sitio web](#el-head-del-sitio-web)
    - [El body del sitio web](#el-body-del-sitio-web)
  - [Multimedia en HTML](#multimedia-en-html)
    - [Imágenes](#imágenes)
    - [Video](#video)
  - [Formularios](#formularios)
    - [General](#general)
    - [Auto-completado y required](#auto-completado-y-required)
    - [Elemento 'select'](#elemento-select)
  - [Accesibilidad](#accesibilidad)
  - [CSS](#css)
    - [Uso basico de CSS](#uso-basico-de-css)
    - [Modelo de caja](#modelo-de-caja)
    - [Selectores en CSS](#selectores-en-css)
      - [Herencia de propiedades en CSS](#herencia-de-propiedades-en-css)
      - [Especifidad de selectores](#especifidad-de-selectores)
      - [Combinadores en CSS](#combinadores-en-css)
    - [Pseudo-clases y Pseudo-elementos en CSS](#pseudo-clases-y-pseudo-elementos-en-css)
    - [Unidades de medida en CSS](#unidades-de-medida-en-css)
    - [Posicionamiento de elementos con CSS](#posicionamiento-de-elementos-con-css)
    - [Variables en CSS](#variables-en-css)
    - [Web fonts](#web-fonts)
  - [Display](#display)
    - [Basico](#basico)
    - [Display flex](#display-flex)
    - [Responsive Web Design](#responsive-web-design)
    - [Imagenes responsive](#imagenes-responsive)

## Desarrolladores Web

Un desarrollador Frontend es un desarrollador que se encarga de programar y
diseñar los elementos de un sistema web que se encuentran del lado del cliente,
esta persona debe ser capaz de utilizar herramientas como:

- El estándar: HTML, CSS y JavaScript
- Frameworks de CSS: Materialize, Bootstrap, etc
- Frameworks de JavaScript: React, Angular, Vue.js, etc.
- Preprocesadores de CSS: Less, Stylus, Sass, etc.
- Compilador/Empaquetador de JavaScript: Babel, Webpack, etc.

Un desarrollador Backend es aquel que se dedica a programar la lógica del lado
del servidor como por ejemplo la conexión a la base de datos, esta persona debe
ser capaaz de utilizar algunas herramientas como:

- Lenguajes de programación: JavaScript, PHP, Python, Ruby, etc.
- Frameworks para desarrollo web: Express.js, Laravel, Flask, Rails, etc.
- Infraestructura de la nube: GCP, Azure, AWS, etc.
- Bases de Datos: MySQL, PostgreSQL, MongoDB, etc.

Un desarrollador FullStack es una persona que tiene conocimientos de frontend y
backend por lo que entiende el funcionamiento de todo el sistema y puede tomar
decisiones de cualquier parte del proyecto, sin embargo tiene un enfoque o
especialidad en alguna rama en especifico.

## Tipos de paginas Web

Existen básicamente 2 tipos de paginas web, las paginas estáticas, las cuales
contienen unicamente información y no poseen ningún tipo de interacción o
conexión con una base de datos y las paginas dinámicas, o aplicaciones web son
aquellas que poseen algún tipo de interacción con el usuario y normalmente tienen
alguna conexión con una base de datos.

## Composición de un elemento HTML

Los elementos html están compuesto de:

- Etiqueta de apertura
- Atributos (opcional)
  - Atributos simples: Son aquellos que no tienen ningún valor asociado.
  - Atributos compuestos: Definen algún valor asociado.
- Contenido (opcional): Solo puede existir si existe etiqueta de cierre.
- Etiqueta de cierre (opcional): No existe para algunas etiquetas.

Ejemplo:

```html
<tag attr1="value1" attr2> [contenido] </tag>
```

[Lista de etiquetas en HTML](https://htmlreference.io/)

## Estructura de un sitio web

### Estructura básica

Los sitios web deben tener una estructura que debe diseñarse utilizando el HTML
semántico y normalmente todos los sitios comparten la estructura básica, esta
estructura básica es:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="desc">
  <title>Document</title>
  <link rel="stylesheet" href="./style.css">
</head>
<body>
  <header>
    <!-- Encabezado del sitio -->
    <nav> <!-- Barra de navegación --> </nav>
  </header>
  <main>
    <!-- Contenido principal del sitio -->
    <section>
      <!-- sección de contenido -->
      <article> <!-- Articulo de una sección --> </article>
    </section>
  </main>
  <footer> <!-- Pie de pagina del sitio --> </footer>
</body>
</html>
```

- **'!DOCTYPE html'**: Esta linea indica que se usara la versión 5 del estándar
  HTML (HTML5)
- **'html lang="es"'**: El atributo `lang` indica el idioma en el que esta
  escrito un sitio web y en este caso esta configurado como `es: español`

El servidor a la hora de intentar mostrar un sitio web siempre tratara de buscar
y encontrar un archivo llamado `index`, el cual corresponde a la pagina principal
de un sitio web.

![Estructura de un sitio web](https://static.platzi.com/media/user_upload/Captura%20de%20pantalla%20%2817%29-f08bb2df-26d7-4221-aebc-c84dd0b015e1.jpg)

![Estructura de un sitio web 2](https://static.platzi.com/media/user_upload/An%20Overview%20of%20HTML5%20Semantics-bfc15245-ca9f-4e5e-b888-4744eb8fca05.jpg)

### El head del sitio web

Dentro de los sitios web existe un elemento llamado `head` el cual contiene los
meta-datos y otra información importante que el proyecto requiere para funcionar
correctamente pero que no debe ser visible para el usuario, por ejemplo: scripts,
hojas de estilos y meta-datos, normalmente la estructura de un head es similar a
esta:

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="desc">
  <title>Document</title>
  <link rel="stylesheet" href="style.css">
</head>
```

Descripción:

- **'meta charset="UTF-8"'**: El elemento meta con el atributo `charset` indica
  el juego de caracteres que usa el proyecto, en este caso utiliza `UTF-8`
- **'meta name="viewport" content="width=device-width, initial-scale=1.0"'**: El
  elemento meta con el atributo `name="viewport"` indica como debe comportarse el
  ancho de la pantalla, esto permite escalar correctamente el zoom en un
  dispositivo movil, por lo que es util para el Responsive Web Design.
- **'meta name="description" content="desc"'**: Este elemento configura la
  descripción del sitio y es el texto que los motores de búsqueda muestran cuando
  encuentran el sitio web.
- **'title'**: Indica el titulo del documento y es lo que se muestra en la
  pestaña cuando visualizamos nuestro sitio en el navegador.
- **'link rel="stylesheet" href="style.css"'**: Esta linea enlaza un archivo
  externo al sitio web, en este caso el atributo `rel="stylesheet"` indica que el
  archivo a enlazar es una hoja de estilos y el atributo `href` indica la
  ubicación del archivo.

### El body del sitio web

Dentro del elemento body se encuentra el contenido del sitio web que debe ser
mostrado al usuario, por lo que es la parte visible del sitio, este elemento esta
compuesto por 2 tipos de elementos:

- Los elementos contenedores que no contienen contenido por si mismo y sirven
  para darle estructura al sitio y contener a el otro tipo de elemento, los
  elementos de contenido.
- Los elementos de contenido son los que contienen la información del sitio y por
  lo tanto todo el texto, imágenes, videos u otros contenidos que tenga el sitio.

Los elemento contenedores aparte de dar estructura al sitio, también le dan las
propiedades semánticas al sitio, lo cual es util cuando trabajamos con los
motores de búsqueda.

Ejemplos de elementos contenedores:

- **div**: Divisiones genéricas dentro de un sitio web.
- **header**: Sección superior de un sitio web.
- **nav**: Barra de navegación de un sitio web.
- **main**: Es el contenido principal del sitio web.
- **section**: Este elemento representa una de las secciones de un sitio web.
- **article**: Este elemento representa un articulo dentro de una sección.
- **ul,ol**: Listas ordenadas o desordenadas.
- **li**: Elemento de una lista.
- **footer**: Pie de pagina de un sitio web.

Ejemplos de elementos de contenido:

- **p**: Párrafo.
- **h1,h2,...,h6**: Elementos de encabezado, para títulos de un sitio web.
- **a**: Elemento de ancla, para crear enlaces, el atributo 'target="_blank"",
  indica que el enlace se abrirá en otra pestaña y el atributo `href="#"`, hace
  referencia a la misma pagina e impide que se recargue al hacer click en el
  enlace.
  
## Multimedia en HTML

### Imágenes

Dentro de nuestro sitio web podemos insertar imágenes, existen básicamente 2
tipos de imágenes:

- Lossless: Formato sin perdida, este tipo de imágenes normalmente son de alta
  calidad y pueden estar comprimidos, sin embargo normalmente son muy pesadas.
- Lossy: Formato con perdida, estas imágenes son mas ligeras y puede que tengan
  una peor calidad ya que se eliminan ciertos datos para reducir su tamaño.

Para el desarrollo web lo ideal es que las imágenes tengan un tamaño de **alrededor
de 70KB.**

|        | Categoría |       Paleta        |                   Uso                    |
| :----: | :-------: | :-----------------: | :--------------------------------------: |
| PNG-8  | Lossless  |     256 colores     | Animaciones, gráficas con colores planos |
| PNG-16 | Lossless  |     256 colores     |     Transparencia, ideal para iconos     |
| PNG-24 | Lossless  | Colores ilimitados  |     Similar a PNG-8 con mas colores      |
|  JPEG  |   Lossy   | Millones de colores |          Imágenes y fotografías          |
|  SVG   | Lossless  | Colores ilimitados  |  Gráficos vectoriales, Alta resolución   |

Podemos comprimir imágenes para utilizarlas en nuestro sitio web en:

- [Tiny PNG](https://tinypng.com/)
- [Verexif](https://www.verexif.com/)
- [Squoosh](https://squoosh.app/)

Y también podemos descargar imágenes, vectores e iconos para nuestro sitio web en:

- [Flaticon](https://www.flaticon.com/)
- [Freepik](https://www.freepik.es/)
- [Unsplash](https://unsplash.com/)
- [Pexels](https://www.pexels.com/es-es/)

Para insertar imágenes dentro de nuestro web utilizaremos el elemento `img` para
indicar la ubicación de la imagen con el atributo `href` y usaremos el elemento
'figure' que sirve como contenedor para las imágenes, usaremos esto de esta
manera:

```html
<figure>
  <img src="./img/image1.png" alt="Descripción de la imagen">
  <figcaption>Esta es la descripción de la imagen</figcaption>
</figure>
```

Descripción:

- **'figure'**: Este elemento contenedor contiene la imagen y nos sirve para
  posicionar la imagen y re-dimensionar la imagen, se podría usar `div` para esta
  función pero es recomendable usar `figure` para darle sentido semántico.
- **'img'**: Este elemento permite insertar la imagen y utiliza los atributos
  `href` para indicar la ubicación de la imagen y `alt` para poner la descripción
  de la imagen que se muestra en caso de que no se pueda cargar la imagen.
- **'figcaption'**: Este elemento dentro de figure permite describir la imagén
  contenida dentro del `figure`, para esto se podría usar un elemento `p`, pero
  es recomendable usar siempre `figcaption` para darle sentido semantico al sitio.

### Video

Dentro de nuestro sitio web podemos introducir videos, esto se hace de la
siguiente manera:

```html
<!-- Forma 1 -->
<video src="./video1.mp4" preload="auto" controls></video>

<!-- Forma 2 -->
<video preload="auto" controls>
  <source src="./video1.mp4"> <!-- Opción 1 -->
  <source src="./video1.mkv"> <!-- Opción 2 -->
  <source src="./video1.webm"> <!-- Opción 3 -->
</video>
```

Podemos observar que existen dos formas de insertar videos dentro de HTML, con la
primera forma podemos insertar un video en un formato especifico, mientras que en
la segunda forma podemos insertar un video en varios formatos distintos, esto es
util para compatibilidad ya que el navegador podrá escoger el formato adecuado
que sea capaz de reproducirlo, el orden de prioridad es de arriba hacia abajo.

La etiqueta `video` permite introducir un video al sitio web, utilizando el
atributo `src` para indicar la ubicación del archivo de video, `preload="auto"`,
indica que el video se comenzara a descargar (no reproducir) automáticamente,
y el atributo `controls` activa los controles de reproducción.

Si usamos la etiqueta `source` dentro de una etiqueta video, podemos agregar
varias ubicaciones de donde descargara el archivo.

También podemos indicar que un video se reproduzca automáticamente al cargarse,
sin embargo esto es considerado una mala practica, se hace de esta forma:

```html
<video src="./video1.mp4" autoplay>
```

Podemos indicar que queremos que un videos inicie y finalize su reproducción en
minutos específicos, esto se hace de esta forma:

```html
<video src="./video1.mp4#t[min-inicio],[min-fin]">
```

## Formularios

### General

Los formularios son la manera en la que interactuamos con el usuario.

> "El mejor formulario es el que no existe."

La manera correcta de crear formularios es utilizando la etiqueta `form`, aunque
es posible crear formularios dentro de un `div` lo ideas es utilizar `form` para
darle sentido semántico al sitio, las etiquetas `input` siempre deben ir dentro
de un contenedor.

```html
<form action="">
    <label for="nombre">
      <span>¿Cual es tu nombre?</span>
      <input type="text" id="nombre" placeholder="Tu Nombre">
    </label>
    <label for="dia-inicio">
      <span>¿Que dia empezaste?</span>
      <input type="date" id="dia-inicio">
    </label>
    <label for="horario">
      <span>¿Que horario prefieres?</span>
      <input type="time" id="horario">
    </label>
  </form>
```

Descripción:

- **'form'**: Este elemento es un contenedor para los elementos del formulario,
  posee el atributo `action`, donde podemos indicar el endpoint o acción a
  realizar con los datos que estamos capturando con el formulario.
- **'label'**: Este elemento sirve para etiquetar un elemento `input` con un
  texto, es util para la accesibilidad del sitio, el atributo `for` debe de ser
  igual al atributo `id` de su `input` asociado.
- **'span'**: Elemento para contener un texto, en este caso el texto con lo que
  estamos preguntando al usuario.
- **'input'**: Elemento del formulario con el que podemos interactuar, su
  atributo `type` indica que tipo de datos puede recibir, el atributo `id` debe
  coincidir con el `for` de su `label` asociado, esto identifica el elemento,
  y el atributo `placeholder` que muestra un texto atenuado en los formularios
  que reciben texto, el atributo `name` sirve para identificar el elemento en el
  servidor,

[Lista de 'types' disponible para 'input'](https://www.w3schools.com/html/html_form_input_types.asp)

[Input - MDN](https://developer.mozilla.org/es/docs/Web/HTML/Elemento/input)

Para poder enviar los datos de un formulario debemos usar el atributo `name` para
identificar dichos datos, ademas tenemos el `input` de tipo `submit` en cual nos
permite enviar los datos.

El `input` de tipo `submit` nos permite enviar nuestros datos, funciona como un
botón, también tenemos el `input` de tipo `datetime-local` nos permite en el
mismo formulario preguntar una fecha y una hora.

Ejemplo:

```html
<form action="">
    <label for="Calendario">
      <span>Calendario</span>
      <input type="datetime-local" name="Calendario" id="Calendario">
    </label>
  <input type="submit">
</form>
```

Dentro de HTML existen 2 tipos de botones, estos son `button` e `input type="submit"`,
el primero se usa en cualquier contexto y el segundo solo en formularios

```html
<!-- Unicamente usar dentro de formularios -->
<input type="submit"> <!-- Por defecto el texto que muestra es Enviar -->
<input type="submit" value="Cargar"> <!-- Podemos personalizar el texto del botón -->

<!-- Botón en cualquier situación -->
<button>Enviar</button>
<button type="submit">Enviar</button> <!-- Si queremos usarla dentro de un formulario -->
```

### Auto-completado y required

HTML nos proporciona en los elementos `input` herramientas de auto-completado,
las cuales nos intentan dar sugerencias de posible datos que podemos llenar en
esos campos, para activar esta función utilizamos el atributo `autocomplete` al
cual le pasamos un valor, el cual indica que tipo de dato debe intentar completar.

[Valores para autocomplete](https://developer.mozilla.org/es/docs/Web/HTML/Atributos/autocomplete)

Si necesitamos que un dato sea obligatorio de llenar podemos añadir el atributo
'required' el cual le indica al navegador que ese campo es obligatorio e informa
un error en caso de que el campo no este rellenado.

```html
<form action="">
  <label for="nombre">
    <span>¿Cual es tu nombre?</span>
    <input
      type="text"
      name="nombre"
      id="nombre"
      autocomplete="name"
      required
    />
  </label>
  <label for="correo">
    <span>¿Cual es tu email?</span>
    <input
      type="email"
      name="correo"
      id="correo"
      autocomplete="email"
      required
    />
  </label>
  <label for="pais">
    <span>¿Cual es tu pais?</span>
    <input
      type="text"
      name="pais"
      id="pais"
      autocomplete="country"
      required
    />
  </label>
  <label for="cp">
    <span>¿Cual es tu codigo postal?</span>
    <input
      type="text"
      name="cp"
      id="cp"
      autocomplete="postal-code"
      required
    />
  </label>
  <input type="submit" />
</form>
```

### Elemento 'select'

Si queremos habilitar la opción de que el usuario pueda seleccionar una opción
entre muchas otras podemos usar el elemento `select`, esto nos permite indicarle
al usuario cuales son las opciones que tiene disponible, se hace de la siguiente
forma:

```html
<select name="cursos" id="cursos">
  <option value="JavaScript">JavaScript</option>
  <option value="HTML5">HTML5</option>
  <option value="CSS3">CSS3</option>
  <option value="Web Standards">Web Standards</option>
</select>
```

Descripción:

- **'select name="" id=""'**: Esta linea indica que estamos trabajando con un
  elemento select, con el atributo `name` le damos una identificación en el
  servidor y el atributo `id` nos permite acceder a ese elemento desde el
  frontend.
- **'option value=""'**: Este elemento nos permite indicar un item dentro
  del `select`, su atributo `value` es el que sera enviado al servidor, mientras
  que lo que este dentro de su contenido es lo que se mostrara al usuario.

Esta es la forma normal de hacer un select, sin embargo puede no ser muy util si
tenemos una gran cantidad de elementos, en ese caso podemos utilizar esta otra
forma:

```html
  <input list="cursos"> <!-- Elemento select -->

    <datalist id="cursos"> <!-- Lista de elementos -->
      <option value="JavaScript"></option>
      <option value="HTML5"></option>
      <option value="CSS3"></option>
      <option value="Web Standards"></option>
    </datalist>
```

Descripción:

- **'input list="cursos"'**: Este elemento define el elemento select, y en lugar
  de tener un `id` tiene el atributo `list` el cual debe apuntar a un `id` de un
  elemento `datalist`, el cual contiene la lista de elementos para el `select`,
  esto permite escribir en el input y el navegador filtrara los datos mientras
  escribimos.
- **'datalist id="cursos"'**: Este elemento contiene elementos `option` con las
  opciones que puede contener el `select`, su `id` sirve para vincularse a un
  `input` con el atributo `list`.
- **'option value=""'**: Este elemento define una opción para el `select`.

## Accesibilidad

La semántica nos permite crear productos que puedan ser utilizados por personas
con algún tipo de discapacidad, la semántica nos permite indicar en que parte del
contenido estamos, por ejemplo: `header` -> Cabecera, `main` -> Parte principal y
'footer' -> Pie de pagina.

Es recomendable aplicar semántica lo mas que se pueda evitando utilizar elementos
de tipo `div`, excepto cuando se requiera para diseñar el sitio web.

Es recomendable utilizar siempre medias relativas para el texto en lugar de usar
medidas absolutas, esto permite escalar el tamaño del texto si es necesario.

La etiqueta `label` sirve para contener elementos `input`, el elemento `label`
tiene un atributo `for` que debe coincidir con el atributo `id` del elemento
'input', esto permite que al hacer click en el `label` ya puedo empezar a
ingresar información en el `input`, esto permite indicarle a los programas de
accesibilidad cuales son los input asociados a un texto.

El atributo `alt` indica a los software de lectura de pantalla cual es la
descripción de la imagen a la que esta apuntando, también se muestra en caso de
que el contenido no pueda cargarse.

El atributo `title` indica el texto que muestra un elemento cuando colocamos el
puntero del ratón encima de el.

## CSS

### Uso basico de CSS

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

- Podemos introducir CSS desde un archivo externo con el elemento `link` en el
  `head` del documento, al elemento `link` le pasamos como atributo `rel` el
  valor `stylesheet` que indica que el archivo que estamos pasando es un CSS, y
  el atributo `href` indica la dirección donde esta el archivo.
- Podemos introducir directamente el CSS al documento, usando el elemento `style`,
  solo es recomendable cuando no tenemos muchas reglas.
- Podemos aplicar estilos a un elemento directamente con el atributo `style`, no
  es recomendable utilizarlo.

La sintaxis de CSS consta de selectores y reglas, un selector apunta a 1 o mas
elementos, y las reglas aplican estilos a esos elementos.

```css
selector {
  propiedad: valor-propiedad; /* Declaración = propiedad: valor  */
}
```

En CSS podemos usar selectores de elemento, de clase y por id, utilizamos el `.`
para seleccionar clases y `#` para seleccionar `id`.

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

### Modelo de caja

Cuando trabajamos con CSS simplemente trabajamos con cajas las cuales actúan como
contenedores donde colocamos nuestros elementos HTML, el modelo de caja es el
siguiente:

![Modelo de Caja](https://static.platzi.com/media/user_upload/Captura-46950aca-9335-48ab-8ef5-2f04c4f31683.jpg)

Descripción:

- El `margin` es un espacio que existe externo al modelo de caja, es decir existe
  entre otros elementos.
- El `border` indica el limite del modelo de caja.
- El `padding` es un relleno o margen interno y nos ayuda a posicionar el
  contenido dentro de la caja.
- El `content` es el contenido del elemento.
  - El `width` indica el ancho del contenido.
  - El `height` indica el alto del contenido.

Cada uno de estos elementos tiene algunas propiedades por defecto, las cuales son:

![Modelo de Caja 2](https://static.platzi.com/media/user_upload/Captura1-0fcf145d-42b2-4b2d-8560-0b1c25acf03e.jpg)

Todos los elementos por defecto tienen algunas propiedades, podemos anularlas con
el selector universal `*`, para aplicarle a todos los elementos un `padding` y
`margin` de 0, ademas para que el tamaño de caja tome en cuenta el contenido, el
relleno y el borde usamos la propiedad `box-sizing` en `border-box`, esta regla
es importante ponerla en todos nuestros proyectos.

Ejemplo:

```css
* { /* el elemento '*' es el selector universal, aplica estas reglas a todo */
  padding: 0; /* Hace que todos los elementos no tengan margen interno o relleno */
  margin: 0; /* Hace que todos los elementos no tengan margen o espacio entre elementos */
  box-sizing: border-box; /* Toma como tamaño de caja content + 'padding' + border, por defecto solo se tomaría el content */
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

### Selectores en CSS

#### Herencia de propiedades en CSS

En CSS definimos reglas a elementos que contienen otros elementos, estos otros
elementos hijos, pueden heredar propiedades de su elemento padre, o romper la
herencia con sus propias reglas de CSS, existen 3 modos de herencia en CSS:

- **'inherit'**: Intenta aplicar la regla de su elemento padre, si este no tiene
  la regla definida explora los elementos hasta el elemento superior, si este no
  tiene la regla definida aplica el valor por defecto.
- **'initial'**: Aplica el valor por defecto.
- **'unset'**: Busca la regla en el elemento padre y si no existe aplica el valor
  por defecto.

#### Especifidad de selectores

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

Es importante destacar que no se pueden repetir `id` a lo largo del documento, es
decir es único, y que tampoco un elemento puede tener mas de un `id`, en cambio
un elemento si puede tener mas de una clase, es decir son genéricas.

Los estilos embebidos, tienen mayor importancia que los estilos definidos en una
hoja de estilos CSS, sin embargo se debe evitar su uso en la medida de lo posible,
por ultimo los selectores de etiqueta son los últimos en ser aplicados.

Es una mala practica usar estilos embebidos, estilos marcado con `!important` y
utilizar los `id` como selectores, en su lugar es recomendable utilizar la
especifidad con los selectores de etiqueta y clase.

#### Combinadores en CSS

Con esto podemos modificar la especifidad de nuestros selectores al combinar
varios selectores, los combinadores de CSS son:

```css
 div + p {/* Elementos hermanos cercanos */}
 div ~ p {/* Elementos hermanos generales */}
 div > p {/* Elemento hijo */}
 div p {/* Elemento descendiente */}
```

En este caso el selector de elemento hermano cercano (div + p) aplica el
selector a todos los elementos `p` que estén inmediatamente después de un
elemento `div` y que sean elementos hermanos en el árbol de elementos.

El selector de elemento hermano general (div ~ p) aplica el selector a todos los
elementos `p` que tengan un elemento hermano `div`, sin importar donde se ubique
este elemento `div`.

El selector de elemento hijo (div > p) selecciona todos los elementos `p` que
sean hijos directos del elemento `div`, si no son elemento hijos directos del
elemento `div` no se aplica.

El selector de elemento descendiente (div p) selecciona cualquier elemento `p`
que este dentro de un elemento `div` ya sea de manera directa o indirecta.

Todos estos selectores funcionan también con id's y clases de HTML.

[Para practicar los combinadores de CSS](https://flukeout.github.io/)

### Pseudo-clases y Pseudo-elementos en CSS

Dentro de CSS tenemos las llamadas pseudo-clases, las cuales sirven para indicar
estados de los elementos dentro del documento, por ejemplo tenemos:

```css
li:hover {
  background-color: blue; /* Cambia el color de fondo cuando el cursor esta sobre el elemento */
}

li:active {
  background-color: red; /* Cambia el color de fondo cuando esta el click presionado */
}
```

También existen los pseudo-elementos, los cuales indican partes especificas de un
elemento, por ejemplo:

```css
li::after {
  content: ' | '; /* Agrega el carácter '|' después del elemento 'li' */
}
```

[Pseudo-Clases](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes)

[Pseudo-Elementos](https://developer.mozilla.org/es/docs/Web/CSS/Pseudoelementos)

### Unidades de medida en CSS

Dentro de CSS podemos utilizar varias unidades de medida, las cuales pueden ser
absolutas, es decir son siempre iguales o relativas, las cuales están en función
de otro parámetro para establecer su valor.

Medidas relativas:

**Em**: Esta unidad determina el tamaño basándose en la propiedad `font-size` del
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

**Rem**: Esta unidad de medida relativa toma como base el atributo `font-size`
de la raíz del documento, normalmente la etiqueta `html`, se comporta como `em`,
es una buena practica utilizar pixeles para las fuentes y luego utilizar `rem`
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

Cuando utilizamos min/max width, debemos utilizar un `width` como base dado en
unidades de porcentaje.

Cuando utilizamos `%`, toma como base su elemento padre y si queremos usar como
base el tamaño de la pantalla del dispositivo que estamos usando podemos usar el
viewport, `vh` para viewport height y `vw` para viewport width.

### Posicionamiento de elementos con CSS

Dentro de CSS tenemos la regla `position` la cual nos permite indicar la manera
en la que los elementos serán posicionados utilizando las reglas de CSS.

Existen varios tipos de posicionamientos en CSS, los cuales son:

- static (default)
- absolute: Tiene una posición fija respecto al elemento padre con `position:relative`
  mas cercano o en su defecto al elemento raiz.
  movido de manera independiente a los otros elementos.
- relative: Tiene una posición relativa a su elemento contenedor.
- fixed
- sticky

### Variables en CSS

```css
:root { /* Hace referencia al HTML */
  --primary-color: #083476; /* De esta manera puedo definir variables */
  --secondary-color: #b4d2f7;
  --header-size: 4rem;
  --font: 1.8rem;
}

header {
  background-color: var(--primary-color); /* Asi puedo llamar a los valores de variables */
}

main {
  font-size: var(--font);
}

footer {
  background-color: var(--secondary-color);
}
```

### Web fonts

Dentro del navegador existen familias de fuentes genéricas, las cuales ya vienen
por defecto en el navegador, estas son:

| **Genericas**  |       **Fuentes**        |
| :------------: | :----------------------: |
|   **serif**    | Times New Roman, Georgia |
| **sans-serif** |    Helvetica, Verdana    |
|  **cursive**   |            ?             |
| **monospace**  | Courier New, Roboto Mono |

Podemos buscar otras fuentes personalizada en:

[Google Fonts](https://fonts.google.com/)

[Para encontrar pares de fuentes](https://fontpair.co/)

Podemos seleccionar fuentes en distintos `weight`, es decir en diferente formas,
por ejemplo: *italic*, **bold**, light, medium, regular, etc. Para integrar estas
fuentes a nuestro documento HTML, usamos:

```css
/* Mala Practica */
/* Font: roboto */
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
```

```html
<html>
  <head>
    <!-- Buena practica -->
    <!-- Font: roboto -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
    <!-- Es mejor cargar las fuentes en el 'head' y siempre antes que el CSS -->
  </head>
</html>
```

Para cargar las fuentes utilizamos:

```css
html {
  font-family: 'Roboto', sans-serif; /* sans-serif o serif, como fallback según el caso */
}

/*  */

```

Según conceptos de diseño hay varias recomendaciones para elegir la fuente que
vamos a utilizar en nuestro sitio web:

- Para textos en digital (Como páginas web) usamos fuente sans-serif.
- Las fuentes serif se recomiendan para impresas o en digital para títulos.

Para calcular el interlineado usamos la siguiente regla:
> 2 puntos más que la fuente (Fuente de 8px pues interlineado de 10px)”

## Display

- [Display](#display)
  - [Basico](#basico)
  - [Display flex](#display-flex)
  - [Responsive Web Design](#responsive-web-design)
  - [Imagenes responsive](#imagenes-responsive)

### Basico

Dentro de CSS existen los display, los cuales son las maneras en las que los
elementos se colocan en el HTML.

![Display](https://static.platzi.com/media/user_upload/04.%20Displays%20simples-49be1b53-ae5c-42d5-8142-30d54adb4345.jpg)

- El display `block` indica que el elemento intentara abarcar todo el ancho
  posible, a este display le podemos manipular el `margin` y el `padding` en las 4
  direcciones, el elemento `div` es de este tipo.
- El display `inline` no ocupa todo el ancho posible, solamente intenta abarcar
  el tamaño que requiera el contenido, por lo que permite posicionar otros
  elementos al lado de el, no se puede manipular el `margin` y el `padding` en la
  dirección de arriba y abajo, tampoco se puede utilizar el width o el height.
- El display `inline-block` permite manipular los elementos de manera que se
  posicionan automáticamente como los elementos `inline` pero permite manipular
  las propiedades de manera similar a los elemento `block`, es decir no ocupa
  todo el espacio y ademas permite manipular el margin, padding, height y width.

### Display flex

Cuando aplicamos el `display: flex` a un elemento, hace que sus elementos hijos
se comporten de manera flexible, podemos modificar el comportamiento de la
siguiente manera:

```css
.container {
  display: flex; /* Activa el modo 'flex' */
  flex-direction: row; /* ordena los elementos en fila (default) */
  flex-direction: column; /* ordena los elementos en columna, equivalente a no-flex */
  flex-direction: (row|column)-reverse; /* Ordena los elementos en el orden inverso */
  flex-wrap: wrap; /* Permite que los elementos se desplacen de manera automática, cambia el tamaño del contenedor de manera automática */
  justify-content: center; /* Permite alinear el contenido de manera horizontal, en este caso centro */
  justify-content: flex-(end|start); /* Permite alinear los elementos de manera horizontal al principio/final del contenedor */
  justify-content: space-around; /* Permite que exista el mismo espacio alrededor de cada elemento */
  justify-content: space-evenly; /* Permite que exista el mismo espacio entre cada elemento */
  align-items: center; /* Alinear elementos de manera vertical, en este caso centro */
  align-items: flex-(end|start); /* Permite alienar elementos verticalmente hacia arriba o abajo */
  align-items: stretch; /* Hace que los elementos ocupen todo el espacio posible, siempre que no estén definidos sus valores de altura y ancho */
  align-items: baseline; /* Hace que los elementos ocupen unicamente el espacio de su contenido */
  order: (1|2|3|4|5|6|...); /* Permite ordenar elementos */
  flex-grow: 1; /* Indica que ese elemento intentara abarcar todo el ancho posible */
  }
```

- **'order'**: Cuando nosotros indicamos un orden a los elementos, los elementos
  que no tengan un orden se moverán al principio del contenedor, y posteriormente
  se colocaran todos los demás elementos.

```css
.box {
  flex-basis: 10rem; /* Indica el tamaño mínimo que debe tener el elemento */
  flex-grow: 1;
}

.container {
  flex-wrap: wrap;
}
```

- **'flex-basis'**: Esto permite que los elementos tengan un tamaño base.

Es importante notar que cuando utilizamos `flex-direction` en `column` las
propiedades de `justify-content` y `align-items` invierten sus funciones, de la
misma manera cuando utilizamos las variantes `reverse` invertimos el orden en el
que funcionan las reglas `flex-start` y `flex-end`.

Existe la propiedad **'align-self'** que sirve para alinear un elemento en
especifico dentro de un contenedor que tiene el display `flex`, es importante
notar que esta regla se aplica al elemento que se quiere posicionar y no al
elemento que lo contiene.

[Guia de flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[Flexbox froggy](https://flexboxfroggy.com/#es)

### Responsive Web Design

Los breakpoints son las dimensiones en los que se aplican cambios a los elementos
es decir re-posicionar o re-dimensionar los elementos.

```css
@media (min-width: 480px){ /* Cada uno de estos es un break-point */
    /* mobile */
}
@media (min-width: 760px){
    /* tablet */
}
@media (min-width: 1024px){
    /* desktop */
}
```

La mejor estrategia es utilizar mobile-first, es decir diseñar primero la pagina
para dispositivos móviles y posteriormente diseñarlos para dispositivos con
mayores dimensiones, siempre deben ir los media queries al final del archivo CSS.

Siempre se deben aplicar los viewports mas pequeños primero y posteriormente se
aplican los mas grandes.

La mejor practica es aplicarlos directamente desde el head utilizando el atributo
media el cual permite cargar solo los archivos correspondientes al break-point
especifico.

```html
<html>
  <head>
    <link rel="stylesheet" href="style.css"> <!-- Codigo base y mobile -->
    <link rel="stylesheet" href="tablet.css" media="screen and (min-width: 760px)">
    <link rel="stylesheet" href="desktop.css" media="screen and (min-width: 1024px)">
  </head>
</html>
```

Break-points recomendados:

- 320px — 480px: Mobile devices
- 481px — 768px: iPads, Tablets
- 769px — 1024px: Small screens, laptops
- 1025px — 1200px: Desktops, large screens
- 1201px and more —  Extra large screens, TV

Es importante no tener mas de 6 break-points en el proyecto.

![Mostly Fluid](https://static.platzi.com/media/user_upload/slide_mostly_fluid-34a3450d-91a3-4b83-9295-1a24bc61c9b8.jpg)

![Layout Shifter](https://static.platzi.com/media/user_upload/slide_layout_shifter-43303113-fa25-4108-bef3-ae83d366a845.jpg)

![Column Drop](https://static.platzi.com/media/user_upload/slide_column_drop-e1902899-937e-4bf4-9aa4-6d79e06e7180.jpg)

### Imagenes responsive

Cuando utilizamos imágenes y queremos que sean responsive deberíamos descargar al
menos 3 tamaños de imágenes distintas.

```html
<picture>
  <!-- Siempre debe ir la imagen con el viewport mas largo primero -->
  <source media="(min-width: 1024px)" srcset="large.png">
  <source media="(min-width: 760px)" srcset="medium.png">
  <img src="small.png" alt="Imagen de ejemplo"> <!-- Siempre cargamos por defecto la imagen para mobile -->
</picture>
```

cuando utilizamos imágenes lo mas recomendable es utilizar el elemento `figure`
para que contenga al elemento `picture` y le damos el tamaño al elemento `figure`
mientras que a la imagen se le da el tamaño de 100% para que se adapte de manera
automatica a las dimensiones del contenedor.

```html
<figure>
  <picture>
    <source media="(min-width: 1024px)" srcset="large.jpg">
    <source media="(min-width: 760px)" srcset="medium.jpg">
    <img src="small.jpg">
  </picture>
</figure>
```

```css
figure {
  width: 320px; /* Le colocamos el tamaño para mobile */
}

img {
  width: 100%; /* La imagen se adapta al contenedor figure */
}

/* Modificamos el tamaño del figure */
@media screen and (min-width: 760px){
  figure {
    width: 760px;
  }
}

@media screen and (min-width: 1024px){
  figure {
    width: 1024px;
  }
}
```
