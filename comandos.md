# Apuntes GIT

## Codigos

- git init: iniciar el git

- git clone <url>: crea copia del repositorio en tu ordenador

- git git add . : el comando añade todos los archivos al área temporal

- git commit -m "Texto que identifique por que se hizo el commit"

- git push: con este comando se suben los archivos a github

- git branch: utilizado para mirar las ramas que tengas creadas

- push -u origin master: sube los archivos de tu rama principal (tu rama master) a la rama de origen de github (origin)

- doskey /history: una vez puesto este comando aparecerán todos los comandos que han sido utilizados en una lista

- git config: el siguiente comando se usa para establecer un email

- git version: sirve para ver que versión de git hay instalada.

- git branch "nombre": crea una nueva rama con el nombre elegido

- git rebase: recopila uno a uno los cambios confirmados en una rama, y reaplicarlos sobre otra

-  git log --online: sirve para ver los identificadores de los commit

- - git status -s: utilizado para saber que archivos no tienen seguimiento

## Recordatorios

### Crea un nuevo repositorio en la línea de comandos 

- echo "# NOMBREEjGithub1" >> README.md 
git init 
git agregar README.md 
git commit -m "first commit" 
git branch -M main 
git remote agregar origen https://github.com/git-youtube/NOMBREEjGithub1.git
 git push -u origen principal

 ### Enviar un repositorio existente desde la línea de comandos

 - git remoto agregar origen https://github.com/git-youtube/NOMBREEjGithub1.git
 git branch -M main 
git push -u origin main

### Importar código de otro repositorio

- Puede inicializar este repositorio con código de un proyecto de Subversion, Mercurial o TFS