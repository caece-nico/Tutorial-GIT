# Tutorial-GIT

1. [Tutorial de GIT](#tutorial-de-git)
    * [Git vs GitHub](#git-vs-github)
    * [Instalacion de Git](#instalacion-de-git)
    * [Comandos principales](#comandos-principales)
    * [Configurar GIT](#configurar-git)
2. [Control de versiones](#control-de-versiones)
    * [Inicializacion de un directorio](#inicializacion-de-un-directorio)
    * [Ramas en GIT](#ramas-en-git)
    * [Commit y Status](#commit-y-status)
    * [Validar commit](#validar-commits)



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


## Control de versiones

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

