# ProyectoUsuario - Aprendiendo Spring Security & API REST

Este proyecto es una API REST base desarrollada con **Spring Boot 3.4.0** y **Java 22**, diseñada como entorno práctico para el aprendizaje y configuración avanzada de **Spring Security**, gestión de usuarios y documentación automatizada de endpoints.

---

## 🛠️ Stack Tecnológico & Versiones

- **Java:** 22
- **Framework Principal:** Spring Boot 3.4.0
- **Persistencia:** Spring Data JPA
- **Base de Datos:** MySQL
- **Documentación de API:** Springdoc OpenAPI UI (Swagger) v2.1.0
- **Utilidades:** Lombok
- **Gestor de Dependencias:** Maven (Wrapper integrado v3.3.2)

---

## 📐 Estructura de Capas del Proyecto

El backend implementa una arquitectura limpia estructurada de la siguiente manera:

1. **Entidades (`tbg.proyecto.Entity`):** Mapeo de la tabla de persistencia `Usuario` mediante anotaciones de Jakarta Persistence y generación de código repetitivo con `@Data` de Lombok.
2. **Repositorios (`tbg.proyecto.Repository`):** Interfaz `UsuarioRepository` que extiende de `JpaRepository` brindando abstracción inmediata de operaciones CRUD sobre la base de datos.
3. **Servicios (`tbg.proyecto.Service`):** Capa encargada del aislamiento de la lógica de negocio y llamadas transaccionales al repositorio.
4. **Controladores (`tbg.proyecto.Controller`):** Exposición de endpoints HTTP en formato JSON bajo la ruta base `/api/usuarios`.

---

## ⚙️ Configuración del Entorno local

### 1. Requisito de Base de Datos
Debes disponer de una instancia de MySQL en ejecución y crear manualmente un esquema o base de datos vacío llamado:

  CREATE DATABASE proyecto_usuario;

### 2. Configuración de Propiedades (`src/main/resources/application.properties`)
Verifica que las credenciales de conexión coincidan con tu servidor MySQL local:

  spring.application.name=ProyectoUsuario
  spring.datasource.url=jdbc:mysql://localhost:3306/proyecto_usuario
  spring.datasource.username=root
  spring.datasource.password=TU_CONTRASENIA

  # Dialecto e inicialización automática de tablas (Modo 'create' para desarrollo inicial)
  spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
  spring.jpa.hibernate.ddl-auto=create

> ⚠️ **Nota Importante:** El modo `spring.jpa.hibernate.ddl-auto=create` regenerará y vaciará todas las tablas cada vez que la aplicación se reinicie. Cambiar a `update` una vez definida la estructura inicial para persistir los datos de prueba.

---

## 🛣️ Especificación de Endpoints (CRUD)

La API mapea los métodos HTTP estándar sobre el recurso `/api/usuarios`:

- **GET /api/usuarios**: Lista de forma global todos los usuarios registrados.
- **GET /api/usuarios/{id}**: Obtiene el detalle de un usuario específico según su ID numérico.
- **POST /api/usuarios**: Registra un nuevo usuario en el sistema. Cuerpo (JSON): `{"nombre", "clave", "email", "estado"}`.
- **PUT /api/usuarios/{id}**: Actualiza completamente los datos de un usuario existente. Cuerpo (JSON): `{"nombre", "clave", "email", "estado"}`.
- **DELETE /api/usuarios/{id}**: Elimina de forma física el registro del usuario por su ID.

---

## 📖 Documentación Interactiva (Swagger UI)

El proyecto incluye soporte nativo para **Springdoc OpenAPI**. Una vez que la aplicación se encuentre corriendo localmente, puedes acceder al panel de pruebas interactivo, visualizar los esquemas JSON de las entidades y ejecutar solicitudes directamente desde tu navegador Web ingresando a:

👉 **http://localhost:8080/swagger-ui/index.html**

---

## 🖥️ Instrucciones de Ejecución

Utiliza el wrapper integrado de Maven para levantar el servidor Amazon Tomcat embebido sin configuraciones globales adicionales:

### En Linux / macOS:
  chmod +x mvnw
  ./mvnw spring-boot:run

### En Windows (CMD / PowerShell):
  .\mvnw.cmd spring-boot:run

El servidor web correrá en el puerto estándar `8080`.

---

## 🧪 Ejecución de Pruebas Unitarias
Para comprobar que el contexto de Spring cargue sin inconvenientes con la base de datos configurada, ejecuta:

  ./mvnw test
