# Curso Profesional de Git y GitHub

- [Curso Profesional de Git y GitHub](#curso-profesional-de-git-y-github)
  - [Conceptos básicos](#conceptos-básicos)
  - [Comandos](#comandos)
    - [Comandos básicos](#comandos-básicos)
    - [Configurar git](#configurar-git)
    - [Operaciones entre working, stage y repository](#operaciones-entre-working-stage-y-repository)
    - [Diferencias entre rm y reset](#diferencias-entre-rm-y-reset)
    - [Analizar archivos y cambios en git](#analizar-archivos-y-cambios-en-git)
    - [Desplazarse entre versiones del proyecto o de un archivo](#desplazarse-entre-versiones-del-proyecto-o-de-un-archivo)
  - [Las ramas](#las-ramas)
    - [Que son las ramas](#que-son-las-ramas)
    - [Crear una rama](#crear-una-rama)
    - [Fusionar una rama](#fusionar-una-rama)
  - [Repositorios remotos](#repositorios-remotos)

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

Para modificar el 'working directory' simplemente realizamos las operaciones
habituales sobre los archivos, es decir copiar, mover, eliminar y editar archivos.

Para realizar operaciones sobre el Staging Area tenemos los comandos:

```bash
git add [ARCHIVO] # Añadir un archivo al stage
git rm --cached [ARCHIVO] # Sacar un archivo de stage sin borrar el working directory
git reset [ARCHIVO] HEAD # Sacar un archivo del stage sin marcar ninguna operación de borrado

git rm --force [ARCHIVO] # Eliminar un archivo de staging y del disco duro
git rm --cached [ARCHIVO]
rm [ARCHIVO] # Equivalente a git rm --force
```

Una vez tenemos nuestro staging area listo podemos realizar operaciones al
repositorio con los comandos:

```bash
git commit -m [MENSAJE] # Para enviar stage al repositorio
git reset --soft # Regresar a un commit anterior pero mantener el stage

git reset --mixed # Regresar a un commit anterior, limpiar el stage, pero mantener el working directory
git reset # Ambas son equivalentes

git reset --hard # Regresar a un commit anterior, limpiar el stage, y borrar el working directory
```

### Diferencias entre rm y reset

La operación 'reset' simplemente deshace los cambios en los lugares que
corresponda según las opciones que se le pasen, a diferencia de 'rm' que registra
la operación de borrado en la base de datos.

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

También podemos crear nuestro propio comando de 'log' personalizado usando:

```bash
git config --global alias.superlog "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"

git superlog # Ejecutamos el nuevo comando que acabamos de definir
```

### Desplazarse entre versiones del proyecto o de un archivo

Con git podemos desplazarnos entre las distintas versiones de un archivo o de
todo el repositorio, estos comandos son:

```bash
git checkout [COMMIT] [ARCHIVO] # Este comando permite traer un archivo de una versión anterior
git checkout [COMMIT] # Este comando trae todo el proyecto a una versión anterior, mueve el apuntador HEAD
```

## Las ramas

### Que son las ramas

Las ramas de git son historiales de commit de un repositorio, pueden existir
ramas paralelas es decir historias de archivos que evolucionen de manera
independiente y posteriormente realizar fusiones entre ellas.

### Crear una rama

Cuando creamos una rama creamos una copia del commit y sobre esa copia realizamos
cambios de manera independiente al original, para crear una rama debemos
ubicarnos en la rama y el commit desde el cual queremos bifurcar la nueva rama,
y ejecutamos el comando:

```bash
git branch [NOMBRE DE LA RAMA] # Crea la rama
git checkout [NOMBRE DE LA RAMA] # Mueve HEAD a la nueva rama
```

Cuando nos movemos entre ramas lo que sucede es que HEAD apunta a un commit que
se encuentra en otra rama, por defecto se mueve al commit mas reciente que exista.

Es importante notar que el comando 'checkout' mueve el apuntador HEAD y por lo
tanto el directorio de trabajo a otro commit, debido a esto si realizamos un
checkout y tenemos cambios que no han sido registrados, perderemos estos cambios,
debido a esto checkout nos informara cuando sea ese el caso y nos pedirá que
enviemos un commit con los cambios al repositorio.

Para ver las ramas que existen dentro del proyecto usamos:

```bash
git branch
```

### Fusionar una rama

Si tenemos 2 ramas, podemos hacer que los archivos sean modificados de manera
independiente en cada una de ellas, sin embargo normalmente las ramas se utilizan
con el fin de fusionar los cambios en un futuro, para realizar esta operación
debo colocarme en la rama que recibirá los cambios y luego realizar la fusión,
esto se hace de la siguiente manera:

```bash
git checkout master # Esto me mueve a la rama master para que master reciba los cambios
git merge [OTRA RAMA] # Trae los cambios de la otra rama
```

Cuando realizamos la fusión se crea un commit nuevo en la rama que recibe los
cambios, en ese caso 'master' y luego en ese commit combina los cambios de la
otra rama con la rama actual.

## Repositorios remotos

Un repositorio remoto permite que varias personas trabajen en un mismo proyecto
y que compartan su histórico de cambios, cada dispositivo mantiene una copia
local exacta del repositorio remoto.

Para empezar a utilizar los repositorios remotos tenemos varias opciones, por
ejemplo para empezar a trabajar con un repositorio ya existente utilizamos:

```bash
git clone [URL]
```

Una vez que tenemos nuestra copia local del repositorio podemos trabajar sobre
el, enviar commit, y sincronizar nuestros cambios con la base de datos en remoto,
esto se hace de la siguiente manera:

```bash
git push
```

También podemos traer cambios del repositorio remoto al repositorio local, esto
se hace de esta manera:

```bash
git fetch # Trae los datos del repositorio remoto al repositorio local
git merge # Trae los datos del repositorio local al directorio de trabajo

git pull # Esto ejecuta fetch y pull en la misma operación
```
