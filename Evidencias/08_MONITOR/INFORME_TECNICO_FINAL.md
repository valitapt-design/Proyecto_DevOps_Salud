# INFORME TÉCNICO FINAL
## Proyecto DevOps – Sistema de Reserva de Horas Médicas

**Proyecto:** Proyecto DevOps Salud  
**Organización:** Centro Médico Salud  
**Servicio:** Plataforma web de reserva de horas médicas  
**Servidor web:** Nginx  
**Contenedorización:** Docker  
**Orquestación:** Docker Compose  
**Repositorio:** https://github.com/valitapt-design/Proyecto_DevOps_Salud  
**Versión inicial:** 1.0.0

---

# 1. Introducción

El presente informe técnico documenta la implementación de prácticas DevOps aplicadas a un servicio web de reserva de horas médicas para una empresa del rubro salud.

El proyecto busca mejorar la estandarización, trazabilidad y reproducibilidad del despliegue de aplicaciones, reduciendo los errores asociados a configuraciones manuales y diferencias entre ambientes de desarrollo y pruebas.

Para cumplir este objetivo se desarrolló una aplicación web estática utilizando HTML y CSS, servida mediante Nginx dentro de un contenedor Docker y administrada mediante Docker Compose.

La solución se ejecuta localmente en Docker Desktop y permite simular el proceso de reserva de horas médicas sin utilizar una API, base de datos ni almacenar información de pacientes.

# 2. Objetivos del proyecto

## 2.1 Objetivo general

Implementar una solución DevOps que permita estandarizar la construcción, ejecución, validación, despliegue y monitoreo de un servicio web de reserva de horas médicas mediante herramientas de contenedorización y control de versiones.

## 2.2 Objetivos específicos

- Implementar una aplicación web estática con HTML y CSS.
- Construir una imagen Docker utilizando Nginx.
- Configurar Docker Compose para ejecutar el servicio en el puerto 8080.
- Mantener el código y las configuraciones bajo control de versiones mediante Git y GitHub.
- Aplicar buenas prácticas de seguridad para evitar la exposición de información sensible.
- Verificar el funcionamiento mediante pruebas HTTP y revisión de logs.
- Monitorear el consumo de recursos del contenedor.
- Proponer mejoras para evolucionar el ciclo DevOps.

# 3. Arquitectura de la solución

La solución utiliza una arquitectura sencilla basada en un servidor web contenerizado.

## Componentes

- HTML5: estructura de la aplicación.
- CSS3: presentación visual.
- Nginx Alpine: servidor web.
- Docker: construcción y ejecución de contenedores.
- Docker Compose: administración del servicio.
- Git: control de versiones.
- GitHub: almacenamiento del repositorio y trazabilidad.
- Docker Desktop: administración local de contenedores.

## Funcionamiento

El navegador realiza solicitudes al puerto 8080 del equipo local. Docker redirige estas solicitudes al puerto 80 del contenedor, donde Nginx entrega los archivos estáticos de la aplicación.

# 4. Implementación realizada

Se desarrolló una aplicación web que permite simular una reserva de horas médicas.

La interfaz incluye:

- Nombre del paciente de demostración.
- Especialidad médica.
- Profesional.
- Fecha de atención.
- Horario disponible.
- Botón para simular la reserva.
- Mensajes de validación y confirmación.

La aplicación no almacena reservas reales ni requiere conexión a una base de datos.

La imagen se construye a partir de Nginx Alpine y el servicio se publica localmente mediante Docker Compose.

# 5. Evidencia de monitoreo

Se realizaron verificaciones locales utilizando herramientas de Docker y solicitudes HTTP.

## 5.1 Revisión de logs

Se utilizó el comando:

`docker compose logs --tail=50 reserva-medica`

Los registros permitieron observar el inicio del servidor Nginx y las solicitudes HTTP recibidas.

Se identificaron respuestas exitosas con código HTTP 200, confirmando que el servidor entregó correctamente los recursos solicitados.

**Evidencia:** EVID_MONITOR_01_DOCKER_LOGS.png

## 5.2 Monitoreo de recursos

Se ejecutó:

`docker stats --no-stream reserva-medica`

Los resultados obtenidos durante una medición puntual fueron:

| Métrica | Resultado |
|---|---:|
| CPU | 0,00 % |
| Memoria utilizada | 8,625 MiB |
| Memoria porcentual | 0,22 % |
| NET I/O | 4,65 kB / 26,7 kB |
| BLOCK I/O | 0 B / 4,1 kB |
| Procesos activos | 9 |

Los valores muestran un consumo reducido de recursos durante la medición realizada.

Es importante considerar que estos resultados corresponden a una observación puntual en un entorno local y no representan una prueba de rendimiento bajo carga.

**Evidencia:** EVID_MONITOR_02_DOCKER_STATS.png

## 5.3 Validación de solicitudes HTTP

Se ejecutaron cinco solicitudes HTTP mediante curl para verificar la disponibilidad del servicio.

Las cinco solicitudes obtuvieron respuesta HTTP 200 OK.

Esto demuestra que Nginx recibió y respondió correctamente las peticiones durante la prueba.

**Evidencia:** EVID_MONITOR_03_HTTP_REQUESTS.png

# 6. Análisis de resultados

Las pruebas realizadas permitieron comprobar que la aplicación se ejecuta correctamente dentro de un contenedor Docker.

El servidor Nginx respondió satisfactoriamente a las solicitudes HTTP y registró la actividad en sus logs.

El consumo de CPU y memoria observado fue reducido, lo que resulta coherente con una aplicación web estática de baja complejidad.

Además, las pruebas de operación permitieron verificar que el contenedor puede detenerse, reiniciarse y recuperarse mediante Docker Compose.

Los resultados demuestran que la contenerización facilita la estandarización del entorno y reduce las diferencias de configuración entre equipos.

Sin embargo, las pruebas se realizaron en un entorno local y con una carga limitada, por lo que no permiten establecer conclusiones sobre el comportamiento del servicio ante múltiples usuarios simultáneos.

# 7. Problemas encontrados y soluciones

Durante el desarrollo se identificaron los siguientes inconvenientes:

## 7.1 Diferencias en el entorno de ejecución

Se buscó evitar las diferencias entre el computador de desarrollo y el entorno de ejecución mediante una imagen Docker basada en Nginx Alpine.

**Solución:** utilizar Docker y Docker Compose para estandarizar el entorno de ejecución.

## 7.2 Botón de simulación sin funcionalidad

Inicialmente, el botón del formulario no ejecutaba ninguna acción.

**Solución:** incorporar JavaScript para validar los campos y mostrar un mensaje de confirmación de la reserva simulada.

## 7.3 Dificultades con el control de versiones

Durante la publicación de cambios se presentó un inconveniente al intentar subir una rama que todavía no había sido creada localmente.

**Solución:** crear la rama correspondiente y posteriormente publicarla en GitHub.

## 7.4 Necesidad de verificar la disponibilidad del servicio

Se requería comprobar que el servicio continuara respondiendo después de reinicios y detenciones.

**Solución:** utilizar Docker Compose para reiniciar, detener y recuperar el contenedor, verificando posteriormente las respuestas HTTP.

# 8. Buenas prácticas transversales de seguridad

Para el proyecto se consideran las siguientes medidas:

1. Mantener el archivo `.env.example` como referencia de configuración, sin credenciales reales.
2. Utilizar `.gitignore` para excluir archivos locales sensibles, especialmente `.env`.
3. No incorporar contraseñas, tokens, claves privadas ni credenciales en el repositorio.
4. Utilizar información ficticia en el formulario de demostración.
5. No almacenar información médica ni datos personales reales.
6. Mantener las configuraciones y los cambios documentados mediante Git.
7. Revisar los archivos antes de publicarlos en GitHub.

La aplicación es estática y no cuenta con una API ni base de datos, por lo que no procesa ni persiste reservas reales.

# 9. Propuestas de mejora para evolucionar el ciclo DevOps

Se identifican las siguientes oportunidades de mejora:

## Mejora 1. Automatización CI/CD mediante GitHub Actions

Implementar un flujo de integración continua que valide automáticamente la estructura del proyecto, los archivos obligatorios y la configuración antes de integrar cambios a la rama principal.

**Beneficio:** reducir errores manuales y mejorar la trazabilidad de las modificaciones.

## Mejora 2. Incorporar análisis de seguridad automatizado

Integrar herramientas de análisis estático y detección de secretos para identificar credenciales expuestas y posibles vulnerabilidades en el repositorio.

**Beneficio:** fortalecer la seguridad desde las primeras etapas del desarrollo.

## Mejora 3. Implementar monitoreo continuo

Incorporar métricas y alertas que permitan observar el consumo de CPU, memoria, disponibilidad HTTP y errores del servidor.

**Beneficio:** detectar oportunamente problemas de disponibilidad y rendimiento.

## Mejora 4. Mejorar la estrategia de pruebas automatizadas

Incorporar validaciones automáticas del HTML, CSS y funcionamiento de los componentes del formulario, además de pruebas de integración del contenedor.

**Beneficio:** aumentar la calidad del servicio y disminuir errores antes de liberar nuevas versiones.

## Mejora 5. Fortalecer la gestión de versiones y liberaciones

Establecer una estrategia de versionamiento semántico y un proceso formal de aprobación mediante Pull Requests antes de fusionar cambios hacia main.

**Beneficio:** mejorar el control de cambios, la trazabilidad y la identificación de versiones estables.

# 10. Conclusiones

La implementación del proyecto DevOps para el servicio de reserva de horas médicas permitió aplicar prácticas de desarrollo y operaciones en un entorno local reproducible.

La utilización de Docker, Docker Compose y Nginx permitió estandarizar la ejecución de la aplicación, mientras que Git y GitHub facilitaron el control de versiones y la documentación de los cambios.

Las pruebas de monitoreo permitieron verificar la disponibilidad del servicio, observar los registros de Nginx y analizar el consumo de recursos del contenedor.

Asimismo, se incorporaron medidas de seguridad orientadas a evitar la publicación de credenciales y datos personales, manteniendo la aplicación como una simulación sin persistencia de información.

Finalmente, las mejoras propuestas permiten identificar oportunidades para avanzar hacia un ciclo DevOps más automatizado, seguro, trazable y orientado a la mejora continua.

# 11. Repositorio y entrega

**Repositorio GitHub:**

https://github.com/valitapt-design/Proyecto_DevOps_Salud

**Versión inicial documentada:** v1.0.0

**Archivo comprimido:** Proyecto_DevOps_Salud.zip

**Entorno de ejecución:** Docker Desktop local.

**URL de verificación:** http://localhost:8080

