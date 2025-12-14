# Git y GitHub
## Instalación de Git y configuración
Para poder realizar este apartado *necesitaremos tener instalado Git* en nuestro sistema, en mi caso *utilizo Fedora*, por lo que voy a explicar como hacer una *instalación y configuración* en este sistema operativo.
*Primero* tendremos que *actualizar los repositorio*s y el sistema con `sudo dnf update -y` para a continuación *instalar git*.
```bash
	sudo dnf install -y git
```
[Prueba instalacion git](imagenes/instalacion_git.png)
Y comprobaremos que se ha instalado correctamente con `git -v`.
[Comprobacion de git instalado](imagenes/comprobacion_git.png)

A continuación vamos a configurar el nombre de usuario y el correo electrónico para poder identificar el origen de los commits. En mi caso el usuario y el correo será el mismo que el de la cuenta de GitHub.
Para poder realizar esto, haremos uso de estos comandos:
```bash
	git config --global user.name "Usuario o Nombre"
	git config --global user.email "Correo electrónico"
```
[Usuario y Correo](imagenes/usuarioycorreo.png)

Y podemos comprobar que se ha realizado correctamente con el comando `git config --list`.
[Comprobación del usuario y correo](imagenes/comprobacion_usuarioycorreo.png)

## Creación del repositorio en Github
