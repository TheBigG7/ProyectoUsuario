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
```sql
CREATE DATABASE proyecto_usuario;
