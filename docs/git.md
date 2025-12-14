# Git y GitHub
## Instalación de Git y configuración
Para poder realizar este apartado **necesitaremos tener instalado Git** en nuestro sistema, en mi caso **utilizo Fedora**, por lo que voy a explicar como hacer una **instalación y configuración** en este sistema operativo.
**Primero** tendremos que **actualizar los repositorio**s y el sistema con `sudo dnf update -y` para a continuación *instalar git*.
```bash
	sudo dnf install -y git
```
![Prueba instalacion git](imagenes/instalacion_git.png)

Y comprobaremos que se ha instalado correctamente con `git -v`.

![Comprobacion de git instalado](imagenes/comprobacion_git.png)

A continuación vamos a configurar el nombre de usuario y el correo electrónico para poder identificar el origen de los commits. En mi caso el usuario y el correo será el mismo que el de la cuenta de GitHub.
Para poder realizar esto, haremos uso de estos comandos:
```bash
	git config --global user.name "Usuario o Nombre"
	git config --global user.email "Correo electrónico"
```
![Usuario y Correo](imagenes/usuarioycorreo.png)

Y podemos comprobar que se ha realizado correctamente con el comando `git config --list`.

![Comprobación del usuario y correo](imagenes/comprobacion_usuarioycorreo.png)

## Creación del repositorio en Github
Para ello desde el navegador y estando en GitHub crearemos un nuevo repositorio en mi caso lllamado `PPS-Unidad0-Tarea-Jesus_Sanchez`.
![Creacion del respositorio](imagenes/repositorio_github.png)

Una vez creado vamos a clonar el repositorio con el enlace del respositorio y lo haremos mediante `git clone`
![Enlace github](imagenes/enlace_github.png)
![Clonacion del repositorio](imagenes/clonarRepositorio.png)

Una vez tenemos clonado el escritorio y hemos comprobado con `ls` que esta vacio vamos a crear la estructura que se nos pide para esta actividad para ello haremos uso de los siguientes comandos:
```bash
	mkdir -p docs .github/workflows calculator
	touch mkdocs.yml requirements.txt
	touch docs/index.md docs/git.md docs/gitActions.md docs/gitPages.md docs/docker.md docs/conclusiones.md
	touch calculator/__init__.py calculator/gui.py
```
Y comprobaremos que lo hemos realizado correctamente con `tree`.
![Comprobacion directorios](imagenes/tree.png)

Una vez comprobado vamos a hacer el primer commit para poder subir todo al repositorio, para ellos primero lo añadiremos con `git add .` indicandoselo en la ruta del repositorio no en ningun subdirectorio, lo siguiente será hacer el commit de lo realizado, para ello usaremos el comando y la descripción de lo realizado `git commit -m "Estructura inicial del proyecto"` y por ultimo haremos el push indicandole la ruta correspondiente, en nuestro caso será main `git push origin main`.

Ahora nos pedirá el usuario y la contraseña pero lo mas probable es que nos de error como pasa en la siguiente imagen:

![Error password](imagenes/primerpushError.png)

### Solución del problema con la contraseña

Para solucionarlo tendremos que crear un Token y usarlo como contraseño. Para ellos nos iremos de nuevo a GitHub en el navegador y nos iremos a Settings>Developer Settings>Personal access tokkens y aqui selecionaremos el "classic".

![Token classic](imagenes/token1.png)

Una vez aquí, le daremos a generar un nuevo token clasico.

![Token classic 2](imagenes/token2.png)

Y aquí la deremos un nombre al token, en mi caso usaré Fedora Git. Tambien le daremos una "fecha de caducidad" al token, que en mi caso serán 90 días y seleccionaremos los permisos que tendremos con ese token, tendremos que tener los permisos de:

	* repo
	* workflow(Lo necesitaremos para más adelante)
	
![Permisos token](imagenes/token3.png)

![Permisos workflow](imagenes/token4.png)
	
Una vez hecho esto crearemos el tokken y se github nos lo mostrará en pantalla.
!!! warning "Copiar y guardar el tokken"
	Tendremos que guardar el tokken, ya que GitHub solo nos lo mostrará una vez, por lo que mucho cuidado con esto.

## Comprobación del problema solucionado y de cambios en el repositorio

Ahora volvemos a intentar la subida de los cambios al repositorios con `git push origin main` y cuando nos pida la contraseña copiaremos el tokken que hemos creado y ahora si tendriamos subidos los cambios al repositorio y podremos comprobarlo en el navegador.

![Git push bien](imagenes/git_push_bien.png)

![Comprobacion del repositorio](imagenes/comprobacionrepositorio.png)

![Comprobacion del repositorio 2](imagenes/comprobacionRepositorio2.png)


Ahora vamos a seguir con el siguiente apartado --> [Continuar...](gitActions.md)
