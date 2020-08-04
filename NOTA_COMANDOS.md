# Comandos de Git y GitHub

## Tabla de Contenido
- [Sistema de control de versiones](#sistema-de-control-de-versiones)
  - [Tipos de sistemas de control](#tipos-de-sistemas-de-control)
- [Beneficios de Git](#beneficios-de-git)
- [Fundamentos de Git](#fundamentos-de-git)
- [Los 3 estados de Git](#los-3-estados-de-git)
- [Github](#github)
- [Configurar Git](#configurar-git)
- [Comandos de terminal](#comandos-de-terminal)
- [Comandos Git](#comandos-git)
  - [Flujos de Trabajo](#flujos-de-trabajo)
  - [Múltiples entornos de trabajo](#múltiples-entornos-de-trabajo)
- [Repositorios Remotos (Github)](#repositorios-remotos-github)
- [Configuraciones de Github](#configuraciones-de-github)
  - [Notificaciones](#notificaciones)
  - [Proteger un branch](#proteger-un-branch)
  - [Plantillas](#plantillas)
- [Ignorar archivos](#ignorar-archivos)
- [Recursos Complementarios](#recursos-complementarios)
- [Enlaces de Interés](#enlaces-de-interés)

## Sistema de control de versiones

Un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo. Este tipo de sistemas nos permiten volver en el tiempo y salvar nuestro trabajo.



### Tipos de sistemas de control

`Local Computer` Solo vive en nuestro computador.

<div align="center">
  <img src="imagenes/local.png">
  <small><p>Sistema de Control Local</p></small>
</div>

`Centralizado` No depende únicamente de un computador en el que se trabaja, sino que depende del súper servidor en donde se almacena la información. El servidor provee las copias a sus hijos, pero solo guarda los cambios en un solo lugar.

<div align="center">
  <img src="imagenes/centralizado.png">
  <small><p>Sistema de Control Centralizado</p></small>
</div>

`Sistema de control distribuidos` Cada uno de los que participan en el proyecto, tienen copia del proyecto que se realiza, por eso no dependemos de un solo computador que almacene toda la información.

<div align="center">
  <img src="imagenes/distribuido.png">
  <small><p>Sistema de Control Distribuido</p></small>
</div>

Git es un Sistema de Control de Versiones Distribuido.

Git fue creado por Linus Torvals



## Beneficios de Git

* `Velocidad` Puedes trabajar fluidamente desde tu computador.
* `Diseño sencillo` El codigo es robusto con las herramientas necesarias, como viajar en el tiempo.
* `Fuerte apoyo en el desarrollo no lineal` No trabaja de manera lineal, la linea del tiempo tiene bifurcaciones de manera independiente al proyecto principal.
* `Completamente distribuido` Cada quien puede tener una copia del proyecto.
* `Capaz de manejar grandes proyectos` Linux, Django, Laravel, etc. Usan git.



## Fundamentos de Git

* Git almacena una referencia a todos los archivos que no se han cambiado
* Casi cualquier operación en Git es local. Se puede trabajar offline
* Git tiene integridad. No puedes perder información durante su transmisión o sufrir corrupción de archivos sin que Git lo detecte

<div align="center">
  <img src="imagenes/checkins-over-time-git.png">
  <small><p>Almacenamiento de Archivos en GIT</p></small>
</div>

<div align="center">
  <img src="imagenes/checkins-over-time-subversion.png">
  <small><p>Almacenamiento de Archivos en Subversion</p></small>
</div>



## Los 3 estados de Git

* `Working Directory` Es donde trabajamos de manera local, pero para guardarlo hay que pasarlo al Staging Area
* `Staging Area` Es el área de preparación, se almacenan justo antes de hacer commit
* `Git repository` El repositorio donde almacenaremos los cambios del proyecto

<div align="center">
  <img src="imagenes/estados-git.png">
  <small><p>Estados de Git</p></small>
</div>



## Github

`GitHub` es una plataforma en la que se almacenan los cambios de un proyecto. Además es una plataforma que funciona como una red social. Aquí, las personas que visiten tu sitio puedan darle estrellitas a los proyectos que hayas desarrollado.

`Git` es el software que ayuda con el versionado y Github es la red social que nos va a ayudar a distribuir el software.



## Configurar Git

Configuración del usuario

```bash
git config --global user.email user@example.com
git config --global user.name "Ruber Hernandez"
```

Colorear el output del terminal de Git.

```bash
git config --global color.ui true
```

Configurar el editor de texto de git

```bash
git config --global core.editor ["editor --wait"] 
```

Ver la lista de configuraciones

```bash
git config --list
```


## Comandos Git

### Flujos de Trabajo

* `git init [nombre]` inicia un repositorio y crea la carpeta [nombre].
* `git status` muestra el estado de los archivos en el repositorio.
  * `untracked files` son archivos que están en nuestro Working Directory, lo que aparezca en rojo es lo que se ha modificado y hay que pasarlo al Staging.
  * `changes to be comitted` son los archivos que se encuentran en el staging area. Aparecen en verde.
* `git add [archivo]` agrega un archivo al staging
* `git add -A` agrega todos los archivos del working directory al staging area. `git add .` hace lo mismo.
 * `git add -n [archivo]` simula el agregado de un [archivo].
* `git rm --cached [archivo]` quita un [archivo] del staging al working area.
* `git rm -f` quita el archivo del staging y del working directory.
* `git commit -m ["mensaje"]` agrega el comentario al staging al repositorio.
* **`git commit -am ["mensaje"]`** agrega los archivos del staging al repositor y agrega comentario.
* `git commit --amend` anexa el nuevo cambio al anterior commit. Si se escribe un mensaje este sobreescribe el anterior.
* `git tag -a [tag] -m ["comentario"]` agrega el tag con un comentario al ultimo commit.
* `git tag -l` lista los tags.
* `git tag [tag] [sha1 del commit]` agrega un tag a un commit en partcular.
* `git tag -d [tag]` elimina el tag.
* `git tag -f -a [nuevo tag] [sha1 del commit]` renombra el tag del commit pero deja el anterior tag.
* `git log` ver la lista de commits.
  * `--oneline` resumido.
  * `--graph` ver las ramificaciones.
  * `-[numero]` ver los ultimos [numero] commits.
* `git diff [sha1 del commit]` muestra la diferencias del commit [sha1].
* `git diff [sha1-1] [sha1-2]` diferencia entre la version 1 vs la version 2.
* `git reset`
  * `--soft [sha1]` borrar todos los commits posteriores a [sha1]. Los archivos que salen del repositorio son pasados al staging area.
  * `--mixed [sha1]` borrar todos los commits posteriores a [sha1]. Los archivos que salen del repositorio son pasados al working directory
  * `--hard [sha1]` elimina todos los cambios incluso del working directory. 

Si se desea eliminar el repositorio, solo hay que eliminar la carpeta oculta .git



### Múltiples entornos de trabajo 

* `git branch [nombre]` crear la rama [nombre]
* `git branch -l` lista las ramas
* `git branch -d [nombre]` elimina el branch [nombre]. Esto solo funciona si el branch no tiene ningún commit.
* `git branch -D [nombre]` fuerza la eliminación de un branch sin importar si tiene commits
* `git branch -m [nombre inicial] [nuevo nombre] ` renombra el branch [nombre inicial] por [nuevo nombre]
* `git checkout [brach]` moverse al branch [branch]
* `git chechout [sha1]` ir al momento del tiempo de ese commit
* `git checkout -b [nombre]` crea un branch y se mueva al mismo
* `git checkout -- [archivo]` descarta todos los cambios del archivo
* `git merge [branch]` mezcla el branch [branch] con el branch actual
* `git rebase [branch]` mezcla el branch con el brach actual. Es como el merge pero sin crear bifurcaciones
* **`git stash`** : Guarda el trabajo actual de manera temporal. (Archivos modificados o eliminados)*
* **`git stash -u `** : Crea un stash con todos los archivos. (Añadiendo los creados Untracked)
* **`git stash save “mensaje”`** : Crea un stash con el mensaje especificado.
* **`git stash list`** :Permite visualizar todos los stash existentes.
* **`git stash clear`** : Elimina todos los stash existentes.
* **`git stash drop`** : Elimina el stash más reciente. El que tiene num_stash=0.
* **`git stash drop stash@{num_stash}`** : Elimina un stash específico.
* **`git stash apply`** : Aplica el stash más reciente. El que tiene num_stash=0.
* **`git stash apply stash@{num_stash}`** : Aplica los cambios de un stash específico.
* **`git stash pop`** : Aplica el stash más reciente y lo elimina. El que tiene num_stash=0.
* **`git stash pop stash@{num_stash}`** : Aplica los cambios de un stash específico y elimina lo stash.
* **`git stash branch nombre_de_rama`** : Crea una rama y aplica el stash mas reciente.
* **`git stash branch nombre_de_rama stash@{num_stash}`** : Crea una rama y aplica el stash especificado.
* `git cherry pick [sha1]` mover el commit [sha1] de otro branch al branch actual
* **`git clean --dry-run`**: Para saber qué archivos vamos a borrar cuando estan repetidos o no son de nuestro proyecto
* **`git clean -f`**: Para borrar todos los archivos listados (que no son carpetas y lo que esta en .gitignore)



##  Recuperar ramas borradas (Git)
* **`git reflog`**: Para recuperar una rama que haya sido eliminada necesitamos el hash ultimo commit hecho en dicha rama. Para eso   usamos git reflog. Buscamos el hash y lo copiamos. ej: git checkout -b cabecera hash_del_utlimo_commit_de_cabecera
Ya habiendo obtenido el hash lo que hacemos sera volver a crear la rama pero le agregamos el hash al final.



## comandos especiales (Git)
* **`git shortlog`**: Ver cuantos commits a hecho los miembros del equipo
* **`git shortlog -sn`**: Las personas que han hecho ciertos commits
* **`git shortlog -sn --all`**: Todos los commits (también los borrados)
* **`git shortlog -sn --all --no-merges`**: muestra las estadisticas de los comigs del repositorio donde estoy
* **`git config --global alias.stats “shortlog -sn --all --no-merges”`**: configura el comando “shortlog -sn --all --no-merges” en un Alias en las configuraciones globales de git del pc
* **`git blame -c blogpost.html`**: Muestra quien ha hecho cambios en dicho archivo identado
* **`git blame --help`**: Muestra en el navegador el uso del comando
* **`git blame archivo -L 35, 60 -c`**: Muestra quien escribio el codigo con informacion de la linea 35 a la 60, EJ: `git blame css/estilos.css -L 35, 60 -c`
* **`git branch -r`**: Muestra las Ramas remotas de GitHub
* **`git branch -a`**: Muestra todas las Ramas del repo y remotas de GitHub 




## Repositorios Remotos (Github)

* `git clone [ruta]` trae el repositorio a la computadora
* `fork` hace una copia de un repositorio externo a nuestra cuenta
* `ssh-keygen -t rsa -b 4096 -C "correo@ejemploc.com"` crea una llave ssh. El correo debe de ser el mismo que se encuentra en Github
* `git remote add [nombre] [ruta]` conecta un repositorio remoto con uno local. Por defecto el nombre es origin
* `git remote -v` lista las conexiones remota
* `git remote remove [nombre]` remueve una conexión remota
* `git fetch [nombre] [branch]` traer . Solo los trae pero no lo mezcla
* `git merge [origin/master] --allow-unrelated-histories` hace un merge del fetch con el repositorio local
* `git pull [origin] [branch]` hace un fetch mas merge
* `git push [origin] [master]` envia al repositorio local al remoto
  * `--tags` enviar los tags
* `git push --all origin` push a todos los branch y tags


## Ignorar archivos

Para ignorar archivos o carpetas de los commits se crea un archivo que se llame `.gitignore`.

Página que crear .gitignore para los proyectos:
https://www.gitignore.io/
