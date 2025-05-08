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

![](imagenes/branch.jpg)
> **Nota:** La rama main solia llamarse master

## ¿Para qué sirven las ramas?
- Evitar pisar el avance de otro en modo colaborativo
- Permite trabajar de manera colaborativa (no es lineal)
Cada quien trabaja en una rama diferente y posteriormente las ramas vuelven a la rama `main`

## Crear una primera rama
Las ramas que creamos siempre son en base a nuestro ultimo commit
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
> No se pueden crear ramas con el mismo nombre

### Tener en cuenta
- Al crear la rama `(HEAD -> branch, main)` esto se debe a que las ramas son apuntadores y ambas ramas estan en el mismo nivel.
- Al hacer el primer commit dentro de la rama `(HEAD -> branch)` y la rama `main` sigue apuntando al commit anterior.
- Al hacer un commit en la rama `main` despues de la creacion de una rama ya no se visualiza el commit al que apunta.
![](imagenes/main.jpg)

# Clase 3
# Clase 4
# Clase 5


### Dato: Que es GitFlow 
Se define como un **sistema de _branching_ o ramificación o modelo de manejo de ramas en Git, en el que se usan las ramas principales y la _feature_. De modo que la rama _feature_ la crean los desarrolladores para fusionarla con la rama principal, únicamente cuando cumpla con sus labores.


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

`git log --oneline --graph`

`$ git commit --amend -m "mensaje"`: "renombrar" el texto del commit realizado pero cambia el identificador

`git checkout`

`git branch` listado de ramas

