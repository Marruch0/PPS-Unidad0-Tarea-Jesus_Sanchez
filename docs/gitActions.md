# **Automatización con GitHub Actions y MkDocs**
En este apartado voy a explicar como instalar y configurar MKdocs así como el Workflow de GitHub para que cada vez que haya cambios y se ejecute un push se actualice la web que posteriormente configuraremos con GitHub Pages 



## **MkDocs**
Para poder convertir los archivos Markdown en una pagina web utilizaremos *MkDocs, con el tema *Material*.
Lo primero que vamos a hacer es intalar todo lo necesario de forma local. Lo primero será Python y lo haremos mediante el siguiente comando:

```bash
sudo dnf install -y python3 python3-pip
```
Y comprobaremos la instalación con:

```bash
python3 --version
pip3 --version
```

![Comprobacion python instalado](imagenes/python_instalacion.png)

Lo sigueinte será instalar MkDocs y para ello ejecutaremos:

```bash
pip install --user mkdocs
```
![Instalacion MkDocs](imagenes/instalacionMkdocs.png)

Y lo comprobaremos con el comando `mkdocs --version`

![Comprobacion instalacion MkDocs](imagenes/comprobacion_instalacion_mkdocs.png)

### Código MkDocs
Ahora vamos a crear el archivo `mkdocs.yml` en la raiz del repositorio, en este vamos a definir la estructura de la nevegación, el tema, las extenesiones, los plugins,etc.
Y en el vamos a incluir lo siguiente:

```yml
site_name: PPS Unidad 0 - Jesus Sanchez
nav:
  - Inicio: index.md
  - Git: git.md
  - GitHub Actions: gitActions.md
  - GitHub Pages: gitPages.md
  - Docker: docker.md
  - Conclusiones: conclusiones.md

theme:
  name: material
  language: es
  palette:
  # Modo Oscuro
    - scheme: slate #Por defecto
      primary: black # Color del header
      accent: lime # Color de los enlaces y botones al pasar el ratón por encima
      toggle:
        icon: material/weather-sunny
        name: Cambiar a modo claro
    # Modo Claro 
    - scheme: default
      primary: indigo   
      accent: purple   
      toggle:
        icon: material/weather-night
        name: Cambiar a modo oscuro

  features:
    - navigation.top  # Botón para volver arriba
    - navigation.expand  # Hace que el menú de la izquierda salga abierto

plugins:
  - search #Buscador
  - glightbox #Para poder poner las imagenes en pantalla completa
  
markdown_extensions:
  - admonition # Extension para las cajas de warning, info,etc
  - pymdownx.details
  - pymdownx.inlinehilite
  - pymdownx.superfences
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
      
extra_css:
  - stylesheets/extra.css # Css personalizado que modifica las imagenes para que tengan borde y sombra
```
Ahora vamos a ejecutar el comando `mkdocs server` y si nos vamos al navegador y nos conectamos al localhost por el puerto 8000 podremos ver como tenemos nuestra página en local.
!!! info ""
	Imagen de antes de toda la configuracion estética. El primer yml fue este:
	```yml
	site_name: PPS Unidad 0 - Jesús Sánchez
	nav:
	  - Inicio: index.md
	  - Git: git.md
	  - GitHub Actions: gitActions.md
	  - GitHub Pages: gitPages.md
	  - Docker: docker.md
	  - Conclusiones: conclusiones.md
	```

![Pagina en local](imagenes/paginalocal.png)



## Workflow de Github
En lugar de generar la web manualmente en mi ordenador y subir los HTML, he creado un **Workflow** de GitHub Actions.

Este es un "robot" que sigue unas instrucciones definidas en el archivo `.github/workflows/CreacionDocumentacion.yml`.

### Código del Workflow
El archivo YAML define los siguientes pasos que ejecuta el servidor de GitHub (Runner):

1.  **Checkout:** Descarga mi código.
2.  **Setup Python:** Instala el entorno de ejecución.
3.  **Instalación:** Instala MkDocs y el tema Material.
4.  **Despliegue:** Ejecuta el comando `mkdocs gh-deploy` para crear la rama `gh-pages`.

![Código del Workflow](images/workflow-codigo.png)

---

## 3. Resolución de Incidencias (Troubleshooting)

Durante la primera ejecución del pipeline, el proceso falló debido a una restricción de seguridad en los permisos del Token automático.

!!! failure "Error en el despliegue"
    El log de GitHub Actions mostró el siguiente error crítico:
    > `refusing to allow a Personal Access Token to create or update workflow`

    Esto indicaba que el robot no tenía permisos de **escritura** para publicar en la rama de la web.

### Solución Aplicada
Para corregirlo, se editaron los permisos dentro del archivo del Workflow, otorgando explícitamente capacidad de escritura al proceso:

```yaml
permissions:
  contents: write
