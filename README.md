# Sistema de Gestión de Despachos y Ventas - Arquitectura DevOps

Este repositorio contiene la solución contenedorizada y automatizada para el Examen Transversal de la asignatura DevOps y Cloud Computing. El proyecto ha sido desacoplado en microservicios independientes utilizando Docker y desplegado en una arquitectura Cloud (AWS).

# Arquitectura del Proyecto

El ecosistema está compuesto por 4 componentes principales orquestados:
* **Frontend:** Aplicación de interfaz de usuario (Node.js) corriendo en el puerto `3000`.
* **Backend Ventas:** API REST en Java Spring Boot encargado del módulo de ventas en el puerto `8080`.
* **Backend Despachos:** API REST en Java Spring Boot encargado del módulo de despachos en el puerto `8082`.
* **Base de Datos:** Motor relacional MySQL 8.0 encargado de la persistencia (`duoc_db`).


# Requisitos Previos

Para ejecutar este proyecto de manera local, asegúrate de tener instalado:
* [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* [Docker Compose](https://docs.docker.com/compose/)
* Git


# Cómo Ejecutar el Proyecto en Local

Sigue estos pasos para levantar la arquitectura completa en tu máquina:

1. Clonar el repositorio:

   git clone [https://github.com/23eeliass/prueba2-devops.git](https://github.com/23eeliass/prueba2-devops.git)
   cd prueba2-devops

2. Levantar los contenedores con Docker Compose:

Este comando descargará las imágenes base, compilará los proyectos Java/Node y encenderá los servicios:
docker-compose up --build

3. Acceder a la aplicación:

Una vez que la terminal muestre que los servidores Tomcat han iniciado correctamente, abre tu navegador web e ingresa a:

* Frontend Web: http://localhost:3000

* API Ventas: http://localhost:8080

* API Despachos: http://localhost:8082


4. Detener el entorno:
Para apagar los servicios de forma limpia sin dejar residuos en memoria: 
docker-compose down


* Pipeline de CI/CD (GitHub Actions)

El proyecto cuenta con un flujo de integración continua automatizado en .github/workflows/. Ante cada push en la rama main, el robot realiza:

Compilación del código Java mediante Maven.

Construcción de imágenes Docker optimizadas para cada microservicio.

Almacenamiento seguro de las imágenes en GitHub Packages (GHCR) como artefactos privados listos para su despliegue en producción.