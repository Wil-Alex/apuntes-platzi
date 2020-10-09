# Curso Definitivo de HTML y CSS

- [Curso Definitivo de HTML y CSS](#curso-definitivo-de-html-y-css)
  - [Desarrolladores Web](#desarrolladores-web)
  - [Tipos de paginas Web](#tipos-de-paginas-web)
  - [Composición de un elemento HTML](#composición-de-un-elemento-html)
  - [Estructura de un sitio web](#estructura-de-un-sitio-web)
    - [Estructura basica](#estructura-basica)
    - [El head del sitio web](#el-head-del-sitio-web)
    - [El body del sitio web](#el-body-del-sitio-web)

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

## Estructura de un sitio web

### Estructura basica

Los sitios web deben tener una estructura que debe diseñarse utilizando el HTML
semántico y normalmente todos los sitios comparten la estructura básica, esta
estructura básica es:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Soy la descripción de este sitio web">
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
  <meta name="description" content="Soy la descripción de este sitio web">
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
