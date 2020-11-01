# Responsive Web Design

## Media Queries

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

La mejor practica es aplicarlos directamente desde el head de esta manera.

```html
<html>
  <head>
    <link rel="stylesheet" href="style.css"> <!-- Codigo base y mobile -->
    <link rel="stylesheet" href="style.css" media="screen and (min-width: 760px)">
    <link rel="stylesheet" href="style.css" media="screen and (min-width: 1024px)">
  </head>
</html>
```

Break-points recomendados:

- 320px — 480px: Mobile devices
- 481px — 768px: iPads, Tablets
- 769px — 1024px: Small screens, laptops
- 1025px — 1200px: Desktops, large screens
- 1201px and more —  Extra large screens, TV

```css
/* CSS BASE */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
}

.container {
  display: flex;
  flex-wrap: wrap;
}

.box1, .box2, .box3, .box4, .box5 {
  width: 100%;
  min-width: 15rem;
  height: 15rem;
}

.box1 {
  background-color: #003476;
}
.box2 {
  background-color: #0062d2;
}
.box3 {
  background-color: #b4d2f7;
}
.box4 {
  background-color: #d5dfef;
}
.box5 {
  background-color: #dfe1e5;
}
```

![Mostly Fluid](https://static.platzi.com/media/user_upload/slide_mostly_fluid-34a3450d-91a3-4b83-9295-1a24bc61c9b8.jpg)

```css
@media screen and (min-width: 600px) {
  .box2, .box3, .box4 {
    width: 50%;
  }
}

@media screen and (min-width: 800px) {
  .container {
    width: 800px;
    margin: 0 auto;
  }

  .box1 {
    width: 60%;
  }
  
  .box2 {
    width: 40%;
  }

  .box3, .box4 {
    width: 33%;
  }

  .box5 {
    width: 34%;
  }
}
```

![Layout Shifter](https://static.platzi.com/media/user_upload/slide_layout_shifter-43303113-fa25-4108-bef3-ae83d366a845.jpg)

```css
.box4 {
  height: auto;
}

@media screen and (min-width: 600px){
  .box1 {
    width: 25%;
  }
  .box4 {
    width: 75%;
  }
  .box5 {
    width: 100%;
  }
}

@media screen and (min-width: 800px){
  .container {
    width: 800px;
    margin: 0 auto;
  }
    .box1 {
    width: 50%;
    order: 1;
  }
  .box4 {
    width: 100%;
  }
  .box5 {
    width: 50%;
    order: 2;
  }
}
```
