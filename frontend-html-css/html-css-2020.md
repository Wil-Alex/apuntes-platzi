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
  <link rel="stylesheet" href="style.css">
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
- **'html lang="es"'**: El atributo 'lang' indica el idioma en el que esta
  escrito un sitio web y en este caso esta configurado como 'es: español'

El servidor a la hora de intentar mostrar un sitio web siempre tratara de buscar
y encontrar un archivo llamado 'index', el cual corresponde a la pagina principal
de un sitio web.

### El head del sitio web

Dentro de los sitios web existe un elemento llamado 'head' el cual contiene los
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

- **'meta charset="UTF-8"'**: El elemento meta con el atributo 'charset' indica
  el juego de caracteres que usa el proyecto, en este caso utiliza 'UTF-8'
- **'meta name="viewport" content="width=device-width, initial-scale=1.0"'**: El
  elemento meta con el atributo 'name="viewport"' indica como debe comportarse el
  ancho de la pantalla, esto permite escalar correctamente el zoom en un
  dispositivo movil, por lo que es util para el Responsive Web Design.
- **'meta name="description" content="desc"'**: Este elemento configura la
  descripción del sitio y es el texto que los motores de búsqueda muestran cuando
  encuentran el sitio web.
- **'title'**: Indica el titulo del documento y es lo que se muestra en la
  pestaña cuando visualizamos nuestro sitio en el navegador.
- **'link rel="stylesheet" href="style.css"'**: Esta linea enlaza un archivo
  externo al sitio web, en este caso el atributo 'rel="stylesheet"' indica que el
  archivo a enlazar es una hoja de estilos y el atributo 'href' indica la
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
  indica que el enlace se abrirá en otra pestaña y el atributo 'href="#"', hace
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

Para insertar imágenes dentro de nuestro web utilizaremos el elemento 'img' para
indicar la ubicación de la imagen con el atributo 'href' y usaremos el elemento
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
  posicionar la imagen y re-dimensionar la imagen, se podría usar 'div' para esta
  función pero es recomendable usar 'figure' para darle sentido semántico.
- **'img'**: Este elemento permite insertar la imagen y utiliza los atributos
  'href' para indicar la ubicación de la imagen y 'alt' para poner la descripción
  de la imagen que se muestra en caso de que no se pueda cargar la imagen.
- **'figcaption'**: Este elemento dentro de figure permite describir la imagén
  contenida dentro del 'figure', para esto se podría usar un elemento 'p', pero
  es recomendable usar siempre 'figcaption' para darle sentido semantico al sitio.

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

La etiqueta 'video' permite introducir un video al sitio web, utilizando el
atributo 'src' para indicar la ubicación del archivo de video, 'preload="auto"',
indica que el video se comenzara a descargar (no reproducir) automáticamente,
y el atributo 'controls' activa los controles de reproducción.

Si usamos la etiqueta 'source' dentro de una etiqueta video, podemos agregar
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

La manera correcta de crear formularios es utilizando la etiqueta 'form', aunque
es posible crear formularios dentro de un 'div' lo ideas es utilizar 'form' para
darle sentido semántico al sitio, las etiquetas 'input' siempre deben ir dentro
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
  posee el atributo 'action', donde podemos indicar el endpoint o acción a
  realizar con los datos que estamos capturando con el formulario.
- **'label'**: Este elemento sirve para etiquetar un elemento 'input' con un
  texto, es util para la accesibilidad del sitio, el atributo 'for' debe de ser
  igual al atributo 'id' de su 'input' asociado.
- **'span'**: Elemento para contener un texto, en este caso el texto con lo que
  estamos preguntando al usuario.
- **'input'**: Elemento del formulario con el que podemos interactuar, su
  atributo 'type' indica que tipo de datos puede recibir, el atributo 'id' debe
  coincidir con el 'for' de su 'label' asociado, esto identifica el elemento,
  y el atributo 'placeholder' que muestra un texto atenuado en los formularios
  que reciben texto, el atributo 'name' sirve para identificar el elemento en el
  servidor,

[Lista de 'types' disponible para 'input'](https://www.w3schools.com/html/html_form_input_types.asp)

[Input - MDN](https://developer.mozilla.org/es/docs/Web/HTML/Elemento/input)

Para poder enviar los datos de un formulario debemos usar el atributo 'name' para
identificar dichos datos, ademas tenemos el 'input' de tipo 'submit' en cual nos
permite enviar los datos.

El 'input' de tipo 'submit' nos permite enviar nuestros datos, funciona como un
botón, también tenemos el 'input' de tipo 'datetime-local' nos permite en el
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

Dentro de HTML existen 2 tipos de botones, estos son 'button' e 'input type="submit"',
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

HTML nos proporciona en los elementos 'input' herramientas de auto-completado,
las cuales nos intentan dar sugerencias de posible datos que podemos llenar en
esos campos, para activar esta función utilizamos el atributo 'autocomplete' al
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
entre muchas otras podemos usar el elemento 'select', esto nos permite indicarle
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
  elemento select, con el atributo 'name' le damos una identificación en el
  servidor y el atributo 'id' nos permite acceder a ese elemento desde el
  frontend.
- **'option value=""'**: Este elemento nos permite indicar un item dentro
  del 'select', su atributo 'value' es el que sera enviado al servidor, mientras
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
  de tener un 'id' tiene el atributo 'list' el cual debe apuntar a un 'id' de un
  elemento 'datalist', el cual contiene la lista de elementos para el 'select',
  esto permite escribir en el input y el navegador filtrara los datos mientras
  escribimos.
- **'datalist id="cursos"'**: Este elemento contiene elementos 'option' con las
  opciones que puede contener el 'select', su 'id' sirve para vincularse a un
  'input' con el atributo 'list'.
- **'option value=""'**: Este elemento define una opción para el 'select'.
