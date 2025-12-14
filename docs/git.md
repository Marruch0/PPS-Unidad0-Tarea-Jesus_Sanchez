# Control de Versiones con Git

En este apartado se detalla la preparación del entorno en Fedora y la creación del repositorio.

## 1. Preparación del entorno
Como paso previo, se actualizó el sistema y se instaló Git en la máquina local (Fedora):

```bash
sudo dnf update -y
sudo dnf install -y git
```
```bash
git config --global user.name "Jesús Sánchez"
git config --global user.email "tu_email@ejemplo.com"
```
## 2. Creacion y estructura
Se creó un repositorio público en GitHub llamado PPS-Unidad0-Tarea-Jesus_Sanchez y se clonó localmente. Posteriormente, se generó la estructura de directorios:
```
PPS-Unidad0-Tarea-Jesus_Sanchez/
├── calculator/
├── docs/
├── .github/workflows/
├── mkdocs.yml
└── requirements.txt
```


