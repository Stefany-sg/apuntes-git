# Curso Git y Github 2025
## Qué es markdown?
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
Nos permite trabajar colaborativamente
Herramienta de control de versiones. Al  ser un sistema distribuido aloja una copia del repositorio en cada maquina local y se puede tener uno o varios repositorios remotos
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
git init nombre-proyecto
cd nombre-proyecto
```

Alternativa:

```
git init nombre-proyecto --initial-branch=main
```

### Dato: Que es GitFlow 
Se define como un **sistema de _branching_ o ramificación o modelo de manejo de ramas en Git, en el que se usan las ramas principales y la _feature_. De modo que la rama _feature_ la crean los desarrolladores para fusionarla con la rama principal, únicamente cuando cumpla con sus labores.

# Clase 2
## States y commits
- ### Modified
    Cuando un archivo se crea, elimina o tiene cambios no confirmados
- ### Staged
    Área temporal transitoria : Archivo marcado listo para ser confirmado en el repositorio local
En esta area de staged van todos los archivos que queremos agregar nuestro commit. 
- ### Commited
    Los cambios son confirmados y grabados en el repositorio. Esto es un **commit**

## Qué es un commit?
Ej. Checkpoint de un videojuego
Muestra los archivos en el momento que se hizo fecha autor.
Es como un punto de restauracion, guarda el avance en un determinado punto de tiempo?
Comando:
Pide escribir un mensaje describiendo el commit
```
$ git commit
```
# Clase 3
# Clase 4
# Clase 5