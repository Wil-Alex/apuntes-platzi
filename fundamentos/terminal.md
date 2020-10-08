# Curso de introducción a la terminal y linea de comandos

- [Curso de introducción a la terminal y linea de comandos](#curso-de-introducción-a-la-terminal-y-linea-de-comandos)
  - [Que es y para que sirve la terminal](#que-es-y-para-que-sirve-la-terminal)
  - [Comandos básicos](#comandos-básicos)
  - [Sistema de archivos](#sistema-de-archivos)
    - [Estructura del sistema de archivos](#estructura-del-sistema-de-archivos)
    - [Punteros dentro del sistema de archivos](#punteros-dentro-del-sistema-de-archivos)
    - [Comandos para ejecutar operaciones en el sistema de archivos](#comandos-para-ejecutar-operaciones-en-el-sistema-de-archivos)
    - [Variaciones del comando 'ls'](#variaciones-del-comando-ls)
    - [Permisos](#permisos)
    - [Buscar](#buscar)
    - [Empaquetar y comprimir](#empaquetar-y-comprimir)
  - [Manejo de texto en la terminal](#manejo-de-texto-en-la-terminal)
  - [Procesos](#procesos)
  - [Variables de entorno](#variables-de-entorno)
  - [Operaciones remotas](#operaciones-remotas)
  - [Automatización y scripts](#automatización-y-scripts)

## Que es y para que sirve la terminal

La terminal es el medio por el cual el sistema operativo recibe instrucciones de
parte del usuario y las traduce a instrucciones que pueden ser interpretadas por
la computadora.

Utilizar la terminal nos permite realizar operaciones de manera mas eficiente que
por medio de una interfaz gráfica y a su vez nos permite automatizar tareas
largas y complejas.

## Comandos básicos

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

...

### Buscar

...

### Empaquetar y comprimir

...

## Manejo de texto en la terminal

...

## Procesos

...

## Variables de entorno

...

## Operaciones remotas

...

## Automatización y scripts

...
