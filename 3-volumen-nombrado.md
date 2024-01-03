# Volúmenes
## NOMBRADO

### Crear volumen

```
docker volume create vol-postgres
```
### ¿Cuál es el Mountpoint de vol-postgres?

### Para determinar la ubicación en el sistema de archivos del host para un volumen Docker específico, se puede usar el siguiente comando:

```
docker volume inspect vol-postgres
```

### ¿Cómo acceder a ese Mountpoint?

### Se puede utilizar un comando Docker para acceder al Mountpoint tal como se muestra a continuación:

```
docker run -it -v vol-postgres:/tmp ubuntu bash
```

### Al ejecutar este comando estamos creando un nuevo contenedor de Ubuntu para poder acceder al contenido del vol-postgres.

### Crear una red para postgres

```
docker network create net-postgres -d bridge 
```

### Servidor postgres usando el volumen nombrado

```
docker run -d --name server-postgres -e POSTGRES_DB=db_drupal -e POSTGRES_PASSWORD=12345 -e POSTGRES_USER=user_drupal -v vol-postgres:/var/lib/postgresql/data --network net-postgres postgres
```

### ¿Qué ha sucedido en vol-postgres?

### Al acceder al vol-postgres podemos ver que ahora contiene los archivos necesarios para el funcionamiento del contenedor creado.
