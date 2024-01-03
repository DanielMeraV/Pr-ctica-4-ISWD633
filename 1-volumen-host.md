# Volúmenes

## HOST

### Volumen tipo host con la imagen nginx:alpine 
### ruta carpeta host: directorio en donde se encuentra la carpeta html en nuestro computador, usar \\
### ruta carpeta contenedor: /usr/share/nginx/html desde la documentación

```
docker run -d --name <nombre contenedor> --publish <mapeo de puertos> -v <ruta carpeta host>:<ruta carpeta contenedor> url: <nombre imagen>
```
docker run -d --name nginx-server --publish published=80,target=80 -v C:\VolumenesDocker\nginx\html:/usr/share/nginx/html nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?

### Se muestra el error 403 Forbidden en el navegador, lo que nos indica que el servidor recibió la solicitud, pero se niega a cumplirla debido a que el cliente no tiene los permisos para acceder al recurso solicitado.

### ¿Qué pasa con el archivo index.html del contenedor?

### No existe ningún archivo index.html dentro de la carpeta “html” creado para el contenedor.

### Ir a https://html5up.net/ y descargar un template gratuito - descomprimir en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?

### Después de haber descargado una plantilla y descomprimirla en la carpeta “html” el servidor ahora si encuentra el archivo index.html y se muestra la página web al ingresar al servidor de nignx.

### Eliminar el contenedor

docker rm -f nginx-server

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

### Al volver a crear el contenedor al tener el mismo volumen de tipo host y los mismos directorios el contenido de la página web configurado previamente se despliega sin ningún problema al acceder al servidor de nginx.

### ¿Qué hace el comando pwd?

### El comando pwd significa "print working directory" (imprimir directorio de trabajo). Cuando ejecutas este comando en una terminal, te muestra la ruta completa del directorio actual en el que te encuentras.

### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name server-nginx --publish published=5000,target=80 -v ${PWD}/html:/usr/share/nginx/html nginx:alpine
```