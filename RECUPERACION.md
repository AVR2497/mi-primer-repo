# Proceso de Recuperación de Archivo Borrado

En esta actividad, simulé un error común al trabajar con Git: el borrado accidental de un archivo y la posterior necesidad de recuperarlo.

## ¿Qué error simulaste?

El error que simulé fue la **eliminación accidental del archivo `hola.txt`** del directorio de trabajo y la confirmación de esta eliminación mediante un commit en el repositorio local.

Los pasos exactos que seguí para simular el error fueron:

1.  Utilicé el comando `rm hola.txt` para borrar el archivo del sistema de archivos.
2.  Verifiqué la eliminación con el comando `ls`.
3.  Utilicé el comando `git status` para ver que Git detectaba el archivo como borrado.
4.  Utilicé el comando `git add hola.txt` para registrar la acción de borrado en el área de staging.
5.  Finalmente, realicé un commit con el comando `git commit -m "Simulación de error: borrado archivo hola.txt"`.
6.  Incluso subí este cambio al repositorio remoto en GitHub con `git push origin master`.

## ¿Qué comandos usaste para recuperar el archivo?

Para recuperar el archivo `hola.txt`, utilicé los siguientes comandos:

1.  **`git reflog`**: Este comando me permitió ver el historial de las acciones de las referencias (como `HEAD` y `master`). Busqué la entrada correspondiente al commit anterior a la eliminación del archivo, identificando su hash (`9f70ef0`).

2.  **`git checkout <hash_del_commit_anterior> -- <nombre_del_archivo>`**: Utilicé este comando para extraer la versión del archivo `hola.txt` tal como existía en el commit anterior al error. El comando específico que ejecuté fue:
    ```bash
    git checkout 9f70ef0 -- hola.txt
    ```
    Este comando restauró el archivo `hola.txt` en mi directorio de trabajo y lo añadió al área de staging.

3.  **`git commit -m "Recuperado archivo hola.txt"`**: Finalmente, realicé un nuevo commit para guardar la recuperación del archivo en la historia del repositorio local.

4.  **`git push origin master`**: Para reflejar la recuperación en el repositorio remoto de GitHub, subí el nuevo commit.

## ¿Qué aprendiste de la experiencia?

De esta experiencia aprendí varias cosas importantes sobre el manejo de errores y la recuperación en Git:

* **La importancia de `git reflog`:** Esta herramienta es invaluable para rastrear cambios en el historial de Git, incluso aquellos que no están directamente representados por las ramas. Me permitió encontrar fácilmente el estado del repositorio antes del error.
* **El poder de `git checkout` para restaurar archivos específicos:** Pude recuperar un archivo en particular desde un commit anterior sin tener que revertir todo el repositorio a ese estado. Esto es mucho más seguro y eficiente cuando solo necesitas recuperar un elemento.
* **La necesidad de hacer commit de las recuperaciones:** Al igual que cualquier otro cambio, la recuperación de un archivo debe ser registrada con un commit para que quede en la historia del repositorio.
* **La tranquilidad de tener un sistema de control de versiones:** Saber que puedo deshacer errores como la eliminación accidental de archivos me da más confianza al trabajar en mis proyectos. Git proporciona las herramientas necesarias para corregir estos problemas sin perder el trabajo por completo.

En el futuro, seré más consciente al eliminar archivos y recordaré la existencia de herramientas como `git reflog` y `git checkout` para la recuperación en caso de errores.
