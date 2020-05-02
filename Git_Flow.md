# ***Git Flow***

Git Flow es un conjunto de extensiones de git, cuyo objetivo es propocionarnos comandos para la terminal que faciliten el desarrollo del Git Branching Model (GBM). Dichos comandos nos ayudan en la creacion de nuevas ramas, en la eliminacion de estas una vez terminadas, realizando varias tareas en un solo comando. Por ejemplo: Si es que quisieramos unir una rama de **Feature** a **Develop**, tendriamos que ir a **Develop**, unir las ramas sin Fast Forward, y por ultimo eliminar la rama **Feature**, si bien es un proceso mecanico, podria generar fallas, como eliminar la rama **Develop**, o no hacer una union de manera correcta. Todo lo mencionado anteriormente se resume en un solo comando de git flow, acelerando el proceso y reduciendo de gran manera los posibles errores en el manejo de ramas.
En el siguiente articulo explicara los principales comandos para Git Flow y los comandos que resumen de Git, abalizando rama por rama.
## Inicio
Para comenzar con Git Flow, primero debemos situarnos en el repositorio git de nuestro proyecto y ejecutar el comando:
```
git flow init
```
Posteriormente de ejecutar este comando, nos realizaran varias preguntas respecto a los nombres que queremos asignar a cada rama, si solo presionamos enter se asignara el nombre por defecto a cada rama: Ejemplo: **Feature** sera feature y asi respectivamente con cada rama. Para finalizar nos situara en la rama *develop* automaticamente para comenzar con el trabajo.

## **Rama Feature**
### Iniciar
Para crear una rama **feature** debemos ejecutar el siguiente comando:
```
git flow feature start NOMBRE
```
Se creara una nueva rama *"feature/NOMBRE"*, que comenzara con el commit de **develop** en el que estemos actualmente, y nos situa en la nueva rama automaticamente .
### Finalizar
Cuando terminamos nuestro trabajo y sentimos que esta listo para ser integrado en la rama **develop**, ejecutamos el siguiente comando:
```
git flow feature finish NOMBRE
``` 
En NOMBRE debemos ingresar el nombre de la rama **feature** que queremos finalizar, a continuacion, se hara un *merge* con la rama **develop** sin Fast Forward, nos cambiara a esta rama y finalmente se eleminara la rama **feature** que habiamos finalizado.

## **Rama Release**
### Iniciar
Para iniciar una rama de tipo *+release** debemos ejecutar el siguiente comando:
```
git flow release start NOMBRE
```
Este comando lo que hara sera crear una nueva rama **release**, que contendra el ultimo commit de **develop**, y nos situara en esta rama automaticamente.
### Finalizar
Para finalizar esta rama usamos el comando:
```
git flow release finish NOMBRE
```
Esto comando realiza varias acciones:  
* Primero realiza un merge sin Fast Forward con la rama **master**.
* Realiza un segundo merge nuevamente sin Fast Forward con la rama **develop**.
* Nos situa en la rama **develop**.
* Finalmente elimina la rama **release**.
## **Rama Hot Fix**
### Iniciar 
Para iniciar una rama de tipo *hotfix* debemos ejecutar el siguiente comando:
```
git flow hotfix start VERSION
```
Este creara una nueva rama a partir del ultimo commit que tengamos en la rama **master**, para despues situarnos en esta.
### Finalizar
Una vez solucionado el error, ejecutamos el siguiente comando para unirlo a sus ramas correspondientes:
```
git flow hotfix finich VERSION
```
Este comandp primero hara un marge con la rama **master**, a demás de taggear el commit de la rama **master** con la version del error, luego realizara el mismo proceso con la rama **develop**, finalmente elimando la rama **hotfix** donde habiamos solucionado el error.

## **Notas finales**
* Las ramas **master** y **develop** van creciendo a medida que las demas ramas van creciendo, por eso es que no se menciono ningun comando para estas dos.
* Cabe aclarar que al usar Git Flow no nos restringe de usar los comandos habituales de Git, si es que deseamos hacer algun merge manual, o crear ramas manuales, lo podemos hacer. Git Flow es solo un comando mas que podemos usar.
* Cuando usamos el Git Flow Init, se nos preguntaran por mas ramas que las tipicas cinco. Si no hacemos nada estas ramas se crearan con sus nombres por defecto, no es oblicatorio usarlas. Como son ramas secundarias, estas ni siquiera estaran nombradas en las ramas que tenemos a no ser que las creemos.
