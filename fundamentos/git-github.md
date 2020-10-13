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
    - [Guardar cambios temporalmente con git stash](#guardar-cambios-temporalmente-con-git-stash)
    - [Traer commit específicos con cherry-pick](#traer-commit-específicos-con-cherry-pick)
    - [Buscar en los commit y archivo con git grep y git blame](#buscar-en-los-commit-y-archivo-con-git-grep-y-git-blame)
  - [Las ramas](#las-ramas)
    - [Que son las ramas](#que-son-las-ramas)
    - [Crear una rama](#crear-una-rama)
    - [Fusionar una rama](#fusionar-una-rama)
    - [Reorganizando el trabajo con git rebase](#reorganizando-el-trabajo-con-git-rebase)
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

Si queremos que git no rastree algún tipo de archivo podemos indicarlo en un
archivo llamado '.gitignore', por ejemplo:

```gitignore
.env
.venv
env/
venv/
ENV/
```

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

Limpiar directorio del proyecto de archivos no deseados

```bash
git clean --dry-run # Muestra los archivos que serán borrados pero no ejecuta el borrado
git clean -f # Borra los archivos
git clean -df # Borra los archivos incluyendo los directorios
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
git commit -am [MENSAJE] # Realiza un add y un commit en la misma instrucción

git reset --soft # Regresar a un commit anterior pero mantener el stage

git reset --mixed # Regresar a un commit anterior, limpiar el stage, pero mantener el working directory
git reset # Ambas son equivalentes

git reset --hard # Regresar a un commit anterior, limpiar el stage, y borrar el working directory
```

Si queremos reconstruir un commit que ya fue registrado podemos usar 'amend', sin
embargo esto no debe usarse para commit que ya están en remoto, unicamente para
realizar correcciones en local, para hacer un 'amend' hacemos:

```bash
git add . # Añadimos los cambios que queremos agregar
git commit --amend # Aplicamos los cambios al ultimo commit enviado
git commit --amend --no-edit # Aplicamos los cambios al ultimo commit pero no cambia el mensaje del commit
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

### Guardar cambios temporalmente con git stash

Cuando tenemos cambios que aun no están registrados en un commit y deseamos
movernos a otra rama o a otro commit, git nos devolverá un error, esto es porque
cuando cambiamos a otra rama o commit, movemos nuestro HEAD y por lo tanto
nuestro directorio de trabajo, por lo que perderíamos nuestros cambios, para
solucionar esto podemos guardar nuestros cambios de manera temporal con una
herramienta de git llamada 'stash', de esta forma:

```bash
git stash # Guarda de manera temporal los cambios que tengo y regresa el directorio al ultimo commit
git stash pop # Aplica los cambios del ultimo stash que estaban almacenados y lo borra de los stash
git stash list # Nos permite ver los stash creados
git stash branch [NOMBRE RAMA] # Crea una rama a partir del ultimo stash creado
git stash drop # Elimina el ultimo stash sin aplicarlo
git stash clear # Borra todos los stash
```

### Traer commit específicos con cherry-pick

Con git podemos traer commit específicos de otras ramas o commit antiguos de la
misma rama a el final de la rama actual, esto se hace con la herramienta
'cherry-pick', sin embargo esto es una mala practica dado que esto re-escribe la
historia del proyecto, por lo que es mejor utilizar 'checkout' o 'merge' para
realizar estas operaciones, 'cherry-pick' se usa de esta manera:

```bash
git checkout [RAMA] # Nos ubicamos en la rama que recibirá el commit
git cherry-pick [COMMIT] # Traemos el commit a la rama actual
git commit # Solo en caso de que existan conflictos, resolverlos
```

### Buscar en los commit y archivo con git grep y git blame

Si necesitamos buscar cuantas veces aparece una palabra, quien modifico una linea
y en que archivo, utilizaremos los comandos:

```bash
git grep [regex] # Busca en que archivos aparecen lineas que coinciden con la expresión regular
git grep -n [regex] # Muestra en que lineas coincide la expresión regular
git grep -c [regex] # Muestra cuantas veces coincide una expresión regular

git blame -c [ARCHIVO] # Muestra quien ha modificado cada linea de un archivo
git blame -c [ARCHIVO] -L[inicio],[fin]# Muestra quien ha modificado cada linea de un archivo desde la linea inicio hasta fin
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

git branch -D [NOMBRE DE LA RAMA] # Elimina la rama
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
git branch # Muestra las ramas que existen
git show-branch --all # Muestra las ramas que existen y cual a sido su historial
git branch -a # Muestra todas las ramas incluyendo las remotas
git branch -r # Muestra solo las ramas remotas
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

Durante la fusión puede darse el caso que una misma linea en un archivo haya sido
modificada en las 2 ramas, esto se llama un conflicto, cuando tengamos un
conflicto, 'git merge' nos informara de la siguiente manera:

```text
Auto-fusionando [ARCHIVO]
CONFLICTO (contenido): Conflicto de fusión en [ARCHIVO]
Fusión automática falló; arregle los conflictos y luego realice un commit con el resultado.
```

Si abrimos el archivo veremos algo como esto:

```text
<<<<<< HEAD
hola mundo, soy una buena linea
======
hola mundo, soy la primera linea
>>>>>> test_1
```

La linea que esta después de HEAD y antes de los símbolos '=' corresponde al
estado del archivo de la rama que recibe el merge, y la linea que esta después de
los símbolos '=' corresponde al estado del archivo en la rama de la que estamos
recibiendo el merge. Para resolver el conflicto simplemente borramos las lineas
que no queramos en el archivo, incluyendo los símbolos del conflicto y enviamos
un commit con los conflictos resueltos.

### Reorganizando el trabajo con git rebase

La función rebase de git re-organiza el orden de los commit entre las ramas, esta
función mueve toda una rama al ultimo commit de otra, es decir cambia el punto de
inicio de una rama en el historial, esto es una mala practica ya que se pierde la
organización del registro de cambios y solo debe usarse de manera local, nunca en
el repositorio remoto, se usa de la siguiente manera:

```bash
git checkout feature # Nos movemos a la rama que queremos mover
git rebase master # Mueve el inicio de la rama feature al final de la rama master
# Resolvemos conflictos
git rebase feature # Actualiza el apuntador HEAD de master al nuevo final
```

## Repositorios remotos

Un repositorio remoto permite que varias personas trabajen en un mismo proyecto
y que compartan su histórico de cambios, cada dispositivo mantiene una copia
local exacta del repositorio remoto.

Para empezar a utilizar los repositorios remotos tenemos varias opciones, por
ejemplo para empezar a trabajar con un repositorio ya existente utilizamos:

```bash
git clone [URL] # Descarga un repositorio de internet y lo enlaza
git remote add origin [URL] # Hace que nuestro repositorio local apunte a una nueva dirección remota
```

Una vez que tenemos nuestra copia local del repositorio podemos trabajar sobre
el, enviar commit, y sincronizar nuestros cambios con la base de datos en remoto,
esto se hace de la siguiente manera:

```bash
git push # Por defecto git push origin master
git push origin [rama] # Envía a una rama remota distinta de master
git push origin  -f # Obliga a enviar los cambios incluyendo las operaciones de borrar commit
```

También podemos traer cambios del repositorio remoto al repositorio local, esto
se hace de esta manera:

```bash
git fetch # Trae los datos del repositorio remoto al repositorio local
git merge # Trae los datos del repositorio local al directorio de trabajo

git pull # Esto ejecuta fetch y pull en la misma operación
git pull origin [rama] # Trae los datos de una rama remota especifica
git pull origin master --allow-unrelated-histories # Permite traer un historial no relacionados a mi repositorio local
```

Es una buena practica antes de enviar cualquier cambio con 'push' al repositorio
remoto, traer cualquier cambio que pudo haber ocurrido con 'pull'.

Si queremos ver las URL a las que apunta los push y fetch de nuestro repositorio
local podemos utilizar el comando:

```bash
git remote -v
```

Podemos modificar la URL a la que un repositorio apunta con el comando:

```bash
git remote set-url origin [URL]
```

Dentro de los repositorios remotos podemos marcar ciertos commit con una etiqueta,
por ejemplo para identificar versiones, para hacer esto usamos el comando:

```bash
git tag -a [NOMBRE TAG] -m [DESC. TAG] [COMMIT] # Crea un tag nuevo en COMMIT
git show-ref --tags # Muestra todos los tags
git push origin --tags # Envía los tags al repositorio remoto

git tag -d [NOMBRE TAG] # Elimina el tag
git push origin :refs/tags/[NOMBRE TAG] # Elimina la referencia a ese tag en el repositorio remoto
```
