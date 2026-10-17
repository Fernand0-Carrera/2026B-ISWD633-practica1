## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
La carpeta se encuentra vacia de momento.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name contenedor-mysql -v "C:\Users\feral\Documents\EPN\Semestre 6 Software\Construccion y Evolucion de Software\ejercicio3\db:/var/lib/mysql" -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=admin -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin --network net-wp mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Pasa a tener los archivos y ficheros que contiene la carpeta el mysql.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name contenedor-wordpress -p 9500:80 -v "C:\Users\feral\Documents\EPN\Semestre 6 Software\Construccion y Evolucion de Software\ejercicio3\www:/var/www/html" -e WORDPRESS_DB_HOST=contenedor-mysql:3306 -e WORDPRESS_DB_USER=admin -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=admin --network net-wp wordpress
```


### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
La informacion persiste, se mantiene las configuraciones y el tema escogido previamente.
