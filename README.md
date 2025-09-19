# InfraGest

Monorepo para la infraestructura de microservicios, servicios de base de datos, almacenamiento y frontend de InfraGest.

## Estructura del proyecto

- `devices-service/`: Microservicio para gestión de dispositivos
- `orders-service/`: Microservicio para gestión de órdenes
- `employees-service/`: Microservicio para gestión de empleados
- `groups-service/`: Microservicio para gestión de grupos
- `notifications-service/`: Microservicio para gestión de notificaciones
- `eureka-server/`: Servicio de descubrimiento Eureka
- `api-gateway/`: API Gateway para los microservicios
- `frontend/`: Aplicación web (Angular)
- `docker-compose.yml`: Orquestador de todos los servicios y bases de datos

## Servicios incluidos

- **Bases de datos MariaDB**: una para cada microservicio (`devices-db`, `orders-db`, `employees-db`, `groups-db`, `notifications-db`)
- **MinIO**: servicio de almacenamiento de objetos compatible con S3
- **Eureka Server**: servicio de descubrimiento para microservicios
- **Microservicios de InfraGest**: dispositivos, órdenes, empleados, grupos, notificaciones
- **API Gateway**: entrada unificada para consumir los microservicios
- **Frontend**: aplicación web de InfraGest

## Cómo levantar el entorno

1. Clona el repositorio:

    ```sh
    git clone https://github.com/tuusuario/InfraGest.git
    cd InfraGest
    ```

2. Construye y levanta todos los servicios con Docker Compose:

    ```sh
    docker-compose up --build
    ```

3. Accede a los servicios:

    - **Frontend**: [http://localhost:4200](http://localhost:4200)
    - **API Gateway**: [http://localhost:8080](http://localhost:8080)
    - **Eureka Server**: [http://localhost:8761](http://localhost:8761)
    - **MinIO**: [http://localhost:9000](http://localhost:9000)
    - **Bases de datos**:  
      - devices-db: puerto 3312  
      - orders-db: puerto 3311  
      - employees-db: puerto 3308  
      - groups-db: puerto 3309  
      - notifications-db: puerto 3310

4. Los microservicios estarán conectados a sus respectivas bases de datos y registrados en Eureka automáticamente.

## Variables de entorno importantes

Revisa el archivo `docker-compose.yml` para modificar contraseñas, usuarios y puertos según tu necesidad.

## Convenciones de ramas

- `main`: Rama principal de producción
- `dev`: Rama de integración/desarrollo
- Usa ramas feature para cambios específicos, por ejemplo: `feat/devices-create`

## Notas

- El frontend debe estar preparado para conectarse al API Gateway por defecto en `http://localhost:8080`.
