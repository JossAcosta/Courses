# Github
## Llave SSH
* **Crear llave SSH:**
```git
ssh-keygen -t rsa -b 4096 -C "<correo>"
```
> * **ssh-keygen:** Generador de la llave SSH.
> * **-t rsa:** Transforma la llave con el algoritmo rsa (podría ser SHA, pero Github propone rsa).
> * **-b 4096:** Git propone este número de bits para crear las llaves.
> * **-C "\<correo\>":** Correo electrónico del usuario.
* **Copiar la llave:** (Pegarla dentro de la configuración de Github)
```git
cat ~/.ssh/id_rsa.pub
```
* **Saber si tenemos una llave SSH:**
```git
ls -al ~/.ssh | grep ".pub"
```
* **Correr el ssh-agent en segundo plano:**
```git
eval "$(ssh-agent -s)"
```
* **Agregar la llave SSH privada al ssh-agent:**
```git
ssh-add ~/.ssh/id_rsa
```
* **Validar la llave SSH con- Github:**
```git
ssh -T git@github.com
```
## Git clone
* **Clonar un repositorio de Github:**
```git
git clone <URL>
```
## Git remote
#### Comunicar el repositorio local con el remoto
* **Agregar un repositorio remoto:**
```git
git remote add <nombre del repositorio remoto> <URL>
```
* **Saber si el repositorio fue agregado correctamente:**
```git
git remote -v
```
* **Borrar el repositorio remoto:**
```git
git remote remove <nombre del repositorio remoto>
```
* **Ver la información referente al repositorio remoto:**
```git
git remote show origin
```
* **Track una branch remota:** (Creará una rama local con el mismo nombre de la rama remota)
```git
git checkout --track <remote>/<branch>
```
* **Track la rama HEAD**
```git
git branch -u <remote>/<branch>
```
* **Mandar al repositorio remoto una rama creada en el local:** (Creará la rama local en el repositorio remoto)
```git
git push -u <remote> <branch>
```
* **Ver las trancking branches configuradas**
```git
git branch -vv
```
* **Borrar una branch en el repositorio remoto**
```git
git push <remote> --delete <branch>
```
* **Borrar una rama remota en el local:** (No la elimina del repositorio remoto)
```git
git branch -d -r <remote>/<branch>
```
## Git pull | fetch
* **git fetch**
  * Recupera los últimos metadatos desde el repositorio remoto, esto para verificar si hay algún cambio disponible (No transfiere ningún cambio)
```git
git fetch <nombre del repositorio remoto> <nombre de la rama remota>
```
* **Actualizar las tracking branches**
```git
git fetch --all
```
* **git pull**
  * Este comando traerá los cambios desde el repositorio remoto y los mezcla.
```git
git pull <nombre del repositorio remoto> <rama remota>
```
> Sí al mezclar tus cambios hubo un conflicto, git creará una rama llamada **(branch|MERGING)** y deberás corregir manualmente el merge de los archivos afectados
* **Si al mezclar ocurre un error, intenta con el siguiente comando:**
```git
git merge <nombre del repositorio remoto/nombre de la rama remota> –allow-unrelated-histories
```
## Git push
* **Mandar los cambios del repositorio local al remoto:**
```git
git push <nombre del repositorio remoto> <nombre de la rama local>
```
* **Mandar tags del repositorio local al remoto:**
```git
git push <nombre del repositorio remoto> <nombre de la rama local> –tags
```
* **Mandar branch del repositorio local al remoto:**
```git
git push <nombre del repositorio remoto> <nombre de la rama local>
```
## Git ignore
> Si tienes archivos que contengan datos confidenciales y no deseas mandarlos al repositorio remoto, solo debes crear un archivo con el nombre **.gitignore** y poner dentro de el o los nombres de los archivos / carpetas que deseas ignorar.

## Templates
* **Pasos para crear templates**
  * Crear una **carpeta** en la raíz del proyecto con el nombre de **.github**.
  * Dentro de la carpeta se alojarán los templates.
  * Podemos crear templates para issues y pull request, estos a su vez pueden tener varios templates.
  * Para alojar varios templates de PRs e issues, debemos crear una carpeta expecífica para cada uno:
    * PRs:    .github/PULL_REQUEST_TEMPLATE/
    * Issues: .github/ISSUE_TEMPLATE/
  * Dentro de estas carpetas debes crear los templates (archivos markdown **.md**) de cada uno.
  * La nomenclatura para el nombre del archivo del template del PR es la siguiente: **pull_request_template.md**
  * Al finalizar tendrás algo parecido a esto:
    **.github/PULL_REQUEST_TEMPLATE/pull_request_template.md**
    **.github/ISSUE_TEMPLATE/***
