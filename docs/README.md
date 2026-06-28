# AstroBooking Documentation

Este directorio contiene toda la documentación funcional y técnica del proyecto **AstroBooking**.

El objetivo es documentar el proceso completo de análisis, diseño, arquitectura e implementación del sistema antes del desarrollo del backend.

---

# Estructura de la documentación

## Análisis

| Documento                         | Descripción                                               |
| --------------------------------- | --------------------------------------------------------- |
| 00-documentation-standard.md      | Estándares de documentación del proyecto.                 |
| 01-product-vision.md              | Visión general del producto, objetivos y alcance del MVP. |
| 02-functional-requirements.md     | Requerimientos funcionales del sistema.                   |
| 03-non-functional-requirements.md | Requerimientos no funcionales.                            |
| 04-user-stories.md                | Historias de usuario del MVP.                             |
| 05-domain-model.md                | Modelo de dominio del negocio.                            |
| 06-software-architecture.md       | Arquitectura general del sistema.                         |
| 07-entity-relationship-diagram.md | Modelo entidad-relación de la base de datos.              |
| 08-business-workflows.md          | Índice de los procesos de negocio documentados.           |

---

# Business Workflows

Los flujos de negocio detallados se encuentran en la carpeta:

```text
BusinessWorkflows-WF/
```

| Workflow | Descripción                           |
| -------- | ------------------------------------- |
| WF-001   | Registro de usuario                   |
| WF-002   | Inicio de sesión                      |
| WF-003   | Recuperación de contraseña            |
| WF-004   | Crear reserva de una consulta en vivo |
| WF-005   | Comprar un informe PDF                |
| WF-006   | Procesar pago                         |
| WF-007   | Confirmar reserva                     |
| WF-008   | Cancelar reserva                      |
| WF-009   | Reprogramar reserva                   |
| WF-010   | Enviar recordatorios automáticos      |
| WF-011   | Entregar informe PDF                  |

---

# Diagramas

La carpeta `diagrams/` almacena los diagramas utilizados durante el diseño del sistema.

Ejemplos:

* Software Architecture
* Entity Relationship Diagram (ERD)
* Class Diagram
* Sequence Diagrams
* Activity Diagrams

---

# Trazabilidad

La documentación sigue el siguiente flujo de análisis y diseño:

```text
Product Vision
        ↓
Functional Requirements
        ↓
Non-Functional Requirements
        ↓
User Stories
        ↓
Domain Model
        ↓
Software Architecture
        ↓
Entity Relationship Diagram
        ↓
Business Workflows
        ↓
Class Diagram
        ↓
Backend Implementation
```

---

# Convenciones

* La documentación funcional se escribe en español.
* El código fuente se desarrolla en inglés.
* Los commits y Pull Requests se escriben en inglés.
* Todas las tareas se encuentran asociadas al EPIC **ASTRO-1 Foundation**.

---

# Estado del proyecto

| Tarea                                           | Estado |
| ----------------------------------------------- | ------ |
| ASTRO-1.1 Product Vision                        | ✅      |
| ASTRO-1.2 Functional Requirements               | ✅      |
| ASTRO-1.3 Non-Functional Requirements           | ✅      |
| ASTRO-1.4 User Stories                          | ✅      |
| ASTRO-1.5 Domain Model                          | ✅      |
| ASTRO-1.6 Software Architecture                 | ✅      |
| ASTRO-1.7 Entity Relationship Diagram           | ✅      |
| ASTRO-1.8 Business Workflows                    | ✅      |
| ASTRO-1.9 Class Diagram                         | ⏳      |
| ASTRO-1.10 Spring Boot Project Setup            | ⏳      |
| ASTRO-1.11 RFC-001 Architecture Decision Record | ⏳      |

---

# Próximos pasos

* Completar el diagrama de clases.
* Configurar el proyecto Spring Boot.
* Definir las decisiones de arquitectura (RFC).
* Iniciar la implementación del backend.
