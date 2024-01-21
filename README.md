# Tutorial-GIT

1. [Tutorial de GIT](#Tutorial-de-git)
    * [Git vs GitHub](#git-vs-github)
    * [Instalacion de Git](#instalacion-de-git)
    * [Comandos principales](#comandos-principales)
    * [Configurar GIT](#configurar-git)



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