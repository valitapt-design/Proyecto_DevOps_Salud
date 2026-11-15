# Fase 06 - DEPLOY

## 1. Objetivo
Verificar el despliegue de la aplicación Reserva de Horas Médicas
mediante Docker y Nginx.

## 2. Herramientas utilizadas
- Docker Desktop
- Docker Compose
- Nginx
- Terminal macOS

## 3. Actividades realizadas
- Construcción de la imagen Docker.
- Inicio del servicio mediante Docker Compose.
- Verificación del estado del contenedor.
- Verificación de las imágenes Docker.
- Validación de disponibilidad HTTP mediante CURL.

## 4. Resultados
El contenedor reserva-medica se encuentra activo.
El servicio está publicado en el puerto 8080.
La aplicación responde correctamente con HTTP 200 OK.
El servidor web Nginx está operativo.

## 5. Evidencias
EVID_DEPLOY_01_VERIFICACION_DOCKER.png

## 6. Conclusión
El despliegue de la aplicación fue exitoso.
El servicio se encuentra disponible localmente mediante
http://localhost:8080.
