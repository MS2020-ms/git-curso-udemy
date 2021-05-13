# Repositorio GitHub
- Crear repositorio en GitHub
- Subir mi repositorio a GitHub
  HTTPS
  SSH [mas seguro]

    >git remote add origin https://github.com/MS2020-ms/git-curso-udemy.git
    >git branch -M main
    >git push -u origin main

>git remote [ver ramas en GitHub]
>git remote -v [ver mi fetch y mi push]

# Markdown
https://www.markdowntutorial.com/
https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf
https://www.webfx.com/tools/emoji-cheat-sheet/

# Subir tags
>git push --tags

# Pull
En GitHub ir archivo README.md y con "lapiz" = editar
Hago cambios
Hago comentario
Commit changes
>git pull o >git pull origin main
>git lg
>git log [ver todos commit]

# Fetch
1. En GitHub-Repo Remoto ir archivo heroes.md y con "lapiz" = editar
Hago cambios
Hago comentario
Commit changes
2. En VSCode-Repo Local hago cambios en archivo README.md
>git s
>git commit -am "Cambios en archivo README.md"
>git s
>git push => rejected!!!
3. Hacer fetch, porque no puede hace merge automaticamente
>git fetch [compara los dos repositorio]
>git pull
>git push [para que suba los cambios]

##### GITHUB

# Clonar repositorio de GitHub
En GitHub:
Code
Clone -> url https://github.com/MS2020-ms/git-curso-udemy.git
En Terminal:
Me situo en carpeta donde quiero clonar el repo
>git clone https://github.com/MS2020-ms/git-curso-udemy.git
>git clone https://github.com/MS2020-ms/git-curso-udemy.git demo-10 [con nombre especifico]

# Github:
Ir repositorio -> ir archivo -> Raw | Blame | History
Raw : codigo en crudo
Blame : historial de cambios sobre el archivo
History : historial de commits
## Crear nuevo archivo en GitHub: creando nueva rama, merge a main y bajar a repo local
Add File - Create new file
Commit
[x]Create a new branch and start a pull request
Propose new file
-> Open a pull request (solicitud antes de realizar cambios definitivos)
   titulo y comentario
   Create pull Request
     -> This branch has no conflicts with the base branch
        Merge pull request [Create a merge commit]
        Confirm merge
        Delete branch
---
>git pull
## Crear nuevo archivo en GitHub: creando directamente en main y bajar a repo local
Add File - Create new file
Commit
[x]Commit directly to the main branch. 
---
>git pull
---
>git fetch [actualiza referencia locales y remotas]
>git status
>git pull
>git lg

# Fork y Clone
## Fork
ir a repositorio -> boton Fork [crea un repo en mi github]
## Clone de mi repo remoto en Github a mi repo local en PC
Ir a repositorio -> clone
copiar http
>git clone https://github.com/MS2020-ms/legion-del-mal.git demo-12
>git s
>git lg
Hacemos cambios en un archivo
>git commit -am "Borramos a scarecrow"
>git push

# Pull Request
>git remote -v
Hacemos cambios en un archivo
>git add .
>git commit -m "Solicitud de MS2020-ms"
>git s
>git push
En GitHub Pull Request -> new pull request -> create pull request: titulo y comentario -> create pull request

# Actualizando Fork = upstream
Hacemos modificacion en archido de repo de Github -> lapiz=editar
Commit changes
Create a new branch
Propose file changes
Crear un Pull-Request
>git remote add upstream [url del repositorio = como un clone]
>git pull upstream master
:wq
>git push

# Flujos de trabajo
A. En base a Forks
B. Un solo Repositorio = Ramas por usuario (features branch)
   >git fetch
   >git branch -a [listado de ramas]
   >git checkout rama-capitan [pasarme a rama de otra persona]
   ---
   >git checkout master
   >git merge rama-capitan
   >git push
   or
   >git push origin rama-silver
   Hacer Pull-Request

# Features Branch - Flujo de trabajo mediante pull request
Sobre un nuevo repositorio en Github y nuevo proyecto-repo local
>git init
>git status 
>git add .
>git commit -m "Primer commit"
---
Subir mi repositorio local a GitHub
  HTTPS
    >git remote add origin https://github.com/MS2020-ms/git-curso-udemy.git
    >git branch -M main
    >git push -u origin main
---
Hago modificaciones y creo una nueva rama:
>git checkout -b rama-villanos
>git add .
>git commit -m "Added archivo de villanos"
>git checkout main [en esta rama no existe el archivo de villanos.md]
>git checkout rama-villanos
Subir mi repolocal a GitHub:
>git push origin rama-villanos

En GitHub:
Ir a branches(2)
Tocar sobre rama-villanos
Ir a Pull Request -> new pull request
Compare changes base:main <- compare:rama-villanos
Split
Create pull request
Mensaje: bla,bla,bla...
Create pull request
---
Merge pull request
Titulo y comentario
Confirm merge
Delete branch - borrar rama-villanos
Ir Pull Request (arriba) -> 0 Open 1 Closed
Ir Code (arriba)

En repo local: 
Borrar rama-villanos
>git checkout main
>git branch -D rama-villanos
Bajarme cambios a rama main
>git pull

# Features Branch - Revisando el trabajo de otros companeros
Ir GitHub: (crear rama = companero)
Branch: master -> crear nueva rama -> create branch: rama-misiones from main -> Branch: rama-misiones
Creo nuevo archivo en esa rama -> commit -> Commit new file
Si regreso Branch: master, no tengo el arvicho creado
---
Ir mi repo local: (yo)
>git pull o >git pull --all
>git branch -a [para ver todas las ramas, incluyendo las remotas]
>git checkout rama-misiones
>git s
Realizo cambios en el archivo:
>git commit -am "Integrado nuevas misiones en archivo misiones.md"
Subo a repo en Github:
>git push origin rama-misiones
Ir Github:
Compare & pull request -> create pull request -> Merge pull request -> Confirm merge [Ya tenemos mergeado de rama-misiones a main el archivo]
Borrar ramas antiguas en local y remoto:
>git branch -a
>git checkout main
>git branch -D rama-misiones
>git pull
---
>git push origin :rama-misiones
>git push origin :rama-villanos [ya estaba borrado en origin - Error]
>git remote prune origin
>git branch -a

# Tags y subirlos a GitHub
>git lg
>git tag -a v1.0.0 -m "Version 1 lista para produccion"
>git tag
>git tag -a v0.0.0 b0ce726 -m "Version alpha = No usar" [tag de un commit anterior - con hash]
>git tag -a v0.0.1 272355d [Para hacer comentario mayor]
a [para empezar agregar]
esc :wq
---
>git push --tags
Ir a GitHub -> 3 tags

# Rama de produccion GitHub
Creamos nueva rama para cambios en la ultima version
>git checkout -b rama-capitan-mad
>git s
>git commit -am "Arreglos sobre archivos miembros y villanos"
>git push origin rama-capitan-mad
>git tag v1.0.1 -m "Arreglo urgente"
>git push --tags
Vuelvo a hacer cambios en esos archivos
>git s
>git commit -am "Se modificaron los areglos anteriores"
>git push origin rama-capitan-mad
Ir Github:
Compare & pull request -> create pull request -> Rebase and merge -> Confirm rebase and merge [Ya tenemos mergeado de rama-capitan-mad a main el archivo]
Rebase: es como si lo huesemos hecho todo en el main, los commit se guardan en main!
---
Borrar ramas:
>git branch -a
>git checkout main 
>git branch -D rama-capitan-mad
>git push origin :rama-capitan-mad

# Releases - Versiones de produccion completas
Pasar tags a release: [version de produccion] Mas informacion y se puede anadir archivos o imagenes a la descripcion del release
Ir a tag -> Edit tag -> Titulo-Descripcion-Anadir archivos o imagenes -> This is a pre-release [no lista para produccion] -> Publish release
Edit -> quitar el pre-release

# Issues y MileStones - Adminsitrar proyectos
Ir GitHub Issues -> New issue - titulo, descripcion -> Submit new issue
Creado el Issue, puedo responder con comentarios o unsubscribe [para no recibir mails con cada comentario]
Close issue y Reopen issue - Lock conversation [cerrarlo definitivamente] y Unlock conversation
>git pull
Hago los cambios en el archivo según issue
>git s
>git commit -am "Agragamos a Hulk fixes #4" [fixes #4: cerrar y  anexarlo al issue] = [closes o resolves]
>git push
Puedo Reopen issue

# Labels - Etiquetas para issues
Issues - Labels - Edit labels - New label - Create label
Cuando creo nuevo Issue puedo aplicarle labels
# Milestones
Crear nuevo Issues - Milestones [Beta-Octubre]
Ir Issues - Milestones [issues que tienen que ver con Beta-Octubre]

# Agregando colaboradores a un repositorio
Ir GitHub
Settings -> Manage access - invitar colaborador por username

# Asociando commits a issues
Creo nuevo Issue [#9]
Code - archivo - History - commits que afectaron a ese archivo - hago un commit "El archivo se resolvio #9" - Referencia al issue (si la toco me lleva al issue)

# Wiki - informacion del repositorio (contenido) - publica
Ir a Wiki -> Create new page - Home -> Save page
Crea un url unico: https://github.com/MS2020-ms/avengers/wiki
Crear link a page Instalacion -> edit ### Instalacion - icono link - link text:instalacion url:instalacion

Create new page - Instalacion
Crea un url unico: https://github.com/MS2020-ms/avengers/wiki/Instalacion
Privada: settings / features / Restrict editing to collaborators only [x]

# Projects - pizarra o dashboard (gestor de projectos)
Create a project
Crea un url unico: https://github.com/MS2020-ms/avengers/projects/1
Add a column - Por hacer -> + [anadir notas] -> ... Convert to issue -> Add task list [x]
Add a column - Pendientes
Add a column - En Progreso
Add a column - Terminados
+ Add cards -> arrastrar issues a las columnas

# GitHub Pages
MS2020-ms.github.io
https://ms2020-ms.github.io/
>git clone https://github.com/MS2020-ms/MS2020-ms.github.io.git demo-14-pages
## Para proyectos
En VSCode ir proyecto (avengers = demo-13). 
Crear carpeta docs/index.html
>git s
>git add .
>git commit -m "Agragado docs/index.html"
>git push
Ir GitHub
Settings - GitHub Pages - Source branch: main/docs - save
Your site is published at https://ms2020-ms.github.io/avengers/
Si tengo ya una carpeta docs, puedo crear otra rama en GitHub "gh-pages" en esa rama gurado mi docs/index.html

# Insights (actividad e info del repositorio)
Pulse, traffic, Code frecuency y Network

# Organizacion de Equipos
Crear una organizacion: arriba derecha + New organization
name/email/free-Create organization
invite members
## Transfiriendo el dominio de un repo a una organizacion
Ir al perfil donde tengo el repositorio ms2020-ms y repositorio a tranferir
Settings - Danger Zone - Transfer ownership
Pierdo el repo de mi cuenta, para recuperarlo, hacerle un fork desde la organizacion
## Teams - equipos de trabajo
Teams - create a new team - name(desarrolladores)/description(este es el equipo de desarrollo)
Quien crea el equipo = administrador del equipo
Add members
Teams - create a new team - name(desarrolladores Jr.)/description(este es el equipo apoyo)/Parent team
Teams - create a new team - name(soporte tecnico)/description(este es el equipo tecnico)/Parent team (equipo hijo de desarrolladores padre)
Teams - create a new team - name(testers)/description(este es el equipo pruebas)/Parent team 
## Asignar repositorios a los equipos
Ir teams - desarrolladores (lista de miembros) - Repositories (asigno repositorios que este equipo puede trabajar) Add repository (solo a los que tiene acceso o he Transfirido el dominio de un repo a una organizacion) seleccionar Read-Write-Admin.
Ir teams - desarrolladores|soporte tecnico|testers -> Write
## People
2FA - Autenticacion
Private (solo visible para miembros de la organizacion)
Member o Owner
Settings (puedo cambiar role, eliminar de la organizacion o convertir en colaborador externo)

# Ajustes y Seguridad
## Ajustes de organizaciones
Settings:
Profile= name/email/description/url/gravatar - Update profile - Upload new picture - Rename organization y Delete organization.
Blocked users
## Ajustes de usuarios de GitHub
Perfil v Settings
## 2FA - Autenticacion de doble factor
Perfil v Settings
Account security - Two-factor authentication - password de Github - set up using an app
Scanear barcode [movil bajar app Google Authenticator] -metodo codigo y continue
Download los codigos 
Enable two factor authentication
## Generando un token de acceso personal
Perfil v Settings
Developer settings
Personal access tokens - Generate new token
note: token-gist - [x]gist -Generate token -> edit =  regenerate token
## Generando una clave SSH para Windows
ir a C:\Users\Besitzer - boton derecho Git Bash hier
>ls .ssh [para ver si ya existe el directorio ssh]
>mkdir .ssh
>cd .ssh
>ssh-keygen -t rsa -C "msotomail@gmail.com"  
enter
passphrase: [palabra clave]
enter
ir a C:\Users\Besitzer\.ssh -> archivo id_rsa.pub
Abrir editor de windows y arrastar archivo = clave ssh [que debemos subir a GitHub]
## Verificando conexion SSH
Con las claves SSH, te puedes conectar con GitHub sin suministrar tu nombre de usuario ni contraseña en cada visita.
Perfil v Settings
SSH and GPG keys - New SSH key - Title: EliteBook MS - Key - Add SSH key
Ir a C:\Users\Besitzer - boton derecho Git Bash hier
>ssh -T git@github.com
Crearme un clone de un repositorio via SSH:
En Github voy a repo - Code v Clone SSH - git@github.com:MS2020-ms/avengers.git
>git clone git@github.com:MS2020-ms/avengers.git demo-15

# GIST
Coleccion de codigos = micro-reposiitorio, se pueden compartir con otros users
Instantly share code, notes, and snippets.
## Creando un Gist
+ v New gist - nombre (HTML Codigo Basico) - extension (index.html)
Create secret/public gist
Crear comentarios
Lo puedo usar como un script <script src="https://gist.github.com/MS2020-ms/8f48c4ca0929ab505c65190f7abe9ea8.js"></script>
Lo puedo usar como url https://gist.github.com/MS2020-ms/8f48c4ca0929ab505c65190f7abe9ea8
## Usando plugings de Gist con tokens personales
+ v New gist - nombre (JavaScript: Simple console.log) - extension (app.js)
Create secret/public gist
Perfil v Settings
Developer settings - Personal access tokens - Regenerate token
No terminado...