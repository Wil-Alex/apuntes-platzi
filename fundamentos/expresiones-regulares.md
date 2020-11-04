# Curso de expresiones regulares

- [Curso de expresiones regulares](#curso-de-expresiones-regulares)
  - [Para que sirven las expresiones regulares](#para-que-sirven-las-expresiones-regulares)
  - [Conceptos](#conceptos)
    - [Acerca de las coincidencias](#acerca-de-las-coincidencias)
    - [Caracteres reservados](#caracteres-reservados)
    - [Variables y grupos](#variables-y-grupos)
  - [Elementos](#elementos)
    - [Las clases](#las-clases)
    - [Clases personalizadas](#clases-personalizadas)
  - [Operadores](#operadores)
    - [Los delimitadores](#los-delimitadores)
    - [Los contadores](#los-contadores)
    - [El operador '^' NOT](#el-operador--not)
    - [Inicio '^' y final '$' de linea](#inicio--y-final--de-linea)
  - [Casos especiales](#casos-especiales)
    - [El caso de '?' como delimitador](#el-caso-de--como-delimitador)

## Para que sirven las expresiones regulares

Las expresiones regulares sirven para analizar, procesar, organizar, validar y
descomponer grandes cantidades de datos que estén en formato texto.

## Conceptos

### Acerca de las coincidencias

Las expresiones regulares se basan en coincidencias y una coincidencia es una
cadena de caracteres que cumple con los requisitos de la expresión regular, por
lo que se dice que esa cadena es una cadena valida.

### Caracteres reservados

Los caracteres reservados son caracteres que forman parte de la sintaxis de las
expresiones regulares por lo tanto deben no pueden formar parte del texto que se
esta analizando a menos que se escapen utilizando el carácter `\\`

### Variables y grupos

En las expresiones regulares podemos crear agrupaciones las cuales podemos usar
posteriormente en alguna función que acepte expresiones regulares, estas
variables y agrupaciones se realizan de la siguiente manera:

```regex
^\[(\d{4})\]\s(\w+)$

$1 // \d{4}, el primer grupo guarda 4 dígitos, por ejemplo un año
$2 // \w+, el segundo grupo guarda alguna descripción
```

Las variables pueden ser accedidas con los símbolos `$1`,`$2`,`$3`, ... ,`$9`.

## Elementos

### Las clases

Son conjuntos de caracteres que se espera que se encuentren en esa posición,
las expresiones regulares traen integradas una serie de clases que representan
cierto tipo de caracteres, estas son:

- **\d**: Dígitos, números del 0 al 9.
- **\D**: Negación de **\d**, todos los caracteres excepto los números.
- **\w**: Carácter de palabras, dentro de las expresiones regulares se consideran
  palabras todas las letras, números y el guion bajo.
- **\W**: Negación de **\w**, cualquier carácter que no sea una palabra.
- **\s**: Espacios en blanco y tabuladores.
- **\S**: Negación de **\s**, todos los caracteres excepto espacios en blanco y
  tabuladores.
- **\n**: Salto de linea.
- (**.**): El carácter punto representa cualquier carácter.

Existen muchas otras clases para representar otros conjuntos de caracteres en las
expresiones regulares.

### Clases personalizadas

Dentro de las expresiones regulares es posible definir nuestras propias clases,
es decir nuestro propio conjunto de caracteres que esperamos en una posición
determinada, utilizando los símbolos: `[`, `]`, dentro de los corchetes deben ir
indicados los caracteres que se esperan en esa posición.

Por ejemplo:

```regex
[0-4b-h]
```

Esta expresión regular espera un carácter que sea un dígito entre el 0 y el 4 ó
una letra que este entre la b y la h. Es importante notar que la clase no espera
primero un numero y luego una letra sino que espera cualquiera de los valores que
estén indicados dentro de la clase, para añadir mas conjuntos de caracteres
solamente debemos colocarlos al lado el uno del otro dentro de los corchetes.

## Operadores

### Los delimitadores

Un delimitador en las expresiones regulares es un operador que indica la cantidad
de veces que una clase debe aparecer para que sea valida, existen 3 delimitadores
básicos:

- **'*'**: (0 -> oo), el operador 'asterisco' indica que la clase puede desde no
  aparecer en lo absoluto hasta aparecer una cantidad indefinida de veces
  consecutivas.
- **'+'**: (1 -> oo), el operador 'suma' indica que la clase debe aparecer al
  menos una vez y a partir de ahi una cantidad indefinida de veces consecutivas.
- **'?'**: (0 ó 1), el operador 'signo de interrogación' indica que la clase
  puede aparecer una única vez o ninguna en absoluto.

La manera de utilizar estos operadores es colocar el operador después de una
clase, donde la clase puede ser una clase interna de las expresiones regulares,
una clase personalizada o un carácter solitario.
Es importante notar que las expresiones regulares son evaluadas de izquierda a
derecha y las expresiones validas deben de tener el mismo orden que la expresión
regular.

Por ejemplo:

```regex
\d+\w*
```

- **'\d+'**: Significa que tiene que aparecer por lo menos un carácter.
- **'\w*'**: Inmediatamente después de el dígito o los dígitos puede o no
  aparecer un carácter de palabra.

Ejemplos de cadenas evaluadas por esta expresión regular:

- `0abcd` - valido
- `01234fgh` - valido
- `abcd1234` - invalido - letras antes que los dígitos.
- `4567`  - valido
- `rty` - invalido - solo contiene letras.

### Los contadores

Los contadores o cuantificadores permiten indicar el numero de veces consecutivas
que esta permitido que una clase aparezca, esto se indica con los símbolos de
llaves, `{`, `}`, inmediatamente después de la clase a la que se le aplican estos
valores, las maneras de utilizar esto son las siguientes:

- **'{x,y}'**: Indica que la clase puede aparecer entre `x` y `y` veces.
- **'{x,}'**: Indica que la clase tiene que aparecer como mínimo `x` veces.
- **'{x,x}','{x}'**: Indica que la clase debe aparecer solamente `x` veces,
  ambas notaciones son validas, sin embargo es recomendable usar `{x,x}` siempre,
  debido a temas de compatibilidad.

### El operador '^' NOT

El operador NOT, sirve para negar la expresión de una clase, negar una clase de
expresiones regulares significa que a partir de ese momento esa clase tomara
cualquier carácter excepto los que estén definidos en la clase.

Para negar una clase debemos usar el carácter reservado `^` dentro de una clase,
es decir dentro de los corchetes, esto es debido a que este carácter posee otras
características si este se encuentra fuera de una clase.

Utilizamos este operador de la siguiente manera:

```regex
[^0-5]
```

Esta expresión regular reconocerá como cadena valida cualquier carácter que NO se
encuentre entre el rango de números del 0 al 5.

### Inicio '^' y final '$' de linea

El carácter `^` marca el inicio de la linea por lo que se puede usar para indicar
una clase que debe ir al principio de una linea de la siguiente manera:

```regex
^\d{4}
```

Esta expresión indica que la linea debe empezar por 4 dígitos.

por otra parte el carácter `$` indica el final de linea por lo que se puede
utilizar para expresar como debe ser el final de una linea.

```regex
[abcd]$
```

Esta expresión indica que la linea debe finalizar con uno de los caracteres `a`,
`b`, `c` ó `d`.

Si usamos las 2 expresiones en combinación podemos indicar expresiones para
evaluar lineas completas, esto se puede realizar colocando una expresión regular
entre los símbolos de la siguiente manera, por ejemplo:

```regex
^\d+\w*[abcd]$
```

Esta expresión regular evaluá una cadena como valida si una linea empieza por al
menos un dígito, ninguna ó una palabra y si finaliza con alguno de los caracteres
`a`, `b`, `c` ó `d`.

## Casos especiales

### El caso de '?' como delimitador

Cuando se usa el símbolo `?` después de un delimitador este modifica el
comportamiento por defecto de las expresiones regulares. Por defecto las
expresiones regulares siempre trataran de abarcar la coincidencia mas grande
posible, sin embargo esto puede no ser algo deseado y para omitir este
comportamiento por defecto utilizamos el carácter `?`, por ejemplo:

```regex
.+,
.+?,
```

Si tenemos el siguiente texto:

```text
[csv1,csv2,csv3,csv4,]csv5 // .+,
[csv1,][csv2,][csv3,]csv4 // .+?,
```

En el primer caso la expresión regular validara la linea 1 hasta el elemento
'csv4,', entonces simplemente tendremos una coincidencia para casi toda la linea,
en el segundo caso tenemos validaciones individuales para cada elemento. De esto
podemos observar que el carácter `?` fuerza a que las expresiones regulares sean
lo mas pequeñas posibles.
