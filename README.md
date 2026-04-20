# Taller Unidad 8: CRUD de Estudiantes con Spring Boot, JPA/Hibernate y MySQL

## Descripción

Este proyecto implementa un CRUD completo de la entidad `Estudiante` utilizando Spring Boot, Spring Data JPA, Hibernate como proveedor ORM, MySQL como base de datos y Thymeleaf para las vistas. La aplicación permite crear, leer, actualizar y eliminar registros de estudiantes, con validaciones de datos y manejo transaccional.

## Requisitos previos

- Java 17 o superior
- MySQL 8.x instalado y en ejecución (local o con Docker)
- Maven 3.x (incluido en el wrapper de Spring Boot)
- IDE (IntelliJ IDEA, VS Code, o similar)

## Configuración de la base de datos

### Crear la base de datos y el usuario en MySQL

Ejecuta los siguientes comandos en MySQL Workbench o en la terminal de MySQL:

```sql
CREATE DATABASE estudiantes_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'apppass';
GRANT ALL PRIVILEGES ON estudiantes_db.* TO 'appuser'@'localhost';
FLUSH PRIVILEGES;

## Configurar la conexión en Spring Boot
spring.datasource.url=jdbc:mysql://localhost:3306/estudiantes_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
spring.datasource.username=appuser
spring.datasource.password=apppass
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

server.port=8080

## Estructura del proyecto
src/main/java/com/universidad/estudiantes/
├── EstudiantesApplication.java
├── controller/
│   └── EstudianteController.java
├── model/
│   └── Estudiante.java
├── repository/
│   └── EstudianteRepository.java
└── service/
    └── EstudianteService.java
src/main/resources/
├── application.properties
└── templates/
    └── estudiantes/
        ├── lista.html
        ├── formulario.html
        └── confirmar-eliminar.html


Funcionalidades CRUD
Listar estudiantes: GET /estudiantes

Mostrar formulario de nuevo estudiante: GET /estudiantes/nuevo

Guardar estudiante: POST /estudiantes/guardar

Mostrar formulario de edición: GET /estudiantes/editar/{id}

Confirmar eliminación: GET /estudiantes/eliminar/{id}

Eliminar estudiante: POST /estudiantes/eliminar/{id}

Capturas de pantalla

Capturas/CrearEstudiantes.png

Capturas/EditarEstudiantes.png

Capturas/EliminarEstudiantes.png

Capturas/ListaEstudiantes.png


Nota: Las capturas de pantalla deben ubicarse en una carpeta screenshots/ dentro del repositorio. Reemplaza los nombres de archivo con los reales.

Validaciones
El nombre y apellido son obligatorios.

El correo debe ser válido y único.

La carrera es obligatoria.

Los mensajes de error se muestran en el formulario sin perder los datos ingresados.
Autor
Jair Sanjuan - Ingeniería de Sistemas - Programación Web 2026
