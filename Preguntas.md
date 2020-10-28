# Las 10 preguntas y respuestas mas interesantes sobre GITHUB

## `1. Pregunta/Respuesta`

- Pregunta: Acabo de hacer un commit:

git commit -m "este es un comentario"

Sin embargo, de repente me he dado cuenta de que este mensaje no es el correcto. ¿Puedo modificarlo? Si sí, ¿cómo?

Si vuelvo a escribir git commit -m "un nuevo comentario" hará otro commit en lugar de modificar el que ya hice.

- Solucion: La opción más práctica y rápida es usar:

git commit --amend

Tras lo cual se te abrirá el editor para que puedas modificar el mensaje.

Si quieres escribir algo totalmente nuevo, puedes decir directamente:

git commit --amend -m "Este es el nuevo comentario"

## `2. Pregunta/Respuesta`

- Trabajo en un branch llamado master2, el asunto es que hice pequeños cambios en 1 archivo y al intentar subirlos, cometi un error e hice git pull origin master y al hacer push me aparecieron casi todos los archivos del repositorio con conflicto, intente resolverlos pero no hubo caso. Necesito volver a la ultima version estable del repositorio o si es que se puede, revertir los cambios o eliminar los commits

- Puedes volver a una revisión antigua usando checkout y pasando el hash del commit. Por ejemplo:

git checkout ab25f1ln2b4o3a9c4u1v6k4n1m7 .

No olvides el punto al final. También puedes descartar cambios mediante reset pasándole el numero de commits. Por ejemplo, para descartar los últimos 3 commits:

git reset --hard HEAD~3
La diferencia entre checkout y reset es que en éste último se descartan las revisiones, mientras que con checkout se preservan.

## `3. Pregunta/Respuesta` 

- Se que los tags existen, pero nunca los he usado y aun no me he encontrado con nadie que los use, ¿para qué se usan?

Por lo que pone en la documentación de Git, es una forma de crear un histórico de mensajes, paralelo al de los commits para marcar sólo los cambios más importantes, ¿es sólo eso? ¿tiene más usos?

- Sirven para dejar un registro, una marca de una versión en concreto. Se hacen cuando publicas una versión (v0.1, v1.0, v2.2, etc.) de modo que puedas volver a dicha versión por si tuvieras que probar alguna funcionalidad o error que suceda en esa versión

## `4. Pregunta/Respuesta`

- Uso doble autenticación con GitHub, por lo tanto uso un token que funciona como contraseña, pero en powershell bajo windows10, cada vez que ejecuto el comando git push o git flow publish me pide usuario y contraseña.

Tengo instalado el módulo Posh-Git y Git-Flow.

- Intenta con...

git config --global credential.helper wincred

Te solicitará las credenciales una vez y quedaran cacheadas para futuras operaciones.

## `5. Pregunta/Respuesta` 

- Recientemente cambiamos de SVN a GIT en el proyecto, con git commit se guardan los cambios que se han hecho localmente. Entonces, ¿para qué sirve git push?¿Cuál es la diferencia entre los comandos git push y git commit?

- git push es un comando que sube los cambios hechos en tu ambiente de trabajo a una rama de trabajo tuya y/o de tu equipo remota. Commit identifica los cambios hechos en dicho ambiente de trabajo. Si tu no haces un push de tus cambios, estos jamas se veran reflejados en tu repositorio remoto.

A nivel de trabajo git push trabaja a nivel de repositorio, es decir con tu repositorio remoto, mientras que git commit trabaja en tu repositorio local.

## `6. Pregunta/Respuesta` 

- Tengo un proyecto almacenado en un respositorio de bitbucket y necesito clonarlo hasta cierto commit, he intentado hacerlo de la siguiente manera:

git clone https://<usuario>@bitbucket.org/<repositorio> id_commit

- 1.- Clonar el repositorio desde el branch deseado

git clone https://<usuario>@bitbucket.org/<repositorio> id_commit
2.- Recuperar el commit especifico

git fetch origin <sha1-del-commit> 
3.- Resetear el branch hasta el commit deseado

git reset --hard FETCH_HEAD

## `7. Pregunta/Respuesta` 

- En git al hacer un push si las ramas local y remota no concuerdan es necesario hacer un force push (aunque no sea bien visto hacer un force push). En git hay dos opciones para esto la opción --force y la opción --force-with-lease.

Por el nombre parece que --force-with-lease es menos agresivo o no siempre hace el push pero quisiera saber cual es la diferencia entre estas dos opciones.

- Git push --force es destructiva porque incondicionalmente sobrescribe el repositorio remoto con lo que tenga a nivel local, posiblemente sobrescribir cualquier cambio que un miembro del equipo ha empujado, lo cual puedes borrar los cambios de algún miembro. Sin embargo hay una manera mejor la opción --force-with-lease la cual es la mejor recomendada puede ayudar cuando se necesita hacer un empuje forzado pero todavía asegurarse de no sobrescribir el trabajo de otros.

## `8. Pregunta/Respuesta` 

- Me está trayendo por el camino de la amargura...Al intentar instalar Git me salta el siguiente error que no sé cómo solucionar. Cualquier sugerencia es bienvenida. Gracias!

marlena@marlena-K55VD:~$ sudo apt-get install git
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes adicionales:
  git-man liberror-perl
Paquetes sugeridos:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-cvs git-mediawiki git-svn
Se instalarán los siguientes paquetes NUEVOS:
  git git-man liberror-perl
0 actualizados, 3 nuevos se instalarán, 0 para eliminar y 4 no actualizados.
Se necesita descargar 22,8 kB/4.733 kB de archivos.
Se utilizarán 33,9 MB de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] S
Ign:1 http://es.archive.ubuntu.com/ubuntu bionic/main amd64 liberror-perl all 0.17025-1
Err:1 http://es.archive.ubuntu.com/ubuntu bionic/main amd64 liberror-perl all 0.17025-1
  409  Conflict [IP: 104.19.139.75 80]
E: Fallo al obtener http://es.archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17025-1_all.deb  409  Conflict [IP: 104.19.139.75 80]
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar «apt-get update» o deba intentarlo de nuevo con --fix-missing?

- A mí me pasó lo mismo; lo resolví cambiando los repositorios en /etc/apt/sources.list

En mi caso, sustituí todos los repositorios que empezaban por es. y utilicé los de Estados Unidos, por ejemplo, cambié:

deb http://es.archive.ubuntu.com/ubuntu/ bionic main restricted
por

deb http://archive.ubuntu.com/ubuntu/ bionic main restricted

## `9. Pregunta/Respuesta` 

- me surgió la duda, ya que encontré en una librería que descargue un archivo .gitkeep, el cual se encontraba vació. Aunque estuve buscando en la documentación de GIT no pude encontrar el uso del mismo.

Alguien sabe si se usa para algo o solo fue creada por el autor sin un fin especifico.

- Si creas una nueva carpeta en un proyecto bajo control de versiones con Git, veras que al hacer un git status, no aparece, mientras está vacía.

Una forma de añadir cartetas vacías en tu repositorio sería añadir un fichero en su interior. Por convenio se usa un .gitkeep, por eso no es un fichero 'oficial' de Git, y si quieres puedes poner un fichero llamado '.pepito-palotes' (o el que te de la gana, aunque el primero se este imponiendo).

## `10. Pregunta/Respuesta`

- En mi entorno de trabajo tenemos la etiqueta "production" para marcar siempre la última versión que está en producción. La creamos a mano al hacer una release y, por tanto, va cambiando periódicamente.

Lo que ocurre después es que cuando hago un git pull en local mi etiqueta "production" no apunta al mismo sitio que la que hay en remoto, por lo que me sale el mensaje de error:

! [rejected]          production -> production  (would clobber existing tag)
Es decir, git me avisa de que rechaza esto porque machacaría la etiqueta ya existente.

¿Cómo puedo hacer para que el git pull funcione correctamente sin recibir este mensaje de error? Leí que se puede hacer git fetch --tags -f, lo que fuerza el "pull" de las etiquetas, sobreescribiendo las que estén en local. ¿Pero puede hacerse todo en un único comando?

- Hay que tener en cuenta lo que dice la documentación sobre git pull

git-pull - Fetch from and integrate with another repository or a local branch ... Incorporates changes from a remote repository into the current branch. In its > default mode, git pull is shorthand for git fetch followed by git merge FETCH_HEAD

Con lo cual te está diciendo que git pull es lo mismo que git fetch

Y con ello podemos entender que git pull --tags -f te forzará bajar los tags de la misma forma que lo harías con git fetch --tags -f

-f, --force When git fetch is used with : refspec it may refuse to update the local branch as discussed in the part of the git-fetch(1) documentation. This option overrides that check.