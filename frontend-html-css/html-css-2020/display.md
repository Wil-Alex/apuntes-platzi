# Display

- [Display](#display)
  - [Basico](#basico)
  - [Display flex](#display-flex)
  - [Responsive Web Design](#responsive-web-design)
  - [Imagenes responsive](#imagenes-responsive)

## Basico

Dentro de CSS existen los display, los cuales son las maneras en las que los
elementos se colocan en el HTML.

![Display](https://static.platzi.com/media/user_upload/04.%20Displays%20simples-49be1b53-ae5c-42d5-8142-30d54adb4345.jpg)

- El display 'block' indica que el elemento intentara abarcar todo el ancho
  posible, a este display le podemos manipular el 'margin' y el 'padding' en las 4
  direcciones, el elemento 'div' es de este tipo.
- El display 'inline' no ocupa todo el ancho posible, solamente intenta abarcar
  el tamaño que requiera el contenido, por lo que permite posicionar otros
  elementos al lado de el, no se puede manipular el 'margin' y el 'padding' en la
  dirección de arriba y abajo, tampoco se puede utilizar el width o el height.
- El display 'inline-block' permite manipular los elementos de manera que se
  posicionan automáticamente como los elementos 'inline' pero permite manipular
  las propiedades de manera similar a los elemento 'block', es decir no ocupa
  todo el espacio y ademas permite manipular el margin, padding, height y width.

## Display flex

Cuando aplicamos el 'display flex' a un elemento, hace que sus elementos hijos
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

[Guia de flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[Flexbox froggy](https://flexboxfroggy.com/#es)

## Responsive Web Design

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

## Imagenes responsive

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

cuando utilizamos imágenes lo mas recomendable es utilizar el elemento 'figure'
para que contenga al elemento 'picture' y le damos el tamaño al elemento 'figure'
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
