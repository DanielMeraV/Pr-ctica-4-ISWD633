# Wordpress

### Crear red net-wp

```
docker network create net-wp -d bridge 
```

### Para que persista la información es necesario conocer ¿en dónde mysql almacena la información?

### La parte -v /my/own/datadir:/var/lib/mysql del comando monta el directorio /my/own/datadir desde el sistema host subyacente como /var/lib/mysql dentro del contenedor, donde MySQL de forma predeterminada escribir sus archivos de datos.

### ruta carpeta host: db
### Crear contenedor de MySQL en la red net-wp

```
docker run -d --name server-mysql --env-file=variables.txt -v ${PWD}/db:/var/lib/mysql --network net-wp mysql:8
```

### Para que persista la información es necesario conocer ¿en dónde wordpress almacena la información?

### La información almacenada de WordPress está en el directorio /var/www/html.

### ruta carpeta host: www

### Crear contenedor de Wordpress en la red net-wp

```
docker run -d --name server-wordpress -v ${PWD}/www:/var/www/html -e WORDPRESS_DB_HOST=server-mysql -e WORDPRESS_DB_USER=danielm -e WORDPRESS_DB_PASSWORD=123456 -e WORDPRESS_DB_NAME=gr2db --network net-wp --publish published=9300,target=80 wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada
### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

```
docker rm server-wordpress
```
