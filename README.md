#  Aprendiendo Git y GitHub
##  Temario
-  [¿Qué es git?](#qué-es-git)
-  [¿Por qué usar git?](#por-qué-usar-git)
-  [Instalación](#instalación)
	* Windows
	* Ubuntu/Debian
-  [Repositorio local](#repositorio-local)
	* Configuración Inicial
	* Creando un repositorio
	* Explicando el Stage
	* Commit
	* Reset
-  [Repositorio remoto](#repositorio-remoto)

##  ¿Qué es git?
Git es un software de control de versiones distribuidas, fue diseñado por Linus Torvalds en 2005, con el objetivo de aumentar la eficiencia y confiabilidad en el mantenimiento del versionado de software. Este software rastrea cualquier cambio en el conjunto de archivos especificado, este seguimiento a los cambios en el proyecto se le llama repositorio.
El repositorio trabaja de manera distribuida, esto quiere decir que todo el equipo de trabajo tiene una copia del proyecto, así como un repositorio central donde se sube los cambios y al equipo de trabajo se le ven reflejados estos cambios.

##  ¿Por qué usar git?

##  Instalación

##  Repositorio local

###  Configuración inicial
Ya que lo tenemos instalado y lo verificamos desde consola con el comando **`git --version`**, es muy importante configurar el git, para asignar un nombre y un correo con el cual se van a registrar las actualizaciones que realices.
-  **Nombre de usuario:**  `git config --global user.name <nombre>`
-  **Correo electrónico:**  `git config --global user.email <correo>`

-  **Configurar el nombre de la rama principal:**  `git config --global init.defaultBranch <nombre>`

-  **Ver la configuración global:**  `git config --global -e`
>  **Si en algún momento te sientes perdido puedes usar el comando `git help` o si tienes duda sobre algún comando en especifico utiliza el comando `git help <instrucción>`.**
ejemplo: `git help status`)

<hr/>

### Creando un repositorio
En git los proyectos son conocidos como repositorios, todo el contenido de esta aplicación va formar parte del repositorio.

**Pasos para crear un repositorio**
1. Crear una carpeta donde se encontrara nuestro repositorio.
2. Abrir una terminal o consola y ir al path de la carpeta recién creada.
3. Ya dentro de la carpeta introducir el comando `git init`

> _Con esto ya tenemos nuestro repositorio iniciado, dentro de directorio en el que nos encontramos se crea una carpeta oculta llamada .git que es donde crean los respaldos de nuestro repositorio
Aun faltan especiar los archivos que queremos que se realice un seguimiento_

<hr/>

### Explicando el stage
En git existen varios estados en el que se pueden encontrar los archivos del repositorio, estos estados son:
1.  **directorio de trabajo:** son los archivos con los que estarás trabajando y sufrirán algún cambo (sin seguimiento, siguiendo pero modificado)
>  `git status`  `git diff`

2.  **Stage:** Esta es una etapa preliminar, aquí se selecciona los archivos que quieres guardar en tu repositorio, una manera de verlo seria "Una caja donde pones cosas antes de meterlo al almacén" (Añadido, Añadido modificado)
>  `git add`  `git diff --staged`

3.  **Repositorio:** por ultimo esta la etapa de repositorio aquí a los archivos que se agregaron al stage, se les hace una instantánea y quedan guardados en caso de cualquier necesidad (siguiendo)
>  `git commit`

<hr/>

-  **Ver el Stage:**  `git status`
>  _Aquí se mostraran el listado de archivos o directorios que existen en el repositorio que han sufrido algún cambio y pueden integrarse al Stage_

<hr/>

-  **Agregar al Stage:**
	* Por Archivo: `git add <nombre.ext>`
	* Por Archivos del mismo tipo: `git add <*.ext>`
	* Por un directorio: `git add <carpeta/>`
	* Agregar todo: `git add .`
	
> _Algunas veces al agregar al stage, en consola se mostrara un error sobre el CRLF (CR - retorno de carro y LF - salto de línea), esto normalmente para especificar el formato de un salto de línea._
Para solucionar esto usa este comando: `git config core.autocrlf false`
 
<hr/>

-  **Ver las diferencias en el stage:**
	* Fuera del stage: `git diff`
	* Dentro del stage: `git diff --staged`

<hr/>

-  **Eliminar del stage:**
	* Por Archivo: `git reset <nombre.ext>`
	* Por Archivos del mismo tipo: `git reset <*.ext>`
	* Por un directorio: `git reset <carpeta/>`
	* Eliminar todo: `git reset`

<hr/>

### Commit
Cuando se realiza un commit, se genera una instantánea de los cambios confirmados, esta confirmación solo afecta en tu repositorio local, esto da la oportunidad de acumular las confirmación que necesites sin afectar el repositorio central

- **Manejo del commit:**
	* Realizar un commit:`git commit -m "<mensaje>"`
	
	* Ver los commit: `git log`
	
	* Revertir cambios al ultimo commit:  `git checkout -- .`

	* Actualizar el ultimo commit: `git commit --amend -<opcion(a, m, am, etc.)>`

<hr/>

### Reset
El comando reset es una herramienta para deshacer cambios, te permite restablecer tu estado actual a un estado específico. Puedes restablecer el estado de archivos específicos, así como el de todo una rama.

- **Restablecer una rama a un commit anterior**
Hay ocaciones en las que tendras que moverte entre commits anteriores y realizar cambios en estos. Básicamente rebobinamos el estado de la rama, luego todos los commits que hagamos en adelante se escriben sobre todo lo que vino después del punto de reinicio. 

	* Comando: `git reset <modo> <hash>`
	
	**Las opciones para MODE son:**
1. `--soft` no restablece el fichero índice o el árbol de trabajo, pero restablece HEAD para `commit`.
> Ejemplos:
git reset --soft HEAD^ - Restablece al ultimo commit sin modificar nada mas que el HEAD
2. `--mixed` restablece el índice, pero no el árbol de trabajo e informa de lo que no se ha actualizado.
3. `--hard` restablece el índice y el árbol de trabajo. Cualquier cambio en los archivos rastreados en el árbol de trabajo desde el `commit` son descartados.

	




















