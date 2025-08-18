# Despliegue de la Calculadora de Probabilidad de Trading

Este repositorio contiene los archivos de configuración para desplegar la aplicación "Calculadora de Probabilidad de Trading" utilizando Docker y Docker Compose.

La imagen Docker de la aplicación se construye automáticamente a través de GitHub Actions y se aloja públicamente en Docker Hub, lista para ser desplegada.

---

## 📋 Pre-requisitos

Para desplegar esta aplicación, necesitas tener lo siguiente instalado en tu máquina o servidor:

*   **Docker:** [Guía de instalación de Docker](https://docs.docker.com/engine/install/)
*   **Docker Compose V2:** (Viene incluido con Docker Desktop o se instala como plugin en Linux con `sudo apt install docker-compose-plugin`)
*   **Git:** Para clonar este repositorio.

---

## 🚀 Puesta en Marcha (Despliegue Rápido)

El proceso para levantar la aplicación es simple y directo.

### 1. Clonar el Repositorio de Despliegue

Abre tu terminal y clona este repositorio en la máquina donde deseas ejecutar la aplicación.

```bash
git clone https://github.com/ale90qm/calcprob-trading-prod.git
cd calcprob-trading-prod
```

### 2. Levantar la Aplicación

Desde la carpeta del proyecto, ejecuta el siguiente comando. Docker Compose descargará las imágenes públicas necesarias de Docker Hub (la de la aplicación y la de Nginx) y levantará los contenedores en segundo plano.

```bash
docker compose up -d
```

¡Eso es todo! La aplicación ahora debería estar accesible.
*   **En local:** `http://localhost:8080` (o el puerto que hayas configurado en `docker-compose.yml`)
*   **En un servidor:** `http://TU_DIRECCION_IP_DEL_SERVIDOR`

---

## 🔄 Actualizar la Aplicación

Para actualizar la aplicación a la última versión disponible en Docker Hub, simplemente ejecuta los siguientes comandos desde la carpeta del proyecto:

```bash
# 1. Descarga la última versión de la imagen
docker compose pull

# 2. Levanta de nuevo los contenedores. Docker Compose recreará solo lo que ha cambiado.
docker compose up -d
```

---

## 📁 Estructura de Archivos

*   `docker-compose.yml`: Orquesta los contenedores de la aplicación (`app`) y el servidor web (`nginx`). Está configurado para descargar las imágenes públicas de Docker Hub.
*   `nginx.conf`: Archivo de configuración para el servidor web Nginx, que actúa como proxy inverso para la aplicación PHP-FPM.