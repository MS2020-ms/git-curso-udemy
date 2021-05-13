# Git y GitHub

# Comandos Ayuda
>git --version
>git help
>git help commit [detalle sobre comando commit]
# Configuracion
>git config --global user.name "Miguel"
>git config --global user.email "ms@gmail.com"
>git config --global -e [dice los datos anteriores user y email]
>:q [Salir]

# Web de Prueba
http://www.initializr.com/
Bootstrap->Download it!

# Comandos Basicos
>git init
>git status 
>git add .
>git commit -m "Primer commit"
---
>git commit -am "Primer commit" [anade todos archivos al stage y hago commit]

# Commit
>git commit
terminal: Escribo commit... + esc + :wq + ENTER

# Recuperar estado de ultimo commit de todo el proyecto
>git checkout -- .

# Listado commits y Hash [id]
>git log
>git log --oneline [hash corto]
>git log --oneline --decorate --all --graph [hash corto por ramas]

# Status
>git status -s [status corto] modo silence
>git status -s -b [status corto y branch] = >git status -sb

### Si da error con CRLF
>git config core.autocrlf true

# Agregar

>git add -A => stages all changes

>git add .  => stages new files and modifications, without deletions (on the current directory and its subdirectories).

>git add -u => stages modifications and deletions, without new files
----
>git add "*.txt" [de todo el proyecto]
>git add *.txt [de directorio actual]
>git add --all [todos los archivos] = >git add -A
>git add <lista de archivos> [lista archivos entre espacios]
>git add pdfs/ [toda la carpeta pdfs]
>git add pdfs/*.pdf [todos los archivos con extension .pdf dentro de carpeta pdfs]
----
# Agregar un archivos al stage
>git add index.html [solo este archivo]
>git status
>git commit -m "Se creo archivo index.html"
# Agregar todos archivos con extension .png al stage
>git add *.png
>git status
>git commit -m "Add imagenes png"
# Agregar carpeta al stage
>git add css/
>git status
>git commit -m "Add carpeta css"
# Agregar todos archivos y Excluir uno al stage
>git add -A [anade todos]
>git reset *.xml [excluye archivos .xml]
>git status
>git commit -m "Add archivos JS y Fuentes"

# Alias para comandos, de forma global
>git config --global alias.lg "log --oneline --decorate --all --graph"
>git lg
---
>git config --global alias.s "status -s -b"
>git s
---
>git config --global -e [ver nuestros alias]
>git config --global -l [ver nuestros alias. No en modo escritura]

# Restauracion de archivos
## Ver los cambios en los archivos en terminal - Comparar
>git diff [solo se visualiza la primera vez]
>git diff --staged [se visualiza siempre]
## Sacar archivo del stage
>git reset HEAD README.md
>git s
## Revertir cambio - Vuelve al anterior commit de un archivo
>git checkout -- README.md
>git s

# Corregir mensajes de commit y Revertir commit
>git commit --amend [en terminal modo escritura]
terminal: Escribo correccion de commit... + esc + :wq + ENTER

>git commit --amend -m "Actualizados readme" [corregir ultimo commit]
---
>git reset --soft HEAD^ 
HEAD = Ultimo commit / HEAD^ = commit anterior

>git lg
>git reset --soft a8ee6cc [Hash del commit donde quiero revertir]
>git s
>git add .
>git commit -m "Agragamos a Linterna Verde y Robin a heroes"
>git lg

# Viajes en el tiempo - reset  
Se quitan del stage pero aun contienen las modificaciones:
>git reset --soft a8ee6cc [Hash del commit donde quiero revertir]
>git reset --mixed e6dd495 

Se quitan del stage pero y elimina archivos del proyecto:
>git reset --hard e6dd495 

## Regresar a un punto anterior - Recuperar - reflog + reset
>git reflog [Listado de commit en linea de tiempo]
>git reset --hard ef17d63 [Me muevo en la linea del tiempo]
>git lg

# Cambio de nombre archivo mediante GIT
>git mv destruir-mundo.txt salvar-mundo.txt
>git commit -m "Renombrando archivo a salvar-mundo.txt"
>git lg

# Eliminar archivo mediante GIT
>git rm salvar-mundo.txt
>git commit -m "Borrado archivo salvar-mundo.txt"
>git lg

# Cambio de nombre archivo y Eliminar archivo fuera de GIT
Cambio nombre manualmente:
>git s
>git add -u [actualizar todo]
>git s
>git add -A
>git s
>git commit -m "Cambiado nombre de archivo superman.md"
>git lg
Elimino archivo manualmente:
>git s
>git add -u
>git s
>git commit -m "Eliminado archivo batman.md"
>git lg

# Ignorando archivos que no deseamos
.gitignore
>git add -A
>git commit -m "Add file .gitignore"

#####

# Ramas, Uniones-(Merge) y Conflictos
## Merge: Fast-Forward (no habia cambios en master)
Crear nueva rama:
>git branch rama-villanos
>git branch [para ver lista ramas]
Moverme a rama-villanos:
>git checkout rama-villanos
>git branch
Archivo cambios al stage:
>git add -A
>git commit -m "Add archivo villanos"
>git s
>git lg [HEAD en rama-villanos]
Mergear rama-villanos a Master:
>git diff rama-villanos master [ver diferencias]
>git checkout master [mover a rama master]
>git merge rama-villanos 
>git lg [HEAD en master y rama-villanos]
Borrar rama-villanos:
>git branch -d rama-villanos
>git branch
## Merge automatico (los cambios en master y en rama-villano no entran en conflicto - cambios en distintos archivos)
Crear y Moverme a nueva rama:
>git checkout -b rama-villano
Archivo cambios en rama-villanos al stage:
>git commit -am "Add cambios en lista villanos + Doom"
>git s
Mover a master:
>git checkout master
Archivo cambios en master al stage:
>git commit -am "Borrados heroes de Marvel"
>git s
>git lg
Mergear rama-villanos a Master:
>git merge rama-villano
>git lg
Borrar rama-villano:
>git branch -d rama-villano
>git branch
## Merge con conflictos
Crear y Moverme a nueva rama:
>git checkout -b rama-conflicto
Archivo cambios en rama-conflicto al stage: (mismo archivo)
>git commit -am "Modificado misiones"
>git s
Mover a master:
>git checkout master
Archivo cambios en master al stage: (mismo archivo)
>git commit -am "Actualizamos misiones en master"
>git s
Mergear rama-villanos a Master:
>git merge rama-conflicto
CONFLICTO:
En VSCode ir archivo en rojo y borro lo que no quiero y me quedo lo que si quiero
>git s
>git commit -am "Resolviendo conflictos"
>git lg
Borrar rama-conflicto:
>git branch -d rama-conflicto
>git branch

###

# Tags - Etiquetas [marcar versiones o releses del app]
>git tag superRelease [crear tag]
>git tag [ver lista tags]
>git tag -d superRelease [borrar tag]
---
>git tag -a V1.0.0 -m "Version 1.0.0" [crear tag y comentario]
>git tag
>git lg
---
Crear un tag a un commit anterior => copiar el hash del commit:
345d7de
>git tag -a V0.1.0 345d7de -m "Version alpha"
>git tag
>git lg
---
Ver informacion-comentarios fel tag
>git show V0.1.0

###

# Git Stash  (Area Temporal) 
WIP WorkInProgress = dejar trabajo temporalmente en espera sin commitear y no perder cambios
>git stash [creo stash] o >git stash save
>git lg
>git stash list
Ahora hago modificaciones en un archivo
>git commit -am "Modificaciones en README de emergencia"
>git lg
Resuelto la entrega urgente. Volver al estado donde hice el Stash
>git stash pop [recupero punto de trabajo y elimina el stash]
>git s
>git commit -am "Agregamos lista de misiones"
>git lg [ya no existe stash]
## Git Stash con Conflictos 
>git stash o >git stash save
Ahora hago modificaciones en mismo archivo donde yo tenia otros cambios antes del stash
>git commit -am "Cambios de mergencia en el README"
>git lg
Resuelto la entrega urgente. Volver al estado donde hice el Stash
>git stash pop
En VSCode ir archivo en rojo y borro lo que no quiero y me quedo lo que si quiero o acepto cambios entrantes
>git s
>git commit -am "Retomando el trabajo guardado en STASH"
>git lg
Pero todavia existe el stash
>git stash drop [elimina el stash]
>git stash list
>git lg
## Git Stash - varios stash -> recuperar una entrada en particular (id)
>git stash apply stash@{1}
>git stash drop stash@{1} [elimina el stash]
---
>git stash list --stat [informacion de cada stash]
>git show stash [mas informacion de ultimo stash]
>git show stash stash@{1} [mas informacion un stash en prticular - por id]
---
Mensaje en los stash, para identificarlos mejor
>git stash save "Agragamos a Loki en los villanos"
---
Borrar todos los stash
>git stash clear

###

# Git Rebase (traer commits de master a mi rama de trabajo)
Se crea area temporal. Mueve los commits de la rama-misiones a ese area. Mueve la rama-misiones a el ultimo commits de la rama master. Regresa los commits del area temporal a la rama-misiones

>git checkout rama-misiones-completadas [mover a la rama]
>git rebase master
>git lg
Unir rama-misiones-completadas a master
>git checkout master
>git merge rama-misiones-completadas
>git lg
Borrar rama-misiones-completadas
>git branch -d rama-misiones-completadas 
---
## Rebase Squash (Unir dos commits)
>git rebase -i HEAD~4 [4 = ultimos 4 commits]
En terminal editar:
    pick 158ba9e Se agrego a la liga: Volcán Negro
    pick 422216b Agregamos el archivo de las misiones completadas
    pick 365c270 Actualizamos dos misiones completadas al momento
    squash 698b584 Actaulizadas las misiones completadas
Esto fusiona el ultimo con el anterior
>esc
>:wq [Guardar y Salir]
En terminal editar mensaje de commit:
    # This is the 1st commit message:
    Actualizamos la informacion de las misiones completadas
>esc
>:wq [Guardar y Salir]
>git lg
---
## Rebase Reword (Modificar titulo de commit)
>git rebase -i HEAD~1
En terminal editar:
    reword 5ffc4c6 Actualizamos la informacion de las misiones completadas (titulo anterior)
>esc
>:wq [Guardar y Salir]
En terminal editar:
    Updated misiones completadas (nuevo titulo)
>esc
>:wq [Guardar y Salir] 
>git checkout master
---
## Rebase Edit (Separar un commit en dos commits)
>git rebase -i HEAD~2 
En terminal editar:
    pick 1076df8 Updated: misiones completadas
    edit 80ef28d commits
>esc
>:wq [Guardar y Salir] 
>git reset HEAD^
>git add README.md
>git commit -m "Actualizaciones al readme"
>git add villanos.md
>git commit -m "Actualizaciones los villanos"
>git rebase --continue
>git lg
---
Rebase interactivo:
>git rebase -i HEAD~3 [3 = numero de commits que quiero]
Se crea area temporal. Mueve los commits de una rama a ese area. Se actua sobre los commits. Regresa los commits del area temporal a la rama.
Sirve para: Ordenar commits, Corregir mensajes de commits, Unir commits o Separar commits