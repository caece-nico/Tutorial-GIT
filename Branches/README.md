Este tema tiene un índice a parte por la complejidad  del mismo.

1. [Introduccion a Branches](#introduccion-a-branches)
2. [Ramas](#2.-ramas)
    * [Introduccion Ramas](#Introduccion-git-diff)
    * [Hard Reset](#hard-reset)
    * [TAGS](#tags)
    * [Desplazamiento por ramas](#deplazamiento-por-ramas)
    * [Ramas BRANCH y SWITCH](#ramas-branch-y-switch)


## 1. Introduccion a Branches

## 2. RAMAS

### Introduccion GIT DIFF

Aveces puede ocurrir que estamos trabajando en un fichero y no estamos seguros si lo que estamos por agregar al stage es correcto o no. Y antes de hacer el commit queremos ver el cambio con respecto a la versión original. Para esto existe el comando __git diff__

Para poder trabajar con el git diff no debemos tener el último cambio en el stage. (SIN GIT ADD)

* Hacemos un cambio en el fichero helloWorld.py

```bach
git diff
```
![git diff](img/git_diff_status.png)

Vemos la versión anterior y la nueva en verde. Este cambio aún no ha sido confirmado en el __stage__

__¿Qué pasaria si queremos movernos a otro commit anterior sin antes haber guardado este utimo cambio?

Al hacer un checkout veriamos esto.

![checkout](img/checkout_problema.png)

DOnde se ve que nos pide que antes commitemos el cambio en el fichero helloWorld.py


**SOLUCION**

1. Hacemos un git checkout al fichero helloWorld.py para dejarlo como estaba antes.

__Elmina el cambio en el mensaje__

2. Ahora queremos volver al commit donde solo teniamos el fichero helloWorld.py

```bash
git checkout c84cb60b702e0afce4d51f9e150ff6b27090d273
```

Ahora el HEAD se mueve al commit incial y elimina el archivo hellogit2 que habiamos creado.

![](img/checkout_final.png)


```bash
git checkout HEAD
```

__¿Cómo deshacemos esto?__

desde git tree veo todos los commits.

```bash
 git checkout 2e25d5a
```
Este es el ultimo commit donde tenia todos los archivos, si lo ejecuto vuelvo a tener todo como estaba antes.

### Hard Reset

Nos permite elminar commits y volver a un punto en el tiempo especifico.

Ejemplo.

Hoy estamos áca, tenemos tres commits y la cabecera está al final.

![](img/hard_reset.png)

Sabemos que todo lo que hicimos en los dos ultimos commits está mal y solo queremos tener el primero.

```bash
git reset --hard c84cb60
```
Cambia la cabecera

![](img/after_hard_reset.png)

Pero ahroa me doy cuenta que el commit del medio lo necesitaba. __¿Cómo lo recupero?__

```bash
git reflog
git checkout 8b98dae
```

### TAGS

Siginfica etiquetar un commit. Esto se utiliza cuando estamos haciendo referencias a que son puntos importantes. Generalmente son las versiones.

```
Todo lo que subí hasta este punto es la version 1.1
```

![](img/git_tag.png)

Ahora mi punto en el tiempo está en mi __git tag__

* Si agregamos un nuevo fichero y le hacemos commit, el head y el main se mueven pero el tag se ha quedado en el pasado.

![](img/after_git_commit_tag.png)

Puedo ver todos mis tags.

```bash
git tag
```

Vuelvo a un punto concreto, hago lo que tengo que hacer y luego vuelvo a lo nuevo.

```bash
git checkout clase_1
```

### deplazamiento por ramas

En el ejemplo anterior siempre nos movimos en la rama __main__ 

Ahora recuperamos el archivo hellogit2.py

![](img/afterhard_reset_checkout.png)

Ahora la cabeza y el main no apuntan al mismo lugar,
Para solucionar esto volvemos a hacer un get reset al mismo has.

![](img/after_hard_reselt_main.png)


## Ramas BRANCH y SWITCH

```
Una rama es un concepto que necesitamos crear algo que no tiene sentido trabajarlo en la rama main.
Quiero empezar en una funcionalidad que no se cuendo la voy a terminar y cuando la haya terminado veo comola integro en la __main__
```

```bash
git branch login
```

Esto me crea una rama llamada login pero sigo en la rama __main__, lo se porque es done apunta el main.

```bash
git switch login
```

Ahora estamos en otra rama u otro flujo. El HEAD -> login

![](img/branch_loging.png) 

Creamos un nuevo archivo en esta rama. Este archivo solo estará disponible en loging pero no en la master.