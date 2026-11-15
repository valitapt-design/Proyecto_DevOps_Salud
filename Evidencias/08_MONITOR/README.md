# Fase 08 - MONITOR

## 1. Objetivo
Verificar el funcionamiento y disponibilidad
del servicio mediante monitoreo de Docker y Nginx.

## 2. Monitoreo del contenedor
Se ejecutó docker stats para revisar:
- Consumo de CPU.
- Uso de memoria.
- Tráfico de red.
- Actividad de disco.
- Procesos activos.

## 3. Monitoreo de logs
Se ejecutó docker compose logs para revisar
los registros del contenedor reserva-medica.

## 4. Prueba de solicitudes HTTP
Se realizaron cinco solicitudes mediante curl.
Todas obtuvieron respuesta HTTP 200 OK.

## 5. Evidencias
- EVID_MONITOR_01_DOCKER_LOGS.png
- EVID_MONITOR_02_DOCKER_STATS.png
- EVID_MONITOR_03_HTTP_REQUESTS.png

## 6. Conclusión
El servicio presenta disponibilidad HTTP,
registra correctamente las solicitudes y mantiene
un consumo reducido de recursos en las mediciones realizadas.
