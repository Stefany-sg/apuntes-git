# Curso Git y Github 2025
## Qué es markdown?   ![](imagenes/markdown.png)

Lenguaje de marcado ligero y sencillo que permite dar estilo a un texto sin usar html.
# Clase 1
## Introduccion a Git
### Que es un control de versiones?
Sistema de registro de cambios en el codigo fuente de un proyecto. Permite tener un historico de cambios y quien los hizo
>Ej. Un checkpoint de un juego

#### Importancia:                
- Rendimiento, solo se guarda lo necesario (solo copia cambios)
- Seguridad, conserva toda acción (cambios y quienes lo hicieron)
- SSH -> Firma digital que permite verificar la identidad
- Flexibilidad, no es necesario un desarrollo lineal. Se pueden hacer cambios "paralelos" en equipo
### Que es Git?
Es una herramienta de control de versiones. Al  ser un sistema distribuido aloja una copia del repositorio en cada maquina local y se puede tener uno o varios repositorios remotos.

Nos permite trabajar colaborativamente
### Que es un repositorio?
Carpeta donde se almacenan ficheros de un proyecto. En el repositorio hay notas que indican el cambio realizado
Pueden ser locales (nuestro ordenador) o remotos (servidor externo)
#### Repositorio remoto
Los repositorios remotos son versiones de tu proyecto que están hospedadas en Internet o en cualquier otra red. Puedes tener varios de ellos, y en cada uno tendrás generalmente permisos de solo lectura o de lectura y escritura.
[Fundamentos de git](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Trabajar-con-Remotos)

> **Nota:**
>Git es sensible a los cambios de salto de linea diferentes entre linux y windows ya que los detecta como modificaciones al momento de hacer un commit (LF y CRLF)
Se debe configurar correctamente


### Iniciar un proyecto en Git
Inicializa un repositorio de git vacio en la ruta en la que estás y crea una carpeta .git

```
$ git init nombre-proyecto
$ cd nombre-proyecto
```

Alternativa:

```
$ git init nombre-proyecto --initial-branch=main
```

# Clase 2
## States y commits
- ### Modified
    Cuando un archivo se crea, elimina o tiene cambios no confirmados
- ### Staged
    Área temporal transitoria : Archivo marcado listo para ser confirmado en el repositorio local. En esta area de **staged** van todos los archivos que queremos agregar nuestro commit.

    - Identifica los archivos modificados

        ![](imagenes/gitStatus1.png) 

    - Despues de un `git add <archivos>` los archivos especificados pasan al estado staged

        ![](imagenes/gitStatus2.png)
    
- ### Commited
    Los cambios son confirmados y grabados en el repositorio.

## Qué es un commit?
>Ej. Checkpoint de un videojuego

Es como un punto de restauracion, guarda el avance en un determinado punto de tiempo. Muestra los archivos en el momento que se hizo fecha autor.

### Cómo crear un commit:
```
$ git commit 
$ git commit -m "mensaje"
```
> **Nota:** Se puede crear un archivo `.gitignore` donde poner archivos que nunca se enviara al repositorio remoto (para guardar contraseñas, etc). Si se modifico algo en el `.env` despues de ponerlo en el `.gitingore` se tiene que borrar el `.env`, volver a crearlo y ponerlo al `.gitignore`. Se debe borrar en todas las "maquinas" en caso de trabajar de forma colaborativa para evitar errores

## ¿Qué es el HEAD?
Indica dónde te encuentras. Solo puedes estar en un lugar es decir el Head 

Referencia el punto actual del historial de cambios en el que se está trabajando
`HEAD -> main`
>Verificar con `git log`

## ¿Qué es una rama en git?
Puntero a un commit especifico (snapshot del proyecto en un momento dado). Son bifurcaciones del código

|Ramas                   |Ramas: Punteros       |
|------------------------|-----------------------|
|![](imagenes/branch.jpg)|![](imagenes/ramas.jpg)|

> **Nota:** La rama main solia llamarse master

## ¿Para qué sirven las ramas?
- Evitar pisar el avance de otro en modo colaborativo
- Permite trabajar de manera colaborativa (no es lineal)
Cada quien trabaja en una rama diferente y posteriormente las ramas vuelven a la rama `main`

## Crear una primera rama
Las ramas que creamos siempre son en base a nuestro ultimo commit y son independientes de otras.
### Crear rama
```
$ git branch <branch>
```
### Cambiar de rama
```
$ git checkout <brach>
$ git switch <branch>
```
### Comando para crear y cambiar de rama
```
$ git switch -c <branch>
```
> No se pueden crear ramas con el mismo nombre.

### Tener en cuenta
- Al crear la rama `(HEAD -> branch, main)` esto se debe a que las ramas son apuntadores y ambas ramas estan en el mismo nivel.
- Al hacer el primer commit dentro de la rama `(HEAD -> branch)` y la rama `main` sigue apuntando al commit anterior.
- Al hacer un commit en la rama `main` despues de la creacion de una rama ya no se visualiza el commit al que apunta.
![](imagenes/main.jpg)

# Clase 3
## Fusionar ramas
Al fusionar, el codigo de una rama se asimila en otra.

Se usa `git merge`, se le indica a que rama queremos aderir la rama en la que nos encontramos. Al ejecutarlo, se crea un commit que incluye todos los cambios de la rama origen a la rama actual.

> **Commit de fusión:** `Merge branch <branch>`

#### ¿Qué es un fast forward
Ocurre durante una fusión (merge) cuando la rama de destino no ha tenido nuevos commits desde que se creó o actualizó la rama de origen. En ese caso, Git puede simplemente mover el puntero de la rama de destino al último commit de la rama de origen, sin crear un nuevo commit de fusión

### Modificando el mensaje del commit
- Abre el editor antes de hacer el commit
    ```
    $ git merge --edit
    ```
- Evita que haga commit automaticamente
    ```
    $git merge --no-commit
    ```

Al hacer `git merge` no solamente crea el commit de la fusion, tambien trae todos los otros commits.
## Eliminar ramas ¿Por qué?
Es buena práctica y para mantener el codigo limpio
### Eliminando ramas
```
git branch --delete <branch>
git branch -D <branch>
git branch -d <branch>
```

## Comando: git rebase
Tiene el mismo efecto que `git reset -hard`
Por ejemplo, si se tienen varios commits, al usar `git rebase` los convierte en un solo commit

## Conflictos en Git 
Cuando Git no es capaz de determinar el cambio que tiene que prevalecer al hacer una fusion, surge un conflicto.
![](imagenes/conflicto.jpg)
Es común tener conflictos al intentar fusionar ramas que hacen cambios en el mismo archivo.

### Resolver conflictos
![Formato](imagenes/formato.jpg)

Dado un conflicto indica:         
```
$ git diff
```
- Cual es el conficto
- Qué esta produciendo el conflicto
- En qué archivo
- Formato de error

Los errores se pueden arreglar en el editor de compilacion eligiendo si se quiere aceptar uno, ambos cambios o ninguno

# Clase 4
# Clase 5


### Dato: Que es GitFlow 
Se define como un **sistema de _branching_ o ramificación o modelo de manejo de ramas en Git, en el que se usan las ramas principales y la _feature_. De modo que la rama _feature_ la crean los desarrolladores para fusionarla con la rama principal, únicamente cuando cumpla con sus labores.

# Clase 7
En que casos deshacemos cambios

deja de funcionar 

recuperar archivos

## Comando destructivos y no destructivos
- Destructivo: Afectan el historial de commits realizados.
- No destructivo: Trabajn en base al historial sin afectarlo.

>Ej. `git rebase` es un comando destructivo

### git reset
- soft: Mantiene los cambios que ocurrieron antes de hacer commit
- hard: Descarta los cambios

Resetea los cambios del commit lo deja en el estado anterior
similar a git commit —ammend 
`git reset --hard` cambia el id
se mantiene los cambios pero borra el commit (los 4 holas se mantienen)

mantiene en el estado de modiffied

esto no es ni hard ni soft (no esta en modiffied)

### git revert
Revierte los cambios de un commit y crea uno nuevo con los cambios revertidos.

no borra commits (no es desctructivo)

solo afecta los cambios del commit que le estamos diciendo

devuelve al **padre**  del commit
te devuelve al estado anterior (se puede usar para el merge y para el pull)
git checkout <id> entramos a un comiit pasado y agarramos la modificacion que necesitamos

> `git reset` o `git revert` cuando sabemos que cambios hicimos

`git show <id>` muestra  

`git reflog` → log de como se fueron cambiando el historial de commits

# Comandos
 `comando && comando` -> se pueden concatenar dos comandos

`$ git init nombre-proyecto`: inicializar nuevo repositorio en el directorio actual

`$ git status`: muestra si existe algun archivo modified

`$ git add .`: mueve todos los archivos modificados al area estado staged

`$ git add <file>`: pone en el area staged solo los archivos seleccionados

`$ git commit`: crea un commit sobre el archivo

`$ git commit -m "mensaje"`: hacer un commit directamente en el bash

`$ git restore --staged <file>`: quita archivos del area de staged

`git log`: para ver los commits realizados con id, fecha, nombre, correo y nombre del commit

`git log --oneline`: solo nombre e identificador del commit

`$ git commit --amend -m "mensaje"`: "renombrar" el texto del commit realizado pero cambia el identificador

`git checkout`

`git rm --cached <archivo_a_ignorar>`: en lugar del .gitignore

`git switch -`: intercala entre dos ramas

## Comandos para ramas
`git branch` listado de ramas

`git branch <branch>`: crear rama

`git branch -a`: permite visualizar todas las ramas incluyendo ramas de la nube

`git checkout <brach>`: Cambiar de rama

`git switch <branch>`: Cambiar de rama

`git merge <branch>`: hacer fusion

`git merge <branch> --no-ff`: se crea el commit apesar de que era posible hacer un ff

`git merge --abort`: cancelar merge

`git branch -D <branch>`: eliminar ramas (forzando) aunque no esten merged

`git branch -d <branch>`: eliminar ramas evitando borrar ramas sin merged

`git log --oneline --graph`: muestra donde se ha hecho los commits que implican una fusion 