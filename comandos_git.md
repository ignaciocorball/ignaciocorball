# Comandos de Git

## Configuración de Git

- Configurar nombre de usuario:
```sh
$ git config --global user.name "name"
```
- Configurar correo electrónico:
```sh
$ git config --global user.mail "mail@mail.com"
```
- Para ver configuracion de git:
```sh
$ git config --global -e
```

## Iniciar repositorio:
- Iniciar un nuevo repositorio:
```sh
$ git init
```
- Ver información del repositorio, archivos listos para hacer commit, y a qué rama pertenecen:
```sh
$ git status
```
- Agregar archivos para estar pendiente de los cambios:
```sh
$ git add .
```
- Hacer snapshot del proyecto:
```sh
$ git commit -m "primer commit"
```
Revertir cambios al ultimo commit:
```sh
$ git checkout -- .
```
- Revisar historial del repositorio actualmente:
```sh
$ git log
```
- Agregar todos los archivos en el directorio actual con extension .png:
```sh
$ git add *.png
```
- Agregar en el directorio actual, solo directorio:
```sh
$ git add css/
```
- Agregar todo lo que nos queda:
```sh
$ git add -A
```
- Quitar uno de los agregados:
```sh
$ git reset *.xml
```
- Agregar todos los archivos que modificamos en el proyecto: 
```sh
$ git add "*.txt"
```
Agregar todos los archivos:
```sh
$ git add --all
```
- Agrega los pdfs dentro de la carpeta pdfs
```sh
$ git add pdfs/*.pdf
```
- Si muestra warnings a la hora de add arcvhivos:
```sh
$ git config core.autocrlf true
```
- Log resumido:
```sh
$ git log --oneline
```
- Muestra log resumido y vistoso: 
```sh
$ git log --oneline --decorate --all --graph
```
- Muestra status resumido:
```sh
$ git status -s
```
- Muestra status resumido con la rama que estamos:
```sh
$ git status -s -b
```
- Para crear un alias personalizado(lg es como lo llamare | esto se llama como "git lg"):
```sh
$ git config --global alias.lg "log --online --decorate --all --graph"
```
- Ver configuraciones sin poder editar:
```sh
$ git config --global -l
```
- Cambios que hubieron en los archivos despues del commit:
```sh
$ git diff
```
- Ver todos los archivos del stage (los que hice add):
```sh
$ git diff --staged
```
- Sacar archivo de add del ultimo commit que hicimos (HEAD)
```sh
$ git reset HEAD README.md
```
- Volver cambios al primer commit
```sh
$ git checkout -- README.md
```
- Agregar y commit de todos los archivos:
```sh
$ git commit -am "Readme actualz"
```
- Cambiar mensaje del ultimo commit:
```sh
$ git commit --amend -m "Actualizamos el readme"
```
- Si queremos apuntar al commit que estaba antes del ultimo commit:
```sh
$ HEAD^
```
- Agregar cambio al penultimo commit que hicimos (o usando una ID):
```sh
$ git reset --soft HEAD^
```
- Volver a un commit:
```sh
$ git reset --mix b2b640d
```
- Borrar todos los commit posteriores del id:
```sh
$ git reset --hard b2b640d
```
- Muestra todos los cambios desde el inicio:
```sh
$ git reflog
```
- Para recuperar todo desde un id con el comando reflog:
```sh
$ git reset --hard a9df858
```
- Para cambiar nombre de un archivo con git (luego hacer commit):
```sh
$ git mv mundo.txt holamundo.txt
```
- Para eliminar archivo con git (luego hacer commit):
```sh
$ git rm holamundo.txt
```
- Para crear una nueva rama
```sh
$ git branch nuevarama
```
- Listar ramas
```sh
$ git branch
```
- Moverme de rama
```sh
$ git checkout namerama
```
- Para ver los cambios entre ramas
```sh
$ git diff nuevarama master
```
- Para unir rama a otra (la rama actual es a lo que se agregara lo de la otra rama)
```sh
$ git merge nuevarama
```
En este caso estoy parado en la master agregando lo de la "nuevarama"

- Para borrar una rama (es buena practica borrar la rama que se uso para merge)
```sh
$ git branch -d nuevarama
```
- Para crear una rama y moverme a ella
```sh
$ git checkout -b nuevarama
```
- Para crear un tag
```sh
$ git tag nombretag
```
- Listar todos los tags
```sh
$ git tag
```
- Borrar un tag
```sh
$ git tag -d nombretag
```
- Crear tag con comentario
```sh
$ git tag -a v1.0.0 -m "Version 1.0.0"
```
- Volver un commit a un tag (con el id)
```sh
$ git tag -a v0.0.1 345d7de -m "Version alfa"
```
- Ver informacion de un tag
```sh
$ git show nombretag
```
- Dejar codigo en reserva, los cambios quedaran como stash y se dejara todo como en el ultimo commit
```sh
$ git stash
```
- Listar todos los stash
```sh
$ git stash list
```
- Extrae los cambios pendientes de los stash (se borra el stash de los commits)
```sh
$ git stash pop
```
- Si hay conflicto al hacer stash, se debe corregir manual y borrar el stash, si no pongo indice solo se usara elstash@{0}
```sh
$ git stash drop stash@{2}
```
- Para aplicar solo un stash, si no pongo indice solo se usara elstash@{0}
```sh
$ git stash apply stash@{1}
```
- Mostrar informacion completa de los stash o con el indice
```sh
$ git stash show stash@{1}
```
- Mensajes en stash
```sh
$ git save "Agregamos a un nuevo stash"
```
- Borra todos los stash de raiz
```sh
$ git stash clear
```
- Pone todos los commits del master detras de la rama que se creo para hacer un merge forward
```sh
$ git rebase <rama>
```
- Revase en modo interactivo (-i) apuntando desde el ultimo commit (HEAD) hasta 4 commits (~4)
```sh
$ git rebase -i HEAD~4
```
Para tomar 2 commits y fusionarlos poner squash (s) delante del id del commit y se fusionara con el de arriba
Para cambiar un nombre de commit de manera interactiva, se debe usar el reword(r)

- Subir tags a github
```sh
$ git push --tags
```
- Resolver conflictos desde GitHub
```sh
$ git config --global pull.rebase true
```
- Para traer todos los cambios y la ramas desde GitHub (las ramas quedan como remoto)
```sh
$ git pull --all
```
- Para listar todas las ramas incluso las remoto (con un checkout me muevo a la rama remota)
```sh
$ git branch --all
```
- Actualiza (fetch) de ramas remotas, si borro una rama desde github. Usando este comando se limpiará la rama
```sh
$ git remote prune origin
```
- Recuperar rama productiva (v1.0.0), y un "-b" para ir a la rama borrada
```sh
$ git checkout nombre_tag
$ git checkout -b nombre-rama
```
- Clonar proyecto desde la rama que quiero
```sh
$ git clone -b NOMBRE_DE_LA_RAMA URL_DEL_REPOSITORIO
```
- Para subir una rama local a GitHub
```sh
$ git push -u origin rama-nueva
```