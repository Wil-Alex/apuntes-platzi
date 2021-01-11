# Curso de Frontend Developer

- [Curso de Frontend Developer](#curso-de-frontend-developer)
  - [Definiciones](#definiciones)
  - [HTML Y CSS](#html-y-css)
  - [DOM, CSSOM y Render Tree](#dom-cssom-y-render-tree)

## Definiciones

- **Internet**: A principios de los años 80 nació esta tecnología Interconnected
  Network o red inter-conectada, y esta es la que hoy en día nos permite compartir
  sonidos, videos e imágenes.
- **WWW**: En 1990 World Wide Web; fue creada por Tim Berners-Lee el cual también
  creo el consorcio de la W3C.
- **W3C**: World Wide Web Consortium y es el consorcio que estandariza y
  supervisa las tecnologías del internet HTTP, URL Y HTML.
- **HTTP**: Hyper Text Transfer Protocol ó protocolo de transferencia de
  hipertexto es la bases que permite la comunicación entre los dispositivos
  conectados en la red por ejemplo computadores y servidores.
- **URL**: Uniform Resource Locator ó el localizador de recursos uniformes más
  conocido como la dirección de un sitio web, es la manera que agregamos un punto
  a la red.
- **HTML**: Hyper Text Markup Language ó lenguaje de marcado de hiper text esta
  es lo que le da la estructura un sitio web como dándonos como herramienta: o
  lista encabezado, párrafo etc.
- **CSS**: Cascade style sheets ú Hoja de estilo en cascada la cual fue creada en
  1994 y son unas series de reglas que describen la apariencia de un sitio web y
  es el navegador que se encarga de agregar estos estilos a nuestro sitio. esta
  surgió por la necesidad de mejorar la apariencia de los sitios web, en ella
  podemos definir el estilo de los componentes html como su tamaño, color, fuente
  entre otras cosas.

## HTML Y CSS

El HTML nos permite definir la estructura de la información dentro de nuestro
sitio web, es decir todos los elementos que lo componen.

[HTML Reference](https://htmlreference.io/)

El CSS nos permite estilizar nuestro sitio web, es decir introducir colores,
fuentes, formas, etc.

[CSS Reference](https://cssreference.io/)

![Como aprender CSS](https://static.platzi.com/media/user_upload/Infografia-Frontend-Javascript-86c602ef-a014-47d7-aadd-1293726d06b2.jpg)

## DOM, CSSOM y Render Tree

Los Objects Models (Modelos de Objetos), transforman el código en HTML y CSS a
objetos internos del navegador, los cuales utiliza para procesar los datos, este
proceso se realiza de manera independiente para la estructura del archivo HTML en
el DOM y para las reglas de CSS en el CSSOM, una vez procesados ambos se combinan
en el árbol de renderizado (Render Tree).

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8"> <!-- Indica la codificación -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Saludo</title>
</head>
<body>
  <h1>Hola !</h1>
</body>
</html>
```

![DOM](https://static.platzi.com/media/user_upload/frontend-developer-slides-comprimido_a4a7a8c9-301f-49e8-b6f9-90928ea798e3-9-cab74eb9-4afc-4422-8fee-d5a8a560739d.jpg)

![CSSOM](https://static.platzi.com/media/user_upload/frontend-developer-slides-comprimido_a4a7a8c9-301f-49e8-b6f9-90928ea798e3-10-29925f2d-2468-4092-9fca-57af22964d07.jpg)

![Proceso](https://static.platzi.com/media/user_upload/frontend-developer-slides-comprimido_a4a7a8c9-301f-49e8-b6f9-90928ea798e3-11-9645a1c8-9b55-4c6a-8f9d-78a534a7d12a.jpg)