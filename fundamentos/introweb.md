# Curso de Introducción a la Web

- [Curso de Introducción a la Web](#curso-de-introducción-a-la-web)
  - [El lenguaje de la computadora](#el-lenguaje-de-la-computadora)
  - [Como funciona el internet](#como-funciona-el-internet)
  - [Historia de la Web](#historia-de-la-web)
  - [Como funciona el navegador](#como-funciona-el-navegador)

## El lenguaje de la computadora

Las computadoras fueron concebidas originalmente para poder realizar grandes
tareas de calculo.

![Historia de la Computación](https://static.platzi.com/media/user_upload/clase2_intro-06de2833-546a-4191-9ad9-3d887e2d3e07.jpg)

Las computadoras tienen dispositivos de entrada y salida, los cuales nos sirven
para interactuar con los datos, es decir nos permite indicarle información a la
computadora y recibir los cálculos que realice.

![Inputs y Outputs](https://static.platzi.com/media/user_upload/clase3_intro-c0f9f9a4-5ccb-41d0-9377-80d70b80cb71.jpg)

Las computadoras utilizan el sistema de numeración binario para codificar toda la
información de manera interna.

![Binario](https://static.platzi.com/media/user_upload/clase4_intro-26bcbabc-5f83-4b68-9452-35058f30515d.jpg)

Para almacenar la información, la computadora internamente agrupa los datos en
grupos de 8 bits, a esta agrupación se le llaman bytes.

![Bits y Bytes](https://static.platzi.com/media/user_upload/clase5_intro-a79d1dbf-479f-4bc8-aaa3-de646d58fa36.jpg)

![Proporciones de bytes](https://static.platzi.com/media/user_upload/pasaje-de-bytes-2-638-1b5a431c-1607-4d7d-8950-3bf2cc049532.jpg)

Debido a que la computadora internamente solo almacena bits y bytes, si queremos
almacenar texto, debemos utilizar una tabla que contenga las equivalencias entre
los caracteres de texto y los números binarios utilizando el código ASCII el cual
solo utiliza 1 byte por carácter, si necesitamos mas caracteres de los que tiene
ASCII, podemos usar la codificación UNICODE, el cual utiliza de 1 a 6 bytes.

[Codigo ASCII](https://www.ascii-code.com/)

[Unicode](https://home.unicode.org/)

[Tabla Unicode](https://unicode-table.com/en/#basic-latin)

![ASCII](https://static.platzi.com/media/user_upload/clase6_intro-7f18aff1-1cba-4875-be64-30152c3ffd07.jpg)

Al igual que con el texto, para codificar colores normalmente usamos el estándar
RGB, el cual indica la proporción de color (rojo, verde y azul) con un numero que
va desde 0 hasta 255.

![RGB](https://static.platzi.com/media/user_upload/clase8_intro-3451ff75-ce9d-44e1-8c40-1c0aa400ec28.jpg)

## Como funciona el internet

El internet es la red de cables que nos permiten conectar distintas computadoras,
nace del proyecto ARPANET, la cual originalmente conectaba 4 universidades, la
mayoría de los cables de internet pasan por cable sub-marinos.

[Cables Sub-marinos de internet](https://www.submarinecablemap.com/)

Para comunicar la información en internet utilizamos los protocolos, las cuales
son reglas que indican como transmitir los datos, el mas común es el protocolo
TCP/IP, el cual indica como se transmiten los datos y la dirección que tiene que
recibirla, estos se hace en 5 capas.

![Protocolos](https://static.platzi.com/media/user_upload/clase10_intro-eeb6fdc9-e7d6-430b-ba77-cb77489ff71d.jpg)

Los ISP son intermediarios que nos permite conectarnos a la infraestructura
global del internet, utilizando los protocolos, ellos se encargan de mantener la
infraestructura.

![ISP](https://static.platzi.com/media/user_upload/clase12_intro-b403c174-a7c9-4317-b90f-db1124e91c07.jpg)

Los servidores DNS, son servidores que mantienen indices donde relacionan una
dirección IP con un string, el cual es el que utilizamos para conectarnos.

![DNS](https://static.platzi.com/media/user_upload/clase12_1_intro-74973d25-0de4-4e82-9e36-8ae3a54ae200.jpg)

## Historia de la Web

La web fue creada por Tim Berners Lee en 1989, mientras trabajaba en el CERN,
originalmente la web fue creada unicamente con 3 protocolos principales: HTML,
URL y HTTP, basado en un modelo de Cliente-Servidor descentralizado.

![Cliente-Servidor](https://secureservercdn.net/45.40.146.28/40b.bf6.myftpupload.com/wp-content/uploads/2015/01/http-protocolo-peticion.png)

El protocolo HTTP, indica las operaciones que el cliente puede solicitar al
servidor, estas operaciones son conocidas como 'métodos HTTP', los métodos
principales son:

| Método HTTP |       Descripción       |
| :---------: | :---------------------: |
|     GET     |     Solicita datos      |
|    POST     |       Envía datos       |
|     PUT     | Crea o reemplaza datos  |
|   DELETE    | Borra datos específicos |

La W3C es una organización que se encarga de definir los estándares que se usaran
en la web, por ejemplo: HTML, CSS y JS, es necesaria la creación de estándares
para que todos los navegadores sean compatibles entre si.
## Como funciona el navegador

Cuando nos conectamos a un sitio web, utilizamos una 'request HTTP', la cual nos
regresa los datos que necesitamos para acceder al sitio web, después realiza
algunas operaciones con estos datos, en un proceso llamado 'Critical Rendering Path'.

![Critical Rendering PATH](https://static.platzi.com/media/user_upload/Untitled%20%2814%29-09c0334b-aa82-4a7f-8efb-494745e9649f.jpg)

El DOM (Document Object Model), es un árbol que contiene los nodos o elementos
que forman todo el contenido de nuestro documento HTML, gracias a esto, podemos
generar interacción utilizando JavaScript o aplicar estilos utilizando CSS.

![DOM](https://static.platzi.com/media/user_upload/introweb-slides_9be717ee-c262-4151-846b-e5248213b4fe-116-f29d92e3-2d70-4b1e-8d4d-951595c333b2.jpg)

El CSSOM (CSS Object Model), es un árbol asociado a los elementos del DOM, el
cual contiene todos los estilos que se deben aplicar al documento HTML.

![CSSOM](https://static.platzi.com/media/user_upload/Screenshot%202020-11-11%20202236-94711fff-48b4-4632-8d4e-54e0fc3e32d4.jpg)

Cuando el navegador procesa el sitio web, solicita al servidor por medio de HTTP
la información, la cual posteriormente procesa, el navegador realiza estos pasos
para procesar los archivos:

1. Procesa el HTML y construye el DOM
2. Procesa CSS y construye el CSSOM
3. Junta el DOM y el CSSOM creando el Render Tree

![Render TREE](https://static.platzi.com/media/user_upload/Screenshot%202020-11-18%20184035-354cf78d-d5ef-48eb-8c07-a034d133a1aa.jpg)

Una vez el navegador tiene el Render Tree, posee a distribuir los elementos en el
espacio de la pantalla, sin inyectar el contenido, usando lo que se conoce como
el Layout.

![Layout](https://static.platzi.com/media/user_upload/introweb-slides_9be717ee-c262-4151-846b-e5248213b4fe-122-8027d081-5587-4159-8b28-bfeec47e3dbc.jpg)

Una vez que el navegador tiene el modelo de caja, aplica los contenidos y los
estilos visuales, para posteriormente dibujarlos en pantalla.

![Paint](https://static.platzi.com/media/user_upload/23-browser-diagram-full-2-5d34606a-c26f-438b-820a-6cf1b9fc339c.jpg)

Una vez esta cargado el HTML y CSS, el motor de JavaScript ejecuta el código de
nuestro proyecto, este motor evalúa el código y posteriormente crea el Abstract
Syntax Tree, el cual contiene el algoritmo y lo ejecuta.

![JavaScript](https://static.platzi.com/media/user_upload/introweb-slides_9be717ee-c262-4151-846b-e5248213b4fe-126-71216f37-2310-4112-b7df-0618a230a88f.jpg)
