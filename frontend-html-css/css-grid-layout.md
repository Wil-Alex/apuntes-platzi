# CSS Grid Layout

- [CSS Grid Layout](#css-grid-layout)
  - [Fudamentales](#fudamentales)
  - [Filas y Columnas](#filas-y-columnas)

## Fudamentales

En los sitios web, cualquier elemento es una caja, es decir contenedores, los
cuales pueden estar contenidos dentro de otras cajas o bien contener dentro de si
otras cajas.

Utilizando grid layout podemos modificar la disposición de nuestro sitio web, por
ejemplo modificando el numero de columnas de manera dinámica utilizando solamente
CSS sin ningún framework.

[CSS Tricks](https://css-tricks.com/)

- **Grid Container**: va a ser el elemento padre que va a tener puesto un nuevo
  tipo de display: grid. Nos permite colocar otras propiedades para manipular
  nuestro layout.
- **Grid Item**: Son nuestro componentes, contenido, lo que vamos a manejar.
  Nuestras filas o columnas que vamos a mover a nuestro gusto. Son hijos directos
  de grid.

  ```html
    <div class="container">
      <div class="item"></div>
      <div class="item">
       <p class="sub-item"></p>
      </div>
    </div>
  ```

- **Grid Line**: Son las lineas divisorias que le dan estructura a la grilla,
  éstas pueden ser horizontales y verticales y se ubican a ambos lados de una
  fila y una columna. **Ejemplo**: Esta es una línea de una columna.
  ![Grid Line](https://css-tricks.com/wp-content/uploads/2016/03/grid-line.png)
- **Grid Track**: Espacio entre 2 lineas adyacentes de la grilla, puedes pensar
  en ellas como un filas o columna de la grilla. **Ejemplo**: Este es el row track
  entre la 2da y 3ra lineas de fila en la grilla.
  ![Grid Track](https://css-tricks.com/wp-content/uploads/2016/03/grid-track.png)
- **Grid Cell**: Espacio entre 2 líneas de filas y 2 líneas de columnas
  adyacentes en la grilla, igual que las celdas en las tablas. **Ejemplo**: Esta es
  un grid cell entre las lineas de fila 1 y 2, y las líneas de columna 2 y 3 de
  la grilla.
  ![Grid Cell](https://css-tricks.com/wp-content/uploads/2016/03/grid-cell.png)
- **Grid Area**: Espacio rodeado por 4 líneas de la grilla. Esta puede ser un
  conformada por cualquier cantidad de celdas. **Ejemplo**: Esta es una grid area
  conformada entre las filas 1 y 3 y las columnas 1 y 3 de la grilla, y consta
  de 4 celdas.
  ![Grid Area](https://css-tricks.com/wp-content/uploads/2016/03/grid-area.png)

## Filas y Columnas

Para definir cuantas columnas tendrá nuestra rejilla y que dimension tendrán,
podemos usar la propiedad `grid-template-columns`, la cual debe colocarse al
elemento contenedor, de esta forma los elementos serán distribuidos en la
cantidad de columnas que definamos, por ejemplo:

```css
.container {
  display: grid;
  grid-template-columns: 33% 34% 33%; /* 3 Columnas */
  grid-template-columns: 50% 50%; /* 2 Columnas */
  grid-template-columns: 25% 25% 25% 25%; /* 4 Columnas */
}
```

De la misma forma podemos controlar las dimensiones de las filas de nuestra
rejilla utilizando la propiedad `grid-template-rows`, de esta forma:

```css
.container {
  display: grid;
  grid-template-rows: 33% 34% 33%; /* 3 Filas */
  grid-template-rows: 50% 50%; /* 2 Filas */
  grid-template-rows: 25% 25% 25% 25%; /* 4 Filas */
}
```

También podemos definir en una sola instrucción tanto filas como columnas de esta
manera:

```css
.container {
  display: grid;
  grid-template-columns: 33% 34% 33%;
  grid-template-rows: 300px 300px;
  /* grid-template: filas / columnas */
  grid-template: 300px 300px / 33% 34% 33%; /* Es equivalente */
}
```

Dentro de CSS Grid existe dos maneras de controlar las dimensiones de las filas y
columnas dentro de la rejilla de CSS, de esta forma:

- **Grid explicito (explicit grid)** es cuando nosotros definimos el numero de
  filas o columnas. Usa `grid-template-rows` y `grid-template-columns`.
- **Grid implicito (implicit grid)** es cuando tenemos filas o columnas que no
  definimos pero son parte de nuestro grid. Usa `grid-auto-rows` y
  `grid-auto-columns`.

![Grid](https://www.quackit.com/pix/stock/css_grid_explicit_and_implicit_track_sizing.png)

[Grid explicito e implícito](https://www.quackit.com/css/grid/tutorial/explicit_vs_implicit_grid.cfm)

Podemos definir espaciado entre los elementos de la grilla utilizando las
propiedades `grid-gap`, `grid-column-gap` y `grid-row-gap` en el elemento que
contiene a los demás de esta forma:

```css
.container {
  display: grid;
  grid-row-gap: 10px;
  grid-column-gap: 100px;
  grid-gap: 10px 100px; /* Esto es equivalente */
}
```
[Grid Gap](https://cssreference.io/property/grid-gap/)

![grid-gap](https://static.platzi.com/media/user_upload/grid-gap-57fc0852-4be3-4a48-9f0d-54ecaa965cf5.jpg)