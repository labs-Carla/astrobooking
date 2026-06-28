# AstroBooking - Software Architecture

| Documento | Software Architecture |
|------------|-----------------------|
| Proyecto | AstroBooking |
| Versión | 1.0.0 |
| Estado | Draft |
| Autor | Carla Tatiana Valderrama Garzón |
| Fecha | 28/06/2026 |

---

# Tabla de contenido

1. Introducción
2. Objetivos de la arquitectura
3. Estilo arquitectónico
4. Arquitectura lógica
5. Stack tecnológico
6. Principios de diseño
7. Definition of Done

---

# 1. Introducción

Este documento describe la arquitectura de software adoptada para el MVP de AstroBooking.

Su propósito es definir la organización general del sistema, las responsabilidades de cada capa, las tecnologías seleccionadas y los principios que guiarán el desarrollo del backend.

---

# 2. Objetivos de la arquitectura

La arquitectura de AstroBooking busca cumplir los siguientes objetivos:

- Facilitar la mantenibilidad del sistema.
- Permitir la escalabilidad del producto.
- Reducir el acoplamiento entre módulos.
- Favorecer una alta cohesión.
- Facilitar las pruebas automatizadas.
- Permitir futuras integraciones con otros servicios.

# 3. Estilo arquitectónico

AstroBooking utilizará una arquitectura en capas (Layered Architecture), siguiendo principios de Clean Architecture para mantener una adecuada separación de responsabilidades.

Las capas principales serán:

- Presentation Layer
- Application Layer
- Domain Layer
- Infrastructure Layer

Cada capa tendrá responsabilidades claramente definidas y dependerá únicamente de las capas permitidas por la arquitectura.

# 4. Arquitectura lógica

La arquitectura lógica del backend estará organizada de la siguiente manera:

```text
Controller
      │
      ▼
Service
      │
      ▼
Repository
      │
      ▼
Database
```

### Responsabilidades

| Capa | Responsabilidad |
|------|-----------------|
| Controller | Recibir solicitudes HTTP y devolver respuestas. |
| Service | Implementar la lógica de negocio del sistema. |
| Repository | Gestionar el acceso a la base de datos. |
| Database | Almacenar la información persistente del sistema. |

# 5. Stack tecnológico

| Categoría | Tecnología |
|-----------|------------|
| Lenguaje | Java 21 |
| Framework Backend | Spring Boot |
| Seguridad | Spring Security + JWT |
| Persistencia | Spring Data JPA |
| Base de datos | PostgreSQL |
| Build Tool | Maven |
| Contenedores | Docker |
| Control de versiones | Git |
| Repositorio | GitHub |
| Gestión de tareas | ClickUp |
| IDE | Cursor |

# 6. Principios de diseño

El desarrollo de AstroBooking seguirá los siguientes principios de diseño:

## Separación de responsabilidades

Cada componente tendrá una única responsabilidad claramente definida.

## Bajo acoplamiento

Los módulos dependerán lo menos posible entre sí para facilitar su mantenimiento y evolución.

## Alta cohesión

Las clases agruparán funcionalidades relacionadas dentro del mismo contexto del dominio.

## Principio SOLID

Siempre que sea posible, el diseño seguirá los principios SOLID para mejorar la extensibilidad y mantenibilidad del sistema.

## Clean Code

El código deberá ser legible, consistente y fácil de comprender por otros desarrolladores.

## API First

Las interfaces REST serán diseñadas antes de su implementación para mantener contratos claros entre cliente y servidor.

# 7. Definition of Done

Este documento se considera terminado cuando se cumplan los siguientes criterios:

- [x] Se definió el estilo arquitectónico del proyecto.
- [x] Se documentaron las capas de la arquitectura.
- [x] Se describieron las responsabilidades de cada capa.
- [x] Se definió el stack tecnológico del MVP.
- [x] Se documentaron los principios de diseño.
- [x] El documento cumple con el estándar de documentación del proyecto.
- [x] El documento está versionado en Git.
- [x] El documento está asociado a la tarea ASTRO-1.6 en ClickUp.