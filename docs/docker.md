# Despliegue de Contenedor NGINX con Docker

Se ha utilizado Docker en Fedora para desplegar la documentación localmente.

## 1. Instalación en Fedora
Se instalaron los paquetes necesarios:

```bash
sudo dnf install -y dnf-plugins-core docker-ce docker-ce-cli containerd.io
sudo systemctl enable --now docker
