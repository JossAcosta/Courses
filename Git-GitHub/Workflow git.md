# GIT
* Git es un sistema de control de versiones (VCS).
* Trabaja de una manera distribuida.

## Ventajas
* Velocidad.
* Diseño Sencillo.
* Desarrollo no lineal: cuentas con bifurcaciones dentro de tu línea del tiempo.
* Completamente distribuido.
* Capaz de manejar grandes proyectos.

## Integridad
* En git no se puede perder información durante el proceso o sufrir corrupción de archivos; ya que almacena los cambios dentro de un **SHA-1**.
> **SHA-1:** Conjunto de 40 carácteres hexadecimales que hace referencia a los cambios realizados.

## Estados de git
* Working Directory
* Staging Area
* Git Directory / Repository

## Configuración
> Los siguientes comandos nos ayudarán a configurar de manera global nuestro entorno de git.
> * global - ajustes globales de Git
> * local - solamente en este repositorio
* **Comando que afectará a todo el entorno global de git:**
```git
git config --global
```
* **Configurar el correo:**
```git
git config --global user.email <correo>
```
* **Configurar el nombre de usuario:**
```git
git config --global user.name <nombre de usuario>
```
* **Configurar los colores de git:**
```git
git config --global color.ui true
```
* **Configurar editor de texto:**
```
git config --global core.editor <editor de texto>
```
* **Configurar Atom como editor de texto:**
```
git config --global core.editor "<path>/atom.cmd --wait"
```
## Comandos básicos
* **Crear carpetas:**
```git
mkdir <nombre de la carpeta>
```
* **Crear archivos:**
```git
touch <nombre del archivo>
```
* **Borrar archivos:**
```git
rm <nombre del archivo>
```
* **Borrar carpetas:**
```git
rm -rf <nombre de la carpeta>
```
* **Conocer en que directorio estoy:**
```git
pwd
```
## Working directory
* **Iniciar un repositorio:**
```git
git init
```
* **Iniciar un repositorio en una carpeta en particular:**
```git
git init <nombre de la carpeta>
```
* **Borrar la carpeta del repositorio (cuidado: borraras todo el historial):**
```git
rm -rf .git
```
* **Saber el estatus de los archivos:**
```git
git status
```
## Staging area
* **Agregar un archivo o carpeta en específico a staging area:**
```git
git add <archivo | carpeta>
```
* **Agregar todos los archivos y carpetas a staging area:**
```git
git add < . | -A >
```
* **Hacer un Unstage:**
```git
git rm --cached <archivo>
```
* **Hacer un Unstage y borrarlo:**
```git
git rm -f <archivo>
```
## Git directory | Repository
* **Confirmar cambios (commit):**
```git
git commit -m "<mensaje>"
```
* **Concatenar un nuevo cambio con un cambio previo - sobreescribir el mensaje anterior:**
```git
git commit --amend -m "<mensaje nuevo>"
```
* **Listar commits:**
```
git log
```
## Tags
* **Tags lightweight / Sin mensaje:**
```git
git tag <versión>
git tag <version> <SHA>
```
* **Tags annotated / Con mensaje:**
```git
git tag -a <versión> -m '<mensaje>'
```
* **Listar tags:**
```git
git tag -l
```
* **Borrar tags:**
```git
git tag -d <versión>
```
* **Renombrar tags:**
```git
git tag -f -a <versión> -m '<mensaje>' <SHA>
```
## Git log
* **Ver la historia de nuestro proyecto:**
```git
git log
```
* **Logs resumidos:**
```git
git log --online
```
* **Logs con gráficas:**
```git
git log --oneline --graph
```
* **Log de un commit en específico:**
```git
git log -<SHA>
```
## Git diff
> Nos permite saber que cambios hubo entre el commit "a" y "b".
* **Ver los cambios que hay entre el commit actual y un commit en específico:**
```git
git diff <SHA>
```
* **Ver los cambios que hay entre commits:**
```git
git diff <SHA> <SHA>
```
## Git reset
> * Debemos seleccionar el commit anterior al que queremos resetear.
> * Si nosotros tenemos 10 commits y borramos el número **7**, los commits **8**,**9** y **10** serán borrados, y el nuevo commit sería el número **8**.
* **Borrar algo desde Stage:** (HEAD -> En donde estamos trabajando)
```git
git reset HEAD <archivo>
```
* **Sobreescribir o resetear un commit:**
```git
git reset <--soft> | <--mixed> | <--hard> | <--merge>
```
* **Git reset --soft:** (Borra solo el commit, los archivos estarán en **Stage area**)
```git
git reset --soft <SHA>
```
* **Git reset --mixed:** (Borra solo el commit, los archivos estarán en **Working directory**)
```git
git reset --mixed <SHA>
```
* **Git reser --hard**
  * Descarta los cambios desde el commit que indiquemos.
  * Borrará los archivos del stage area y del working directory (Prácticamente borrará todo).
  * Si no se específica un commit, será ejecutado dentro de donde estemos (HEAD).
  * Si tenemos archivos en working directory (untracked files) estos archivos no se pueden borrar porque Git no puede manipularlos.
```git
git reset --hard
git reset --hard <SHA>
```
* **Recuperar un commit después de borrarlo:** (Debes conocer el SHA)
```git
git reset --hard <SHA deseado>
```
## Git branch
* **Crear una branch:**
```git
git branch <nombre>
```
* **Listar branches:**
```git
git branch -l
```
* **Borrar una branch:** (Este borrado no funciona si la branch tiene commits)
```git
git branch -d <nombre>
```
* **Forzar el borrado:**
```git
git branch -D <nombre>
```
* **Renombrar una branch:**
```git
git branch -m <nombre viejo> <nombre nuevo>
```
## Git checkout
* **Mover entre branches:**
```git
git checkout <nombre de la rama>
```
* **Mover a un commit:** (Se crea como una rama virtual: Es usada para encontrar errores)
```git
git checkout <SHA>
```
* **Crear una branch con checkout:**
```git
git checkout -b <nombre de la rama>
```
* **Descartar cambios del working directory:**
```
git checkout -- <archivo>
```
## Git merge
* **Mezclar cambios:**
```git
git merge <nombre de la rama>
```
* **_Fast – Forward:_** Una rama que estaba en la continuación directa de la rama de la que vino, se fusionó.
* **_Recursive:_** Cuando 2 ramas salen al mismo tiempo de una rama, pero ya se ha fusionado una rama anterior,;en el momento en que desea combinar la segunda rama, no la recuerda y hace una fusión recursiva.
* **_Conflict:_** Fusiona 2 ramas pero en cada una de ellas, haces un cambio en las mismas líneas; ¿Por lo tanto debes elegir con qué versión te quedarás?
## Git Rebase
* **Sobreescribir la historia de nuestro proyecto (El SHA cambia):**
  * Es muy peligroso usarlo, solamente usarlo cuando trabajes en local.
```git
git rebase <rama>
```
* **Rebase interactivo:**
  * **Tipos de rebase:** < pick | reward | edit | squash | fixup | exec | drop >
```git
git rebase -i <rama>
```
## Git Stash
* **Es una etapa intermedia, que guarda los cambios sin hacer commits:** ( Los cambios debe estar en Stage o deben ser modificados)
```git
git stash
```
* **Ver la lista del Stash:**
```git
git stash list
```
* **Borrar Stash:**
```git
git stash drop <stash@{numero}>
```
* **Aplicar los cambios:** (Solo se aplica el último cambio que se encuentra en el valor {0})
```
git stash apply
```
* **Aplicar los cambios a cualquier Stash:**
```
git stash apply <stash@{numero}>
```
## Cherry pick
* **Solucionaste un problema en una branch incorrecta y debes moverlo a la branch correcta:**
  * Elige el commit que necesitas mover.
```
git cherry-pick <SHA>
```
