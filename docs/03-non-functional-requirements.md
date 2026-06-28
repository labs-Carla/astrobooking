# AstroBooking - Non-Functional Requirements

| Documento | Non-Functional Requirements |
|------------|-----------------------------|
| Proyecto | AstroBooking |
| Versión | 1.0.0 |
| Estado | Draft |
| Autor | Carla Tatiana Valderrama Garzón |
| Fecha | 28/06/2026 |

---

# Tabla de contenido

1. Introducción
2. Convenciones
3. Categorías de requisitos
4. NFR-01 Rendimiento
5. NFR-02 Disponibilidad
6. NFR-03 Seguridad
7. NFR-04 Escalabilidad
8. NFR-05 Mantenibilidad
9. NFR-06 Usabilidad
10. NFR-07 Compatibilidad
11. NFR-08 Observabilidad
12. Definition of Done

---

# 1. Introducción

Este documento define los requerimientos no funcionales del MVP de AstroBooking.

Los requerimientos no funcionales establecen los criterios de calidad que deberá cumplir el sistema en aspectos como rendimiento, seguridad, disponibilidad, mantenibilidad y escalabilidad.

Estos requisitos servirán como guía para las decisiones de arquitectura, implementación, despliegue y operación del sistema.

---

# 2. Convenciones

Los requerimientos no funcionales utilizarán la siguiente nomenclatura:

- **NFR**: Non-Functional Requirement.
- **NFR-XX**: Categoría del requisito.
- **NFR-XX.X**: Requisito específico.

Ejemplo:

- NFR-01 Rendimiento
- NFR-01.1 Tiempo de respuesta

# 4. NFR-01 Rendimiento

## Descripción

Esta categoría define los requisitos relacionados con el tiempo de respuesta, la capacidad de procesamiento y el comportamiento general del sistema bajo condiciones normales de operación.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-01.1 | El sistema deberá responder el 95% de las solicitudes HTTP en un tiempo igual o inferior a 2 segundos bajo condiciones normales de operación. | Alta | ≤ 2 segundos para el 95% de las solicitudes |
| NFR-01.2 | El sistema deberá soportar al menos 100 usuarios concurrentes durante el MVP sin degradar significativamente el rendimiento. | Media | ≥ 100 usuarios concurrentes |
| NFR-01.3 | Las consultas a la base de datos deberán ejecutarse de forma eficiente evitando operaciones innecesarias. | Alta | Sin consultas redundantes o de complejidad innecesaria |
| NFR-01.4 | Las operaciones críticas, como autenticación y reservas, deberán priorizar tiempos de respuesta consistentes. | Alta | Tiempo promedio ≤ 2 segundos |

# 5. NFR-02 Disponibilidad

## Descripción

Esta categoría define los requisitos relacionados con la disponibilidad del sistema y la continuidad del servicio.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-02.1 | El sistema deberá estar disponible para los usuarios el 99% del tiempo durante el MVP, excluyendo ventanas de mantenimiento programadas. | Alta | Disponibilidad ≥ 99% |
| NFR-02.2 | El sistema deberá registrar errores críticos para facilitar su diagnóstico. | Alta | Todos los errores críticos registrados |
| NFR-02.3 | En caso de una falla inesperada, el sistema deberá recuperarse sin comprometer la integridad de la información almacenada. | Alta | Sin pérdida de datos confirmados |

# 6. NFR-03 Seguridad

## Descripción

Esta categoría define los requisitos relacionados con la protección de la información, autenticación, autorización y confidencialidad de los datos almacenados y procesados por AstroBooking.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-03.1 | El sistema deberá almacenar las contraseñas utilizando un algoritmo de hash seguro. | Alta | Contraseñas almacenadas con BCrypt o algoritmo equivalente |
| NFR-03.2 | El sistema deberá utilizar autenticación basada en JWT para proteger los recursos privados. | Alta | Todos los endpoints protegidos requieren un token válido |
| NFR-03.3 | El sistema deberá utilizar conexiones HTTPS para proteger la información en tránsito. | Alta | 100% del tráfico cifrado mediante HTTPS |
| NFR-03.4 | El sistema deberá aplicar autorización basada en roles para restringir el acceso a los recursos. | Alta | Acceso validado según el rol del usuario |
| NFR-03.5 | El sistema deberá registrar eventos relevantes de autenticación para fines de auditoría. | Media | Eventos de autenticación registrados correctamente |

# 7. NFR-04 Escalabilidad

## Descripción

Esta categoría define los requisitos que permitirán que AstroBooking pueda crecer en número de usuarios y funcionalidades sin afectar significativamente su rendimiento o arquitectura.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-04.1 | La arquitectura deberá permitir incorporar nuevos módulos sin modificar significativamente los existentes. | Alta | Arquitectura modular documentada |
| NFR-04.2 | El sistema deberá soportar el crecimiento del volumen de datos sin cambios estructurales importantes. | Media | Modelo de datos normalizado y extensible |
| NFR-04.3 | Los componentes del sistema deberán estar desacoplados para facilitar futuras ampliaciones. | Alta | Bajo acoplamiento entre módulos |

# 8. NFR-05 Mantenibilidad

## Descripción

Esta categoría define los requisitos relacionados con la facilidad de mantenimiento, evolución y comprensión del código fuente.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-05.1 | El código deberá seguir principios de Clean Code. | Alta | Cumplimiento de estándares definidos por el proyecto |
| NFR-05.2 | La arquitectura deberá seguir una estructura consistente y modular. | Alta | Arquitectura documentada y aplicada |
| NFR-05.3 | Todas las funcionalidades deberán estar documentadas mediante commits, Pull Requests y documentación técnica. | Alta | Trazabilidad completa entre tareas y código |
| NFR-05.4 | El proyecto deberá utilizar control de versiones mediante Git. | Alta | Todo cambio registrado en Git |
| NFR-05.5 | El código deberá mantenerse organizado siguiendo las convenciones establecidas por el proyecto. | Alta | Cumplimiento de la guía de desarrollo |

# 9. NFR-06 Usabilidad

## Descripción

Esta categoría define los requisitos relacionados con la experiencia de usuario y la facilidad de uso de la plataforma.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-06.1 | La interfaz deberá ser intuitiva y fácil de utilizar para usuarios sin conocimientos técnicos. | Alta | Las tareas principales pueden completarse sin asistencia |
| NFR-06.2 | El sistema deberá ser responsive y adaptarse correctamente a dispositivos móviles, tabletas y escritorio. | Alta | Visualización correcta en los principales tamaños de pantalla |
| NFR-06.3 | La navegación deberá ser consistente en todos los módulos de la aplicación. | Alta | Componentes y navegación uniformes |
| NFR-06.4 | Los mensajes de error deberán ser claros y comprensibles para el usuario. | Media | Todos los errores muestran mensajes descriptivos |

# 10. NFR-07 Compatibilidad

## Descripción

Esta categoría define los requisitos relacionados con la compatibilidad del sistema con navegadores, dispositivos y tecnologías utilizadas en el proyecto.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-07.1 | La aplicación deberá ser compatible con las dos últimas versiones de los principales navegadores modernos. | Alta | Compatibilidad verificada en Chrome, Edge, Firefox y Safari |
| NFR-07.2 | La API deberá seguir los principios REST. | Alta | Endpoints diseñados conforme a REST |
| NFR-07.3 | El sistema deberá utilizar UTF-8 para el almacenamiento y transmisión de información. | Media | Codificación UTF-8 en toda la aplicación |

# 11. NFR-08 Observabilidad

## Descripción

Esta categoría define los requisitos relacionados con el monitoreo, registro de eventos y diagnóstico del sistema durante su operación.

### Requerimientos

| ID | Requerimiento | Prioridad | Métrica/Criterio |
|----|---------------|-----------|------------------|
| NFR-08.1 | El sistema deberá registrar los eventos relevantes de la aplicación mediante logs estructurados. | Alta | Logs disponibles para eventos críticos |
| NFR-08.2 | El sistema deberá registrar errores inesperados para facilitar el diagnóstico. | Alta | Todos los errores registrados con información suficiente |
| NFR-08.3 | El sistema deberá permitir identificar la causa de errores mediante información registrada en los logs. | Media | Logs con contexto suficiente para análisis |

# 12. Definition of Done

Este documento se considera terminado cuando se cumplan los siguientes criterios:

- [x] Se definieron los requerimientos no funcionales del MVP.
- [x] Los requerimientos están organizados por categorías.
- [x] Cada requerimiento posee un identificador único.
- [x] Cada requerimiento tiene una prioridad asignada.
- [x] Cada requerimiento incluye un criterio o métrica verificable.
- [x] El documento cumple con el estándar de documentación del proyecto.
- [x] El documento se encuentra versionado en Git.
- [x] El documento está asociado a la tarea correspondiente en ClickUp.