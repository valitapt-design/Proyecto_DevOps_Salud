# Fase 07 - OPERATE

## 1. Objetivo
Verificar la continuidad operativa y recuperación
del servicio Reserva de Horas Médicas.

## 2. Herramientas utilizadas
- Docker Desktop
- Docker Compose
- Nginx
- Terminal macOS

## 3. Actividades realizadas

### 3.1 Reinicio del servicio
Se ejecutó docker compose restart para comprobar
la capacidad de reinicio del contenedor.

### 3.2 Detención del servicio
Se ejecutó docker compose stop.
Se verificó el estado Exited (0).

### 3.3 Recuperación del servicio
Se ejecutó docker compose start.
Se verificó nuevamente el estado Up.

### 3.4 Validación de disponibilidad
Se ejecutó curl -I http://localhost:8080.
El resultado obtenido fue HTTP/1.1 200 OK.

## 4. Resultados
El contenedor pudo detenerse, reiniciarse y recuperarse
correctamente. La aplicación volvió a responder
mediante el servidor Nginx.

## 5. Evidencias
- EVID_OPERATE_01_REINICIO_SERVICIO.png
- EVID_OPERATE_02_DETENCION_RECUPERACION.png

## 6. Conclusión
Las pruebas de operación y recuperación fueron exitosas.
El servicio mantiene su disponibilidad después
de los procedimientos de reinicio y recuperación.
