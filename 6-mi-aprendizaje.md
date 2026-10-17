# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.

Previo a la práctica tenía conocimiento básico de los comandos, no obstante, seguía presentando problemas al momento de distiguir qué hacían o en qué situaciones servían, además, sentía muy complejo todo lo referente a docker.
Posteriormente, logré comprender de manera más sólida el funcionamiento general de docker, su importancia, identifiqué de mejor manera las variables de entorno, los puertos de origen y destino, lo relevante de leer la documentación antes de realizar configuraciones y la correcta declaración de volúmenes nombrados y anónimos.
Entre los problemas que tuve estuvo que al momento de declarar el comando 
```
docker run -d --name contenedor-mysql -v C:\Users\feral\Documents\EPN\Semestre 6 Software\Construccion y Evolucion de Software\ejercicio3\db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=admin -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin --network net-wp mysql:8
```
No era reconocido y marcaba un error, lo cual se debía a que estaba poniendo las rutas sin comillas ("") y el demonio de docker no lee los espacios al no poner la ruta entre comillas por lo cual la ruta solo era leída hasta la parte mostrada a continuación:
C:\Users\feral\Documents\EPN\Semestre
Motivo por el cual el demonio no reconocia el "6" que seguia despúes del espacio, esto, como mencioné, se solucionó al poner comillas en toda la ruta.
```
docker run -d --name contenedor-mysql -v "C:\Users\feral\Documents\EPN\Semestre 6 Software\Construccion y Evolucion de Software\ejercicio3\db:/var/lib/mysql" -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=admin -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin --network net-wp mysql:8
```

Otro error fue al momento de ingresar al servidor de postgres y a server-drupal, los problemas presentados se debieron a que no tenia los contenedores de client-postgres ni de server-postgres activos, lo cual se solventó al usar 
```
docker start <nombre-contenedor>
```
