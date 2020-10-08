# Curso de introducción a la terminal y linea de comandos

- [Curso de introducción a la terminal y linea de comandos](#curso-de-introducción-a-la-terminal-y-linea-de-comandos)
  - [Que es y para que sirve la terminal](#que-es-y-para-que-sirve-la-terminal)
  - [Comandos y conceptos básicos](#comandos-y-conceptos-básicos)
  - [Sistema de archivos](#sistema-de-archivos)
    - [Estructura del sistema de archivos](#estructura-del-sistema-de-archivos)
    - [Punteros dentro del sistema de archivos](#punteros-dentro-del-sistema-de-archivos)
    - [Comandos para ejecutar operaciones en el sistema de archivos](#comandos-para-ejecutar-operaciones-en-el-sistema-de-archivos)
    - [Variaciones del comando 'ls'](#variaciones-del-comando-ls)
    - [Permisos](#permisos)
  - [Buscar](#buscar)
  - [Empaquetar y comprimir](#empaquetar-y-comprimir)
  - [Manejo de texto en la terminal](#manejo-de-texto-en-la-terminal)
    - [Utilidades estándar de manejo de texto](#utilidades-estándar-de-manejo-de-texto)
    - [Flujos estándar](#flujos-estándar)
  - [Procesos](#procesos)
  - [Operaciones remotas](#operaciones-remotas)
  - [Automatización y scripts](#automatización-y-scripts)

## Que es y para que sirve la terminal

La terminal es el medio por el cual el sistema operativo recibe instrucciones de
parte del usuario y las traduce a instrucciones que pueden ser interpretadas por
la computadora.

Utilizar la terminal nos permite realizar operaciones de manera mas eficiente que
por medio de una interfaz gráfica y a su vez nos permite automatizar tareas
largas y complejas.

## Comandos y conceptos básicos

Dentro de la terminal existen varios comandos que nos permiten interactuar con la
computadora y realizar tareas simples, estos comandos son:

```bash
date # Muestra la fecha
echo [TEXTO] # Imprime por pantalla el texto que se le pase
man [COMANDO] # Muestra la ayuda del comando que se le pasa
```

También tenemos un comando que nos permite ver el historial de comandos que se
han ejecutado en la maquina, podemos usar este comando de la siguiente manera:

```bash
history
```

Este comando devuelve como salida algo como esto:

```text
 4325  git status
 4326  git pull
 4327  git commit
 4328  git status
 4329  git push
```

Utilizando el numero que nos devuelve podemos volver a ejecutar un comando que
ejecutamos en el pasado, de esta manera:

```bash
!4325
git status # Esto es equivalente
```

Las variables de entorno son valores que puede ser accedidos por cualquier tipo
de procesos, y estas se definen asi:

```bash
export VAR=[VALUE] # define una variable llamada VAR
echo $VAR # Para acceder al valor de una variable utilizamos el símbolo '$'
```

Sin embargo estas variables no son permanentes, para que las mismas sean
permanentes, tenemos que definirías en uno de estos archivos:

```text
/etc/environment
.zshrc
.bashrc
```

Por ejemplo la variable de entorno $PATH, almacena los directorios donde el
sistema busca los archivos ejecutables.

## Sistema de archivos

### Estructura del sistema de archivos

El sistema de archivos esta conformado por una estructura de archivos y
directorios, donde los directorios actúan como contenedores de archivos o de
otros directorios en una estructura jerárquica, de la siguiente manera:

```text
/
├── directorio1/
│   ├── archivo1
│   ├── archivo2
│   └── directorio2/
├── archivo3
└── archivo4
```

La identificación de un archivo esta conformada por su ubicación mas el nombre
del archivo. No pueden existir 2 archivos que tengan la misma identificación, es
decir no pueden existir 2 archivos en la misma ubicación y con el mismo nombre
de esta manera:

```text
[/ubicación/del-archivo/][nombre-del-archivo]
```

### Punteros dentro del sistema de archivos

Dentro del sistema de archivos existen elementos llamados punteros, la función de
estos es apuntar a otras ubicaciones dentro del sistema de archivos, estos
apuntadores son:

```text
/
├── . # Apunta al directorio actual
└── .. # Apunta al directorio padre
```

### Comandos para ejecutar operaciones en el sistema de archivos

Existen varios comandos para ejecutar operaciones sobre archivos:

```bash
ls # 'List' permite ver los archivos de la ubicación actual
ls -a # Muestra todos los archivos incluyendo los ocultos
pwd # 'Print working directory' muestra la ubicación actual
cd [DIRECTORIO] # 'Change directory' permite movernos a otra ubicación
cd - # Nos mueve a la ubicación donde estábamos previamente
cd ~ # Nos mueve a la ubicación /home/[USUARIO]
touch [NOMBRE ARCHIVO] # Crea un archivo
cp [ACTUAL] [NUEVO] # Copia el archivo [ACTUAL] a la ubicación [NUEVO]
mv [ACTUAL] [NUEVO] # Mueve el archivo desde [ACTUAL] a [NUEVO]
mkdir [DIRECTORIO] # Crea un directorio
rmdir [DIRECTORIO] # Elimina el directorio, solo funciona si el directorio esta vacío
```

### Variaciones del comando 'ls'

El comando 'ls' permite mostrar los archivos y directorios que están dentro de mi
ubicación actual, este comando permite diversas opciones para mostrar los
archivos, estas opciones son:

```bash
ls -a # Muestra los archivos ocultos
ls -t # Muestra los archivos ordenados por fecha de modificación
ls -x # Muestra los archivos ordenados por nombre y luego por extensión
ls -X # Muestra los archivos ordenados por extensión y luego por nombre
ls -l # Muestra los archivos con su información
ls -R # Muestra los archivos de manera recursiva en los sub-directorios
ls -S # Muestra los archivos ordenados de mayor a menor tamaño
ls -h # Muestra los archivos con sus tamaños en KB, MB, etc.
```

### Permisos

Todos los archivos poseen un valor asociado que indica que permisos tienen los
usuarios sobre ellos, estos permisos son: lectura, escritura y ejecución, y estos
permisos pueden ser aplicados para 3 tipo de usuarios: el usuario propietario, el
grupo del usuario propietario y los otros usuarios, para alterar los permisos
tenemos los comandos:

```bash
chmod # (Change mode) Cambiar los permisos
chown # (Change owner) Cambiar el propietario
chgrp # (Change group) Cambiar el grupo
```

Para alterar los permisos podemos usar 2 sintaxis con el comando chmod:

```bash
chmod +x [ARCHIVO] # Añade el permiso de ejecución
chmod +w [ARCHIVO] # Añade el permiso de escritura
chmod +r [ARCHIVO] # Añade el permiso de lectura
chmod -x [ARCHIVO] # Remueve el permiso de ejecución
chmod -w [ARCHIVO] # Remueve el permiso de escritura
chmod -r [ARCHIVO] # Remueve el permiso de lectura
```

También existe el sistema de permisos octal que asigna un valor de 0 a 7 a una
combinación especifica de permisos, de esta manera:

- Lectura: 4
- Escritura: 2
- Ejecución: 1

Para obtener el valor sumamos las cantidades de los permisos que necesitemos y
ese numero representa esa combinación de permisos, el primer dígito representa
los permisos del propietario, el segundo del grupo y el tercero de los otros
usuarios, por ejemplo:

```bash
chmod 644 [ARCHIVO] # Le asigna permisos de lectura y escritura al propietario y solo lectura a los demás
```

## Buscar

Dentro de la terminal tenemos herramientas para realizar búsquedas de archivos
dentro del árbol de directorios en el disco, las herramientas son:

```bash
locate [ARCHIVO] # busca el archivo en una base de datos
whereis [ARCHIVO] # Busca en la PATH donde se encuentra el archivo ejecutable de un comando especifico
find [ARCHIVO] # Busca en el disco duro un archivo especifico
```

Las herramientas locate y whereis hacen básicamente lo mismo pero locate no busca
directamente en el disco sino en una base de datos que se actualiza cada cierto
tiempo, debido a esto puede que no sea capaz de encontrar algún archivo creado
recientemente.

## Empaquetar y comprimir

Cuando trabajamos con archivos a veces es util comprimir archivos o directorios
para poder enviarlos por la red, podemos hacer todas estas operaciones desde la
terminal.

Para comprimir archivos individuales podemos usar la herramienta 'gzip' de la
siguiente manera:

```bash
gzip [ARCHIVO] # Comprimir un archivo
gzip -d [ARCHIVO] # Descomprimir un archivo
```

La herramienta gzip unicamente puede comprimir un archivo, por lo que no nos es
util para comprimir directorios, para hacer esto tenemos que empaquetar los
directorios en un archivo y para eso usamos la herramienta 'tar', de esta forma:

```bash
tar cf [ARCHIVO 1] [ARCHIVO 2] ... [ARCHIVO] # Empaquetar archivos en un archivo tar
tar cf [DIRECTORIO] # Empaquetar un directorio
tar xf [ARCHIVO TAR] # Extrae los archivos de un archivo tar
```

La herramienta tar solo empaqueta los archivos en uno solo, sin embargo podemos
combinarla con gzip para comprimir el archivo tar de esta forma:

```bash
tar czf [ARCHIVO 1] [ARCHIVO 2] ... [ARCHIVO] # Comprimir varios archivos
tar xzf [ARCHIVO TAR] # Extraer los archivos de un archivo tar.gz
```

## Manejo de texto en la terminal

### Utilidades estándar de manejo de texto

Podemos manejar archivos desde la terminal utilizando aplicaciones interactivas
desde la terminal como por ejemplo: vim o nano, también podemos utilizar comandos
para realizar búsquedas, los comandos son los siguientes:

```bash
cat [ARCHIVO] # Imprime el contenido de un archivo
head -n [x] [ARCHIVO] # Imprime las primeras x lineas de archivo, imprime 10 lineas por defecto
tail -n [x] [ARCHIVO] # Imprime las ultimas x lineas de archivo, imprime 10 lineas por defecto
grep -EP [EXPR. REGULAR] [ARCHIVO] # busca en función de una expresión regular dentro del archivo
sed '/s/[ORIGINAL]/[SUSTITUTO]/;' # Permite sustituir una cadena por otra, NO edita el archivo
sed '/s/[ORIGINAL]/[SUSTITUTO]/; /s/[ORIGINAL]/[SUSTITUTO]/;' # Se pueden sustituir varias cadenas al mismo tiempo
```

### Flujos estándar

Los flujos estándar que existen son:

- **stdout**: Salida estándar: Pantalla
- **stdin**: Entrada estándar: Teclado
- **stderr**: Salida de error estándar: Pantalla

Por defecto los flujos estándar apuntan a un lugar donde muestran su contenido,
sin embargo podemos desviar el lugar a donde apuntan estos flujos estándar con la
terminal, de esta manera:

```bash
echo "Hola soy una linea de texto" > archivo.txt # Desvía el resultado a un archivo de texto, si ya existe lo sobre-escribe
echo "Hola soy una linea de texto sobre otra" >> archivo.txt # Igual que el anterior, peri si existe lo agrega al final
echo < archivo.txt # Envía como entrada al comando el texto del archivo
```

También podemos en lugar de enviar y leer archivos, desviar los flujos estándar a
otros procesos utilizando los pipes '|':

```bash
cat archivo.txt | head -n 15 | grep -EP "texto" # Esto envía la salida del primer comando a la entrada del segundo y de ahi al tercer comando
```

## Procesos

Cuando tenemos que ejecutar comandos que tardan mucho tiempo en ejecución es util
poder ejecutarlos en segundo plano mientras seguimos ejecutando otros, esto lo
podemos hacer de la siguiente manera:

```bash
[COMANDO] & # El símbolo '&' después del comando indica que sera ejecutado en segundo plano
```

También podemos pausar un comando con las teclas ctrl + Z, y el comando 'fg' para
recuperar la ejecución posteriormente.

Para administrar procesos utilizamos los comandos:

```bash
ps
top # Nos permite ver los procesos en ejecución
htop # Alternativa a top

kill [ID PROCESO]
killall [NOMBRE PROCESO] # Nos permiten finalizar un proceso

kill -9 [ID PROCESO]
killall -9 [NOMBRE PROCESO] # Nos permiten finalizar forzosamente un proceso
```

## Operaciones remotas

## Automatización y scripts

...
