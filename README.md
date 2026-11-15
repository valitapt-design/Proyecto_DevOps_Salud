
# Proyecto DevOps - Reserva de Horas Médicas

## 1. Descripción del proyecto

Proyecto DevOps desarrollado para una empresa
del rubro salud que administra una plataforma web de reserva
de horas médicas, correspondiente a la semana 3 de estudio

El objetivo es implementar un servicio web estático utilizando
Nginx y Docker, facilitando la ejecución local, la
reproducibilidad del entorno y la trazabilidad de los cambios.

## 2. Tecnologías utilizadas

- Git y GitHub: control de versiones.
- Visual Studio Code: editor de código.
- Docker Desktop: gestión de contenedores.
- Docker Compose: configuración y ejecución del servicio.
- Nginx Alpine: servidor web.
- HTML5 y CSS3: interfaz web.

## 3. Estructura del proyecto

Proyecto_DevOps_Salud/
├── src/
│   ├── index.html
│   └── styles.css
├── Evidencias/
├── Dockerfile
├── docker-compose.yml
├── .gitignore
├── .env.example
└── README.md

## 4. Requisitos previos

- macOS.
- Git instalado.
- Docker Desktop instalado y funcionando.
- Visual Studio Code (recomendado).

## 5. Instalación y ejecución

Clonar el repositorio:

git clone https://github.com/valitapt-design/Proyecto_DevOps_Salud.git

Ingresar a la carpeta:

cd Proyecto_DevOps_Salud

Construir y ejecutar el servicio:

docker compose up -d --build

## 6. Acceso al servicio

Abrir el navegador en:

http://localhost:8080

## 7. Verificación del servicio

Consultar el estado del contenedor:

docker compose ps

Consultar los registros:

docker logs reserva-medica

Consultar métricas:

docker stats --no-stream reserva-medica

Detener el servicio:

docker compose down

## 8. Seguridad

- Se utiliza .gitignore para excluir archivos sensibles.
- Se incorpora .env.example como plantilla de configuración.
- No se deben publicar contraseñas, tokens ni credenciales reales.
- La aplicación utiliza información ficticia para fines académicos.
- No se almacenan reservas ni datos personales reales.

## 9. Monitoreo

Se utilizan los registros de Docker y las métricas
del contenedor para observar el funcionamiento del servicio.

## 10. Alcance

La aplicación corresponde a una demostración académica para la semana de
estudio correspondiente a la asignatura DevOps de una página web estática 
servida mediante Nginx.
No implementa API ni base de datos.

## 11. Autor

Proyecto académico DevOps Valeska Peña.
