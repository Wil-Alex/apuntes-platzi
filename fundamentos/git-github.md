# Curso Profesional de Git y GitHub

- [Curso Profesional de Git y GitHub](#curso-profesional-de-git-y-github)
  - [Conceptos básicos](#conceptos-básicos)
  - [Comandos](#comandos)
    - [Comandos básicos](#comandos-básicos)
    - [Configurar git](#configurar-git)
    - [Operaciones entre working, stage y repository](#operaciones-entre-working-stage-y-repository)
      - [Modificar el working directory](#modificar-el-working-directory)
      - [Staging area](#staging-area)
      - [Repository](#repository)
    - [Analizar archivos y cambios en git](#analizar-archivos-y-cambios-en-git)
    - [Desplazarse entre versiones del proyecto o de un archivo](#desplazarse-entre-versiones-del-proyecto-o-de-un-archivo)
  - [Las ramas](#las-ramas)
  - [Notas](#notas)
    - [Diferencias entre rm y reset](#diferencias-entre-rm-y-reset)

## Conceptos básicos

El 'working directory' o directorio de trabajo es el directorio que se encuentra
en disco duro, es sobre este donde se hacen los cambios en primera instancia.

El 'staging area' o area de preparación es una zona en memoria RAM, en la cual se
van preparando los cambios que serán enviados al repositorio.

Un commit es una instantánea del estado de staging en ese momento, la cual es
enviada al repositorio, es decir cada commit conserva el estado y las operaciones
realizadas en staging en un momento especifico.

El 'git repository' es el repositorio de git y es aquí donde se almacena el
historial de archivos, es decir los commit, esto nos permite regresar a versiones
anteriores de nuestro proyecto.

El apuntador HEAD marca el estado de los archivos en disco actualmente, es decir
apunta al commit en el que nos encontramos actualmente.

## Comandos

### Comandos básicos

Iniciar un repositorio de git:

```bash
git init
```

Ver el estado del repositorio:

```bash
git status
```

Para mover o renombrar archivos es recomendable usar:

```bash
git mv [ANTIGUO] [NUEVO] # Esto registra la operación para evitar conflictos
```

### Configurar git

```bash
git config --global user.name [TU NOMBRE REAL] # Es recomendable no usar el nickname
git config --global user.email [TU CORREO] # Recomendable que sea el mismo que tienes en github
```

### Operaciones entre working, stage y repository

#### Modificar el working directory

Para modificar el 'working directory' simplemente realizamos las operaciones
habituales sobre los archivos, es decir copiar, mover, eliminar y editar archivos.

#### Staging area

Añadir un archivo al stage:

```bash
git add [ARCHIVO]
```

Sacar un archivo de stage sin borrar los cambios del disco duro:

```bash
git rm --cached [ARCHIVO]
```

Sacar un archivo del stage sin marcar ninguna operación de borrado:

```
git reset [ARCHIVO] HEAD
```

Eliminar un archivo de staging y del disco duro:

```bash
git rm --force [ARCHIVO]

git rm --cached [ARCHIVO]
rm [ARCHIVO] # Ambas operaciones son equivalentes
```

#### Repository

Para enviar stage al repositorio:

```bash
git commit -m [MENSAJE]
```

Regresar a un commit anterior pero mantener el stage:

```bash
git reset --soft
```

Regresar a un commit anterior, limpiar el stage, pero mantener los cambios en el
disco duro:

```bash
git reset --mixed # Esta es la opción por defecto
git reset # Ambas son equivalentes
```

Regresar a un commit anterior, limpiar el stage, y eliminar los cambios del disco:

```bash
git reset --hard
```

### Analizar archivos y cambios en git

Git almacena todos los cambios que se realizan sobre un proyecto, por lo que
también proporciona herramientas para analizar los cambios que se realizan dentro
del mismo, podemos ver el historial general de cambios o podemos analizar
archivos individuales, los comandos de los que disponemos son:

```bash
git show [ARCHIVO] # Muestra los 2 últimos commit y los cambios entre ellos
git log # Muestra todo el historial de cambios del repositorio
git log [ARCHIVO] # Muestra el historial de cambios sobre un archivo especifico.
git diff [ANTIGUO] [NUEVO] # Muestra todos los cambios entre los 2 commit, es importante el orden
git log --stat # El modificador 'stat' muestra información mas detallada de los cambios
```

### Desplazarse entre versiones del proyecto o de un archivo

Con git podemos desplazarnos entre las distintas versiones de un archivo o de
todo el repositorio, estos comandos son:

```bash
git checkout [COMMIT] [ARCHIVO] # Este comando permite traer un archivo de una versión anterior
git checkout [COMMIT] # Este comando trae todo el proyecto a una versión anterior, mueve el apuntador HEAD
```

## Las ramas

Las ramas de git son historiales de commit de un repositorio, pueden existir
ramas paralelas es decir historias de archivos que evolucionen de manera
independiente y posteriormente realizar fusiones entre ellas.

## Notas

### Diferencias entre rm y reset

La operación 'reset' simplemente deshace los cambios en los lugares que
corresponda según las opciones que se le pasen, a diferencia de 'rm' que registra
la operación de borrado en la base de datos.