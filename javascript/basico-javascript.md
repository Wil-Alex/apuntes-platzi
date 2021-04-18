# Curso Básico de JavaScript

- [Curso Básico de JavaScript](#curso-básico-de-javascript)
  - [¿Que es JavaScript?](#que-es-javascript)
  - [Componentes básicos de JavaScript](#componentes-básicos-de-javascript)

## ¿Que es JavaScript?

JavaScript forma parte de los estándares web (HTML, CSS Y JavaScript), por lo que
es aprobado y estandarizado por la W3C, recientemente se añadió a las tecnologías
web estándar un lenguaje llamado WebAssembly.

Permite convertir paginas web estáticas en dinámicas, esta completamente
orientado al desarrollo web, es un lenguaje interpretado, orientado a objetos,
débilmente tipado y dinámico.

Es un lenguaje multiplataforma con el cual podemos desarrollar para la Web usando
alguno de los frameworks disponibles como: Angular, React, Svelte y Vue, podemos
usarlo para programar aplicaciones móviles con React Native, podemos desarrollar
aplicaciones de escritorio con Electron o podemos usarlo en el Backend e IoT con
NodeJS.

```javascript
// Ejemplo de tipado débil
4 + "7"; // 47
4 * "7"; // 28
2 + true; // 3
false -3; // -3
```

Podemos ver que los valores `true` y `false` devuelven 1 y 0 respectivamente.

Al ser un lenguaje interpretado, el programa se corre linea por linea, esto hace
que en caso de ocurrir un error, este solo sera detectado en el momento que la
linea que genero el error sea leída y ejecutada. JavaScript se compila
just-in-time, es decir sobre la marcha de la ejecución.

Javascript es Backwards Compatible, esto significa todas las funciones nuevas que
sean añadidas a Javascript no romperán código existente, pero no se podrán
utilizar en nuestro entorno de trabajo inmediatamente. Para solucionar esto
existen compiladores como Babel que permite utilizar las nuevas características
del lenguaje, convirtiendo el código escrito en una version moderna de javascript
a una version anterior compatible.

## Componentes básicos de JavaScript

Dentro de JavaScript existen diversos tipos de valores, es decir diferentes tipos
de datos que podemos utilizar en la ejecución de nuestro script, existen los
valores primitivos, los cuales son:

- **Numéricos**: Los cuales se indican de esta forma: `40`
- **Texto o String**: El cual se indica con los símbolos de comillas dobles o
  comillas simples, de esta forma: `"Hola mundo"` o de esta forma `'Hola mundo'`
- **Valores booleanos**: Verdadero o Falso, de esta forma `true` o `false`
- **Empty Values o Valores Placeholder**: Indican cuando existe algún valor
  inexistente, por ejemplo: `null` o `undefined`, este ultimo esta reservado por
  JavaScript y estos pueden generar algún error durante el tiempo de ejecución.

También existen los tipos de datos no primitivos, los cuales pueden contener
dentro de si otros elementos, sean estos primitivos o no, estos son:

- **Arrays**: pueden contener varios elementos dentro de si, a los cuales se
  puede acceder mediante un indice numérico, este se indica de esta forma: `[0,1,2]`
  siendo el símbolo `,` el indicador de separación entre elementos.
