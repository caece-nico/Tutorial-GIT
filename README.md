# Tutorial-GIT

1. [Tutorial de GIT](#1.-tutorial-de-git)
    * [Git vs GitHub](#git-vs-github)
    * [Instalacion de Git](#instalacion-de-git)
    * [Comandos principales](#comandos-principales)
    * [Configurar GIT](#configurar-git)
2. [Control de versiones](#2.-control-de-versiones)
    * [Inicializacion de un directorio](#inicializacion-de-un-directorio)
    * [Ramas en GIT](#ramas-en-git)
    * [Commit y Status](#commit-y-status)
    * [Validar commit](#validar-commits)
    * [Agregamos un segundo fichero](#agregamos-un-segundo-fichero)
    * [Git checkout y Reset](#git-checkout-y-reset)
3. [Ramas](#3.-ramas)
    * [Introduccion Ramas](#Introduccion-git-diff)
    * [Desplazamiento por ramas](#deplazamiento-por-ramoas)
4. [GIT Alias](#4.-git-alias)
5. [GIT Ignore](#5.-git-ignore)



## 1. Tutorial de git

**IMPORTANTE** Con git podemos trabajar desde la terminal o desde [herramientas gráficas](https://git-scm.com/download/gui/windows).

### Git VS GitHub

![wwww.git.org](/img/pic_git.png)

```
Es un sistema de control de versiones distribuido, no depende de un único sitio.
Cada participante de un proyecto podria tener una copia del código siempre disponible.
El control de versioens nos permite llevar un historial de todos los cambios que se han hecho en un proyecto.
Existe una linea de tiempo donde se van guardando diferentes fotografias a las que podemos volver y ver que ha pasado.
```

## Instalacion de Git

__Puede venir una versión no actualizada con el Sistema Operativo__ pero se puede actualizar.

**En windows**

1. Descargamos el archivo desde [windows git](https://git-scm.com/download/win)

2. Una vez instalado ejecutamos el comando desde la terminal.

```bash
git --version
```

![git-install](/img/git_install.png)

## Comandos principales

|comando|descripcion|
|--------|-----------|
|git --help| Muestra los principales comandos de git|
|ls| Nos desplazamos por los ficheros del S.O|
|pwd| Donde estoy ubicado|
|mkdrir|creamos un directorio en la ubicación en la quee estemos|

## Configurar GIT

```
Lo primero que necesitamos hacer crar un mail y un nombre de usuario.
```

__El archivo de configuracion se encuentra en :
c:/usuario/miUser/.gitconfig__ Si existe lo borramos.

En la terminal escribimos.

```bash
git config --global user.name "NicoUdin" 
git config --global user.email "xxxxx@xxx.com
```

Esto deberia actualizar el fichero anterior.


## 2. Control de versiones

## Inicializacion de un directorio

__Para comenzar a trabajar con git y el control de versiones neceitamos inicializar el directorio creado previamente__

1. Nos posicionamos con la terminal en la carpeta creada y ponemos:

```bash
git init
```

Esto inicializa el directorio y crea una carpeta .git  oculta que indica que es un repositorio de git.

![inicializa directorio](/img/init_git.png)

**IMPORTANTE** Notar que apenas creamos un repo nuevo, estamos trabajando en la __master__

## Ramas en GIT

```
Un repositorio se crea en una rama __master__ pero raramente trabajaremos sobre esta master.
Se deben crear distintas ramas o flujos de trabajo que iran sufriendo cambios.
```

**Nota** Otra forma mas moderna de llamar a la rama master es main.

__¿Cómo cambio el nombre a la rama principal del proyecto?__

```bash
git branch -m main
```

![renombrar a rama main](/img/branch_main.png)

## Commit y Status

Tres comandos importantes de GIT son 

|comando|descripcion|
|-------|-----------|
|status|Para ver que cambios hubo en el repositorio, muestra lo que no está trackeado|
|add|Para agregar esos cambios al stash y poder seguirlos, es la base del versionado|
|commit|Para confirmar los cambios|
|checkout|Para situarnos en un punto concreto de un ficheto que no fue commiteado|
|reset|Para volver a una foto anterior|
|git diff|Muestra diferencias entre commits|


### Git STATUS

Lo usamos para hacer un track de los cambios.

![git status](/img/git_status.png)

Nos indica que el archivo helloworld.py tuvo algún cambio pero no los tiene guardados, esto quiere decir que __NO TIENE UNA FOTOGRAFIA DE ELLOS__ porque están local en nuestra máquina.
Acá entra otro comando importante el **GIT ADD**.


### GIT ADD

Lo usamos para crear la fotografia de lo que no estamos versionando. Lo usamos para poder seguir los cambios en el código.

__Siguiendo el ejemplo anterior__

```bash
git add helloworld.py
```

si volvemos a hacer un git status vemos lo siguiente

![git status](/img/git_status_add.png)

Indica que aún no hay commit pero detectó algo que está en el stage.
Paso siguiente creamos una fotografia con un **GIT COMMIT**


### GIT COMMIT

Para crear una fotografia hacemos un 

```bash
git commit -m "mensaje"
```

sobre los que tenemos en el stage.


![primer commit](/img/primer_commit.png)

**IMPORTANTE** Para poder hacer un commit siempre debemos poner un comentario.

__Al hacer un commit nos devuelve un valor de hash, en este casoc84cb60, pero es útil para el seguimiento de ese commit__


## Validar commits

Para validar si un __commit__ se hizo de forma correcta usamos el comando __log__

```bash
git log
```

![primer log commit](/img/git_log_primer_commit.png)

Vemos los datos asociados al commit, con nombre de usuario, fecha, **hash** y el mensaje.

## Agregamos un segundo fichero

Hasta ahora tenemos en la __master__ o __main__ una sola fortografia, del archivo __helloworld.py__

Hacemos

```
git status
git add hellogit2.py
git commit "Se agrega nuevo hellogit2.py"
```

Ahora tenemos dos fotos de nuestra __master__

![Segundo commit](/img/git_segundo_commit_log.png)

En un diagrama se veria

![Estado actual](/img/estado_actual_git_master.png)

## Git CHECKOUT y RESET

### GIT CHECKOUT

Si queremos volver para atras a un cambio que aun no fué comiteado usamos cheackout.

Ejemplo.

Al fichero __hellogit2.py__ le agregamos unas lineas de codigo pero no le hacemos **add** ni **commit**.

```bash
git status
```
Ahora vemos que ya no tenemos un archivo nuevo, sinó que __git status__ indica que el archivo está en estado __modified__

![git status 2](/img/git_modified_file.png)

**Pero por algun motivo no queremos estos cambios, entonces hacemos un git checkout __FILE__ para revertirlo**


```bash
git checkout hellogit2.py
```
El resultado es, volvimos a la versión anterior del archivo, que estaba en el último commit. (Ultima fotografia de la rama)

![git checkout](/img/git_checkout.png)

### GIT RESET

???

## 3. RAMAS

### Introduccion GIT DIFF

Aveces puede ocurrir que estamos trabajando en un fichero y no estamos seguros si lo que estamos por agregar al stage es correcto o no. Y antes de hacer el commit queremos ver el cambio con respecto a la versión original. Para esto existe el comando __git diff__

Para poder trabajar con el git diff no debemos tener el último cambio en el stage. (SIN GIT ADD)

* Hacemos un cambio en el fichero helloWorld.py

```bach
git diff
```
![git diff](/img/git_diff_status.png)

Vemos la versión anterior y la nueva en verde. Este cambio aún no ha sido confirmado en el __stage__

__¿Qué pasaria si queremos movernos a otro commit anterior sin antes haber guardado este utimo cambio?

Al hacer un checkout veriamos esto.

![checkout](/img/checkout_problema.png)

DOnde se ve que nos pide que antes commitemos el cambio en el fichero helloWorld.py


**SOLUCION**

1. Hacemos un git checkout al fichero helloWorld.py para dejarlo como estaba antes.

__Elmina el cambio en el mensaje__

2. Ahora queremos volver al commit donde solo teniamos el fichero helloWorld.py

```bash
git checkout c84cb60b702e0afce4d51f9e150ff6b27090d273
```

Ahora el HEAD se mueve al commit incial y elimina el archivo hellogit2 que habiamos creado.

![](/img/checkout_final.png)


```bash
git checkout HEAD
```

__¿Cómo deshacemos esto?__

desde git tree veo todos los commits.

```bash
 git checkout 2e25d5a
```
Este es el ultimo commit donde tenia todos los archivos, si lo ejecuto vuelvo a tener todo como estaba antes.


### deplazamiento por ramas

En el ejemplo anterior siempre nos movimos en la rama __main__ 

## 4. GIT alias

Los alias sirven para guardar comando dentro del archivo de configuraciones y no tener que escribir mucho código.

```git
git config --global alias.tree "log --graph --decorate --all --oneline"
```

**tree** es el nombre que le doy al alias.

__¿Cómo lo uso?__

```bash
git tree
```

![](/img/git_tree_log.png)


## 5. GIT Ignore

Se un fichero que se coloca en el directorio del repositorio que indica lo que no queremos que se suba al commit.

### Comandos

|comando|descripcion|
|-------|-----------|
|**/xxx| Con ** lo que hacemos es ignorar todo archivo con el nombre xxx en cualquier carpeta|
|/xx|Ignora el archivo xxx|
