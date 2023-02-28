# WINDOWS
### Desplazarse entre carpetas:
```
cd desktop
```
### Desplazarse entre varias carpetas:
```
cd desktop/MyRepos-Github/Dart-cheatSheet
```
### Si el nombre de la carpeta tiene espacios se usan las comillas:
```
cd “curso de git y github”
```
### Crear una carpeta:
```
mkdir carpetaNueva
```
### Ver todo el contenido dentro de un directorio:
```
ls
```
### Retroceder una carpeta
```
cd ..
```
### Regresar al directorio raíz:
```
cd
```
### Eliminar una carpeta:
```
rmdir nombreCarpeta
```
# GITBASH and GIT
>Escribir `q` para salir cuando se abre el editor propio para comentarios o ver los commits.

### Copiar texto:
`Control + tecla insert`
### Pegar texto:
`Shift + tecla insert`
### Limpiar pantalla:
`clear`
### Configurar usuario:
```
git config --global user.name "educa"
```
### Ver el nombre del usuario:
```
git config user.name
```
### Configurar email:
```
git config --global user.email “aquivaelcorreo@gmail.com”
```
### Ver el email del usuario:
```
git config user.email
```
>si se requiere la configuración de usuario y email para un único repositorio se omite --global

>>es recomendable usar el correo que te asigna github, para ello se va a la cuenta en configuraciones, luego emails, y en la sección primary email address, estará un correo con el formato: números+nombreDeUsuario@users.noreply.github.com

### Iniciar el uso de control de versiones:
```
git init
```
### Configurar nombre de la rama por defecto:
**Si durante la instalacion de git se selecciono que la rama por defecto se llame main, no es necesario hacer esto; pero si ya se tenia instalado git, la rama por defecto la asigna como master, pero nuevos estándares recomiendan usar main en lugar de master.**
```
git config –global init.defaultBranch main
```
**TENER EN CUENTA: que si se crea un repositorio sin haber ejecutado el comando anterior para que asigne a la rama por defecto main, la rama se llamara master y no cambiara automáticamente a main si se ejecuta la configuración por defecto de la rama, para ello hay que ingresar manualmente(buscar en las carpetas no desde gitbash) al repositorio y activar la visión de carpetas ocultas y borrar la que dice `.git` y nuevamente situarse en el repositorio y ejecutar el `git init`, allí si se creara el nombre de la rama con `main`.**

### Verificar el estado del repositorio local:
```
git status
```
### Abrir visual studio code desde bash:
Situarse en la carpeta que contiene el repositorio y escribir:
```
code . 
```
### Agregar cambios al área de stage:
```
git add nombre-archivo.txt
```
**si son varios archivos que se quiere subir al área de stage:**
```
git add .
```
### Retirar del area de stage(unstage):
```
git rm –cached archivo
```
### Crear commit:
```
git commit
```
**esto abre un editor de texto por defecto o uno que se pudo configurar al momento de la instalación de git o se puede configurar para que use el editor que queramos.**
### Cuando es un comentario corto:
```
git commit -m “aqui va un comentario”
```

### Configurar para que los mensajes de commits se abran en VScode:
```
git config -global core.editor “code -wait”
```
### Mas info sobre asociar otros editores de texto:
Associating text editors with Git - GitHub Docs
### Editar un comentario de un commit:
**solo es recomendable hacer en el repositorio local**
```
git commit -amend
```
### Deshacer el ultimo commit que se hizo:
```
git reset -soft HEAD~1
```
**el contenido del archivo no se va a modificar, es decir mantiene los cambios, solo el historial del commit cambia. Si en lugar de soft agregamos –hard para no mantener los cambios de ese commit**
### Crear una rama nueva:
```
git branch NombreNuevaRama
```
### Ver las ramas que tiene el repositorio:
```
git branch 
```
### Cambiar de ramas:
```
git checkout NombreNuevaRama
```
### Crear una rama y situarse en esa rama directamente sin hacer el comando `checkout`:
**Se crea a partir de la rama principal.**
```
git checkout -b nombreRamaNueva
```
### Cambiar nombre de ramas:
**Se cambia a la rama que se quiere cambiar de nombre**
```
git branch -m nombreRama
```
### Cambiar nombre de rama (no desde la rama que queremos cambiar):
```
git branch -m nombreactualRamaAcambiar nombreRamaAmodificar
```
### Eliminar una rama:
**Rama de respos locales y no debes estar ubicado en la rama a eliminar**
```
git branch -d ramaAeliminar
```
### Ver el registro de commits:
```
git log
```
### Ver el registro de commits en una linea:
```
git log --oneline
```
### Ver el registro de commits con los cambios:
```
git log -p
```
### Fusionar rama al Proyecto principal:
**Hay que estar en la rama que recibirá la fusión(main).**
```
git merge nombreDeLaOtraRama
```
### Continuar haciendo el merge cuando se ha arreglado un conflicto de dos archivos diferentes:
```
git merge –continue
```
# GITHUB
## Clonar un repositorio de GitHub a local:
>`origin` es el nombre que se asocia al repositorio remoto que esta en github.

>Se abre el repositorio a clonar, se va al botón verde que dice code, se elige HTTPS y se copia el link.
```
git clone  https://rutadelrepositorio
```
### Consultar nombre de servidor remoto:
```
git remote
```
### Mas sobre git remote(fetch y push):
>`fetch` obtiene los cambios en el repositorio remoto.

>`push` envia los cambios de local a remoto.
```
git remote -v
```
### Enviar cambios al repositorio remoto:
```
git push origin main
```
>OJO: cuando se usa el mismo git(usuario y email) que fue utilizado para una cuenta de github anterior, al cambiarle las credenciales nuevas(usuario y email acorde a la nueva cuenta de github da un error de acceso denegado, pese a haber actualizado el usuario y email que usamos en la nueva cuenta de github, sale un error de acceso denegado al usuario anterior, y esto es debido a que almacena las primeras credenciales de autenticación en cache y por mas que se las actualiza con los datos de la nueva cuenta sigue mostrando error de acceso al usuario pasado.

#### Para solucionar eso:
1. ChatGPT me recomendó ejecutar el siguiente código para borrar la cache de autenticación de git
```
git config --global --unset credential.helper
```
**pero no funciono!**

2. Como segunda opcion me dijo que borre la cache de autenticacion manualmente:
```
%HOME%\AppData\Local\GitHub\Roaming\ 
```
**Busque la carpeta en el disco C, pero solo encontré hasta Local, la carpeta GitHub no apareció.**

3. Le dije a ChatGPT que no encontraba la carpeta GitHub y me dijo que: Es posible que en mi caso la carpeta donde se encuentra la caché de autenticación de Git no se haya creado todavía.

Me volvió a recomendar ejecutar el primer comando mencionado arriba:
```
git config --global --unset credential.helper
```
pero como ya lo había ejecutado antes, no lo volvi hacer porque no me funcionaba. 

Sin embargo había otra segunda opción que recomendaba y era ejecutar:
```
printf "protocol=https\nhost=github.com\n" | git credential-manager-core erase
```
4. ChatGPT :Este comando debería eliminar cualquier caché de autenticación de Git para GitHub en tu sistema.

5. Le pregunto: me salio este mensaje: warning: git-credential-manager-core was renamed to git-credential-manager warning: see https://aka.ms/gcm/rename for more information.

6. ChatGPT :Puedes ignorar esta advertencia y utilizar el nuevo comando:
```
git-credential-manager
```
en su lugar. 
7. Así que, para borrar la caché de autenticación de Git en Windows, ejecuta el siguiente comando en Git Bash o en la terminal que estés utilizando:
```
printf "protocol=https\nhost=github.com\n" | git credential-manager erase
```

Este comando debería eliminar cualquier caché de autenticación de Git para GitHub en tu sistema.

8. Finalmente el ultimo comando me funciono y pude ejecutar:
```
git push origin main
```
donde me abrio un recuadro para ingresar el token de autenticación que lo cree en la nueva cuenta de Github(settings/developer settings/personal Access tokens).
### Actualizar un repositorio local con los cambios realizados en un repositorio remoto:
**Si hay cambios en remoto con git pull se trae esos cambios y se combinan con los cambios en local**
```
git pull origin main
```
**Este commando trae automaticamente todos los cambios que existan en el repositorio remoto y los incorpora al repositorio local, siempre y cuando no haya conflictos.**
## Git pull vs Git fetch
### git pull
Comando que descarga todo el contenido o cambios del repositorio remoto y fusiona con los cambios del repositorio local, para que ambos repos tengan la misma información.
### git fetch
Comando que verifica los cambios hechos en el repositorio remoto **SIN COMBINAR** con los cambios del repositorio local.
```
git fetch origin
```
Otra variante para hacer la misma acción:
```
git fetch 
```
### Visualizar los cambios remotos antes de combinar los cambios con el repo local
```
git checkout origin/main 
```
**Si queremos Volver a ver los cambios como estaban antes de visualizar los cambios que tenia remoto:**
```
git checkout main
```
### Crear un repositorio local y subirlo por primera vez a GITHUB
 1. Creamos una carpeta donde se almacenará el repositorio.
2. Desde gitbash nos ubicamos en la carpeta anterior y ejecutamos `git init`, para indicar que queremos rastrear los cambios de ese repo.
3. Luego ejecutamos `code .` para abrir vscode.
4. Una vez que abre `vscode` creamos el archivo que tendrá nuestro repositorio.
5. Ejecutamos `git add .` para preparar los archivos o cambios que hemos hecho.
6. Ejecutamos `git commit -m “aquiVaElMensaje”` o `git commit` para abrir el vscode y escribir el mensaje.
7. Creamos un repositorio nuevo en github, solo agregamos el nombre, no agregamos descipcion, ni agregamos el archivo `README.md`, esto abrirá en github unas indicaciones de sugerencia.
8. Ejecutamos el comando: 
```
git remote -v
```
>Esto no mostrara nada, porque el repo local no tiene ningún comunicación github.

>>Anteriormente(cuando clonamos un repo remoto a local y ejecutamos ese comando, mostraba (fetch) y (pull).

9. Ahora debemos ejecutar:
```
git remote add origin https://enlace de repositorio (este enlace lo da github cuando creamos el repo vacio).
```
10. Volvemos a ejecutar:
```
git remote -v
```
**Ahora si nos da el (fetch) y el (push)**
>si ejecuto git fetch, no sale nada porque debo ejecutar el comando que visualiza los cambios.

11. Ejecuto el comando para ver los cambios: 
```
git checkout origin/main
```
**Me sale este error: **

>error: pathspec 'origin/main' did not match any file(s) known to git

porque en el repositorio de github no se ha creado ningún archivo, solo el repositorio, por lo tanto no encuentra el archivo README.md y no tiene como comparar cambios para visualizar.

12. Subimos lo cambios locales a github:
```
git push origin main
```
## Bifurcar un repositorio(Fork):
Se va al repositorio(de otro usuario por lo general) y se da click en el icono `Fork`.
Esto copia el mismo repositorio del dueño del repo en tu cuenta de github.
## Clonar repositorio bifurcado en local
```
git clone https://enlacedeTuCuentadeGithubDelRepoAClonar
```
## Pull request
Solicitud de combinar tus cambios con el repositorio original.

>Primero se hace un `fork` a tu cuenta de github, luego se clona para llevarse ese repo a local, se hace algún cambio y se sube esos cambios a tu repositorio bifurcado de github, y finalmente se hace la solicitud de `pull request` para que el dueño del repositorio acepte o no tus cambios.

## Pull request apartir de una rama
1. Primero se hace un `fork` a tu cuenta de github, luego se clona para llevarse ese repo a local, con `git clone https://enlaceDeturepobifurcado`. 
2. Luego creamos una nueva rama en nuestro repo en local:
```
git checkout -b nombreRama
```
**esto creara la nueva rama y nos ubica en ese rama nueva.**

3. Modificamos el archivo y agregamos al stage:
```
git add . 
```
4. Registramos los cambios:
```
git commit
``` 
Ahora toca subir estos cambios al repo remoto ya que solo están listos en local en la nueva rama.
```
git push origin nombreNuevaRamaCreadaEnLocal
```
**Esto crea una nueva rama en el repositorio remoto**

**Nos ubicamos en la nueva rama que se creo en github y ya podremos hacer el pull request**
## Actualizar un repositorio bifurcado:
1. Se puede dar el caso que el repositorio bifurcado tuyo se quede atrás con nuevos cambios que implemento el repositorio del dueno del repositorio.

2. En github hay una opción que dice `Sync fork` nos dará dos opciones, 1|ver cambios y 2| actualizar rama. La 1 opcion permite ver que cambios se han hecho de la rama del dueño del repo con la rama que tenemos. Y la 2 opcion actualiza automáticamente los cambios del repo del dueño con la rama que tenemos en github.

3. Pero el repo local no tiene conocimiento que se ha actualizado el repo que tenemos en remoto, para ello hay que traerse esos cambios.

**nos ubicamos en la rama main,luego ejecutamos:**
``` 
git pull origin main 
```

>OJO: es recomendable crear una nueva rama en el repo bifurcado y allí hacer los cambios que querramos, siempre se recomienda dejar la rama main del repo bifurcado intacta para poder actualizar automáticamente con la rama del repo que hemos bifurcado ya que si trabajamos sobre main al traer los nuevos cambios del repo bifurcado tendremos conflictos.

## ISSUES
Registra tareas que queremos abordar en el futuro.

Antes de un `PULL REQUEST` se abre un `ISSUE` donde se discute que cambios se quiere hacer, como se va a hacer para saber si lo va aprobar o no, esto evita invertir horas en vano para esa tarea. Tambien se puede hacer esos ISSUES en nuestro propio repo.

## Crear ramas en github
En github hacemos click en el icono de la rama `main`, allí escribimos el nombre de la nueva rama que queremos crear, como la rama nueva no existe, github nos propone la creación de la nueva rama.
## Traer esa rama a local
Primero clonamos el repositorio con:
`git clone https://repoEnGitHub`
Esto trae el repositorio remoto **solo** con la rama main.

Para traer los demás cambios, es decir la rama que se creo en github, se ejecuta
```
git pull origin nombreDelaRama
```
Esto no hará nada, ya que en local no existe esa rama, entonces no puede traer los cambios.

Veremos los cambios que existen con:
```
git fetch origin
```
Una vez que tenemos los cambios ejecutamos:
```
git checkout nombreRamaNuevaCreadaEnGithub
```
**`git fetch` en este caso al ver que hay una nueva rama en github y no en local, crea la nueva rama y trae los cambios**

**Otra alternativa era crear una rama en local con el mismo nombre de la rama de github y hacer el git pull para combinar esos cambios**

## Eliminar rama tanto en local como en repo remoto
Nos ubicamos en la rama principal `main`, con 
```
git checkout main
```
Ejecutamos el comando para eliminar la rama local:
```
git branch -d nombreRamaAeliminar
```
**esto elimina la rama local**

Si ejecutamos el siguiente código veremos las ramas que tiene el repo remoto:
```
git branch -a 
```
Para eliminar la rama en remoto, se puede hacer directamente en github, pero si queremos hacerlo desde la línea de comandos de gitbash:
```
git push origin -d nombreDeLaRamaRemota
```
Comprobamos si se elimino la rama:
```
git branch -a
```
