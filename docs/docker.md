# Despliegue de Contenedor NGINX con Docker
Lo primero que tendremos que hacer es instalar docker, en mi caso el proceso de instalación es con este simple comando:
```bash
sudo dnf install docker-cli containerd
```
Una vez instalado podemos hacer una simple prueba para ver que docker esta instalado correctamente, para ellos vamos a iniciar el contenedor `hello-world` con `docker run hello-world`

![hello-world](imagenes/hello-world.png)

Una vez hemos comprobado que esta instalado correctamente, vamos a cambiar la rama de git para poder iniciar el contenedor desde esta. Para ello usaremos el comando `git checkout gh-pages`, si no os funciona como me pasó a mi, simplemente tendremos que hacer un fetch para actualizar, usamos el comando `git fetch origin` y volvvemos a lanzar el comando anterior para cambiarnos de rama.

![checkout1](imagenes/checkout1.png)

![checkout2](imagenes/checkout2.png)

Una vez que el comando se nos ha completado con exito, haremos un `ls` para comprobar que hemos cambiado de rama de manera correcta.

![ls](imagenes/ls.png)

Y ahora para poder iniciar el contenedor de docker, simplemente ejecutaremos el siguiente comando:
```bash
sudo docker run -d \
  --name PPSUnidad0-Tarea_Jesus_Sanchez \
  -p 8085:80 \
  -v $(pwd):/usr/share/nginx/html:ro,z \
  nginx
```
Al estar en fedora para que funcione tendremos que re-etiquetar el volumen para que SELinux permita el acceso.

![rundocker](imagenes/rundocker.png)

Y comprobamos que está corriendo con `docker ps`.

![dockerps](imagenes/dockerps.png)

Ahora si nos entramos en el localhost mediante el navegador por el puerto 8085, nos encontraremos con nuestra pagina web en github site.

![Comprobacion final](imagenes/comprobacionfinal.png)

!!! info "Contenido de inspect"
	El contenido de inspect estará en la subida de la tarea en el moodle.
