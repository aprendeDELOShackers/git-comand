# Comandos útiles de "_*_git_*_"
				
					#----*Aprenderemos a usar comandos básicos de *git*-----
1. git init
2. git add <<fichero>>, git add <<carpeta>>, git add .
3. git commit -m "mesaje", git commit --amend -m "mensaje"
4. git status
5. git log, lo mas comunes son: --oneline, --graph
6. git show, git show <commit>
7. git annotate
8. git diff, git --cached, git diff HEAD
9. git checkout <commit> -- <file>, git checkout HEAD -- <file>.
10. git reset <fichero>
11. git reset <commit>, git reset --hard <commit>, git reset --hard HEAD
12. git branch <rama>
13. git checkout <rama>, git checkout -b <rama>
14. git marge <rama>
15. git branch -d <rama>, git branch -D <rama>
16. git remote add <repositorio-remoto> <url>
17. git remote, git remote -v
18. git pull <remote> <rama>, git fetch <remoto>
19. git push <remoto> <rama>
8. git checkout -b rama-heroes
9. git checkout master
10. git branch -d rama-heroes
11. git push
12. git commit -am 

#Estare explicando brevemente los comando de *git* y sus funcines.
--------------------------------------------------------------------
#Creación de repositorios
#Creación de un repositorio nuevo
	git init
					---------git init----------
git init <nombre-repositorio> crea un repositorio nuevo con el
nombre <nombre-repositorio>.
Este comando crea crea una nueva carpeta con el nombre del repositorio,
que a su vez contiene otra carpeta oculta llamada .git que contiene la
base de datos donde se registran los cambios en el repositorio.

-----------------------------------------------------------------------
#Añadir cambios a la zona de intercambio temporal
	git add
					-----------*git add*-------------
git add <fichero> añade los cambios en el chero <fichero> del
directorio de trabajo a la zona de intercambio temporal.
git add <carpeta> añade los cambios en todos los cheros de la
carpeta <carpeta> del directorio de trabajo a la zona de intercambio
temporal.
git add . añade todos los cambios de todos los cheros no guardados
aún en la zona de intercambio temporal.

----------------------------------------------------------------------------------------
#Añadir cambios al repositorio
	git commit
					--------git commit--------
git commit -m "mensaje" = confirma todos los cambios de la zona de
intercambio temporal añadiéndolos al repositorio y creando una nueva
versión del proyecto. "mensaje" es un breve mensaje describiendo los
cambios realizados que se asociará a la nueva versión del proyecto.

git commit --amend -m "mensaje" = cambia el mensaje del último
commit por el nuevo mensaje "mensaje".

------------------------------------------------------------------------
#Estado e historia de un repositorio
#Mostrar el estado de un repositorio
	git status
					------------git status----------
git status muestra el estado de los cambios en el repositorio desde la
última versión guardada. En particular, muestra los cheros con cambios
en el directorio de trabajo que no se han añadido a la zona de
intercambio temporal y los cheros en la zona de intercambio temporal
que no se han añadido al repositorio.

-----------------------------------------------------------------------
#Mostrar el historial de versiones de un repositorio
	git log
				----------------git log---------------
git log = muestra el historial de commits de un repositorio ordenado
cronológicamente. Para cada commit muestra su código hash, el autor, la
fecha, la hora y el mensaje asociado.
Este comando es muy versátil y muestra la historia del repositorio en
distintos formatos dependiendo de los parámetros que se le den. Los
más comunes son:
--oneline = muestra cada commit en una línea produciendo una
salida más compacta.
--graph muestra = la historia en forma de grafo.

-----------------------------------------------------------------------
#Mostrar los datos de un commit
	git show
					------------git show-----------
git show = muestra el usuario, el día, la hora y el mensaje del último
commit, así como las diferencias con el anterior.
git show <commit> muestra el usuario, el día, la hora y el mensaje del
commit indicado, así como las diferencias con el anterior.

-----------------------------------------------------------------------
#Mostrar el historial de cambios de un chero
	git annotate
					----------git annotate---------
git annotate = muestra el contenido de un chero anotando cada línea
con información del commit en el que se introdujo.
Cada línea de la salida contiene los 8 primeros dígitos del código hash del
commit correspondiente al cambio, el autor de los cambio, la fecha, el
número de línea del chero y el contenido de la línea.

-----------------------------------------------------------------------
#Mostrar las diferencias entre versiones
	git diff
					-----------git diff------------
git diff = muestra las diferencias entre el directorio de trabajo y la zona
de intercambio temporal.
git diff --cached = muestra las diferencias entre la zona de
intercambio temporal y el último commit.
git diff HEAD = muestra la diferencia entre el directorio de trabajo y el
último commit.

-----------------------------------------------------------------------
#Deshacer cambios
#Eliminar cambios del directorio de trabajo o volver a
#una versión anterior
	git checkout
					--------git checkout---------
git checkout <commit> -- <file> actualiza el chero <file> a la
versión correspondiente al commit <commit>.
Suele utilizarse para eliminar los cambios en un chero que no han sido
guardados aún en la zona de intercambio temporal, mediante el comando
git checkout HEAD -- <file>.

--------------------------------------------------------------------------
#Eliminar cambios de la zona de intercambio temporal
	git reset
					----------git reset-----------
git reset <fichero> elimina los cambios del chero <fichero> de
la zona de intercambio temporal, pero preserva los cambios en el
directorio de trabajo.
Para eliminar por completo los cambios de un chero que han sido
guardados en la zona de intercambio temporal hay que aplicar este
comando y después git checkout HEAD -- <fichero>.

----------------------------------------------------------------------------
#Eliminar cambios de un commit
	git reset
					-------------git reset-------------
git reset --hard <commit> elimina todos los cambios desde el
commit <commit> y actualiza el HEAD este commit.
¡Ojo! Usar con cuidado este comando pues los cambios posteriores al
commit indicado se pierden por completo.
Suele usarse para eliminar todos los cambios en el directorio de trabajo
desde el último commit mediante el comando git reset --hard
HEAD.
git reset <commit> actualiza el HEAD al commit <commit>, es decir,
elimina todos los commits posteriores a este commit, pero no elimina los
cambios del directorio de trabajo.

----------------------------------------------------------------------------
#Creación de ramas
	git branch
					------------git branch------------
git branch <rama> crea una nueva rama con el nombre <rama> en el
repositorio a partir del último commit, es decir, donde apunte HEAD.
Al crear una rama a partir de un commit, el ujo de commits se bifurca en
dos de manera que se pueden desarrollar dos versiones del proyecto en
paralelo.

------------------------------------------------------------------------------
#Listado de ramas
	git log
					---------git log-----------
git branch = muestra las ramas activas de un repositorio indicando con *
la rama activa en ese momento.
git log --graph --oneline = muestra la historia del repositorio en
forma de grafo (--graph) incluyendo todas las ramas (--all).

--------------------------------------------------------------------------------
#Cambio de ramas
	git checkout
					-----------git checkout------------
git checkout <rama> actualiza los cheros del directorio de trabajo a
la última versión del repositorio correspondiente a la rama <rama>, y la
activa, es decir, HEAD pasa a apuntar al último commit de esta rama.
git checkout -b <rama> crea una nueva rama con el nombre
<rama> y la activa, es decir, HEAD pasa a apuntar al último commit de
esta rama. Este comando es equivalente aplicar los comandos git
branch <rama> y después git checkout <rama>.

--------------------------------------------------------------------------------
#Fusión de ramas
	git marge
					----------git merge-----------
git merge <rama> integra los cambios de la rama <rama> en la rama
actual a la que apunta HEAD.

-------------------------------------------------------------------------------------
#Eliminación de ramas
	git branch -d
					-------------git branch -d---------------
git branch -d <rama> elimina la rama de nombre <rama> siempre y
cuando haya sido fusionada previamente.
git branch -D <rama> elimina la rama de nombre <rama> incluso si
no ha sido fusionada. Si la rama no ha sido fusionada previamente se
perderán todos los cambios de esa rama.

-----------------------------------------------------------------------------------------
			¿Qué es GitHub?
GitHub es el proveedor de alojamiento en la nube para repositorios
gestionados con git más usado y el que actualmente tiene alojados más
proyectos de desarrollo de software de código abierto en el mundo.
La principal ventaja de GitHub es que permite albergar un número ilimitado
de repositorios tanto públicos como privados, y que además ofrece
servicios de registro de errores, solicitud de nuevas funcionalidades, gestión
de tareas, wikis o publicación de páginas web, para cada proyecto, incluso
con el plan básico que es gratuito.

-----------------------------------------------------------------------------------------
#Añadir un repositorio remoto
	git remote add
					-----------git remote add-----------
git remote add <repositorio-remoto> <url> crea un enlace
con el nombre <repositorio-remoto> a un repositorio remoto
ubicado en la dirección <url>.
Cuando se añade un repositorio remoto a un repositorio, Git seguirá
también los cambios del repositorio remoto de manera que se pueden
descargar los cambios del repositorio remoto al local y se pueden subir los
cambios del repositorio local al remoto.

-------------------------------------------------------------------------------------------
#Lista de repositorios remotos
	git remote
					-----------git remote-----------
git remote = muestra un listado con todos los enlaces a repositorios
remotos denidos en un repositorio local.
git remote -v = muestra además las direcciones url para cada
repositorio remoto.

-------------------------------------------------------------------------------------------
#Descargar cambios desde un repositorio remoto
	git pull
					----------git pull----------
git pull <remoto> <rama> descarga los cambios de la rama <rama>
del repositorio remoto <remoto> y los integra en la última versión del
repositorio local, es decir, en el HEAD.
git fetch <remoto> descarga los cambios del repositorio remoto
<remoto> pero no los integra en la última versión del repositorio local.

----------------------------------------------------------------------------------------------
#Subir cambios a un repositorio remoto
	git push
					-----------git push-----------
git push <remoto> <rama> sube al repositorio remoto <remoto>
los cambios de la rama <rama> en el repositorio local.
