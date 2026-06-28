# AstroBooking - Entity Relationship Diagram

  Documento   Entity Relationship Diagram
  ----------- ---------------------------------
  Proyecto    AstroBooking
  Versión     1.0.0
  Estado      Draft
  Autor       Carla Tatiana Valderrama Garzón
  Fecha       28/06/2026

------------------------------------------------------------------------

# Tabla de contenido

1.  Introducción
2.  Objetivos
3.  Entidades
4.  Relaciones
5.  Diagrama Entidad-Relación
6.  Cardinalidades
7.  Decisiones de diseño
8.  Definition of Done

------------------------------------------------------------------------

# 1. Introducción

Este documento describe el modelo entidad-relación del MVP de
AstroBooking.

Su objetivo es representar la estructura lógica de la base de datos,
identificando las entidades, sus atributos principales y las relaciones
existentes entre ellas.

El modelo servirá como base para la implementación de PostgreSQL y las
entidades JPA del backend.

------------------------------------------------------------------------

# 2. Objetivos

-   Identificar las entidades persistentes.
-   Definir las relaciones entre ellas.
-   Establecer las cardinalidades.
-   Servir como base para el diseño físico de la base de datos.

------------------------------------------------------------------------

# 3. Entidades

## User

  Campo            Tipo           Restricciones
  ---------------- -------------- ------------------------
  id               UUID           PK
  first_name       VARCHAR(100)   NOT NULL
  last_name        VARCHAR(100)   NOT NULL
  email            VARCHAR(255)   UNIQUE, NOT NULL
  password         VARCHAR(255)   NOT NULL
  role             VARCHAR(20)    NOT NULL
  status           VARCHAR(20)    NOT NULL
  email_verified   BOOLEAN        NOT NULL DEFAULT FALSE
  created_at       TIMESTAMP      NOT NULL
  updated_at       TIMESTAMP      NOT NULL

------------------------------------------------------------------------

## ProfessionalProfile

  Campo                 Tipo           Restricciones
  --------------------- -------------- ---------------
  id                    UUID           PK
  user_id               UUID           FK → User.id
  display_name          VARCHAR(150)   NOT NULL
  biography             TEXT           NULL
  specialization        VARCHAR(100)   NULL
  timezone              VARCHAR(50)    NOT NULL
  meeting_platform      VARCHAR(50)    NULL
  profile_image         VARCHAR(500)   NULL
  contact_information   VARCHAR(255)   NULL
  is_published          BOOLEAN        NOT NULL
  created_at            TIMESTAMP      NOT NULL
  updated_at            TIMESTAMP      NOT NULL

------------------------------------------------------------------------

## Service

  Campo                     Tipo            Restricciones
  ------------------------- --------------- -----------------------------
  id                        UUID            PK
  professional_profile_id   UUID            FK → ProfessionalProfile.id
  name                      VARCHAR(150)    NOT NULL
  description               TEXT            NULL
  delivery_type             VARCHAR(30)     NOT NULL
  requires_birth_data       BOOLEAN         NOT NULL
  duration_minutes          INTEGER         NULL
  max_delivery_days         INTEGER         NULL
  price                     DECIMAL(10,2)   NOT NULL
  currency                  VARCHAR(10)     NOT NULL
  color                     VARCHAR(20)     NULL
  is_online                 BOOLEAN         NOT NULL
  status                    VARCHAR(20)     NOT NULL
  created_at                TIMESTAMP       NOT NULL
  updated_at                TIMESTAMP       NOT NULL

------------------------------------------------------------------------

## Availability

  Campo                          Tipo        Restricciones
  ------------------------------ ----------- -----------------------------
  id                             UUID        PK
  professional_profile_id        UUID        FK → ProfessionalProfile.id
  day_of_week                    SMALLINT    NOT NULL
  start_time                     TIME        NOT NULL
  end_time                       TIME        NOT NULL
  appointment_interval_minutes   INTEGER     NOT NULL
  is_available                   BOOLEAN     NOT NULL
  created_at                     TIMESTAMP   NOT NULL
  updated_at                     TIMESTAMP   NOT NULL

------------------------------------------------------------------------

## Booking

  Campo                      Tipo            Restricciones
  -------------------------- --------------- -----------------------------
  id                         UUID            PK
  client_id                  UUID            FK → User.id
  professional_profile_id    UUID            FK → ProfessionalProfile.id
  service_id                 UUID            FK → Service.id
  service_name               VARCHAR(150)    NOT NULL
  service_price              DECIMAL(10,2)   NOT NULL
  service_duration_minutes   INTEGER         NULL
  delivery_type              VARCHAR(30)     NOT NULL
  booking_date               DATE            NULL
  start_time                 TIME            NULL
  end_time                   TIME            NULL
  birth_date                 DATE            NULL
  birth_time                 TIME            NULL
  birth_place                VARCHAR(255)    NULL
  client_notes               TEXT            NULL
  status                     VARCHAR(30)     NOT NULL
  created_at                 TIMESTAMP       NOT NULL
  updated_at                 TIMESTAMP       NOT NULL
  cancelled_at               TIMESTAMP       NULL

------------------------------------------------------------------------

## Payment

  Campo                     Tipo            Restricciones
  ------------------------- --------------- -----------------
  id                        UUID            PK
  booking_id                UUID            FK → Booking.id
  amount                    DECIMAL(10,2)   NOT NULL
  currency                  VARCHAR(10)     NOT NULL
  payment_method            VARCHAR(50)     NOT NULL
  payment_provider          VARCHAR(50)     NOT NULL
  provider_transaction_id   VARCHAR(255)    NULL
  status                    VARCHAR(30)     NOT NULL
  paid_at                   TIMESTAMP       NULL
  created_at                TIMESTAMP       NOT NULL
  updated_at                TIMESTAMP       NOT NULL

------------------------------------------------------------------------

## Notification

  Campo        Tipo           Restricciones
  ------------ -------------- -----------------
  id           UUID           PK
  user_id      UUID           FK → User.id
  booking_id   UUID           FK → Booking.id
  type         VARCHAR(50)    NOT NULL
  channel      VARCHAR(30)    NOT NULL
  title        VARCHAR(150)   NOT NULL
  message      TEXT           NOT NULL
  status       VARCHAR(30)    NOT NULL
  sent_at      TIMESTAMP      NULL
  created_at   TIMESTAMP      NOT NULL

------------------------------------------------------------------------

# 4. Relaciones

-   User 1:1 ProfessionalProfile
-   ProfessionalProfile 1:N Service
-   ProfessionalProfile 1:N Availability
-   User 1:N Booking
-   ProfessionalProfile 1:N Booking
-   Service 1:N Booking
-   Booking 1:1 Payment
-   User 1:N Notification

------------------------------------------------------------------------

# 5. Diagrama Entidad-Relación

> Mantener sincronizado el diagrama Mermaid con las tablas anteriores.
> El bloque Mermaid definitivo se actualizará conforme evolucione el
> modelo durante la implementación.

------------------------------------------------------------------------

# 6. Cardinalidades

  Relación                             Cardinalidad
  ------------------------------------ --------------
  User → ProfessionalProfile           1 : 1
  ProfessionalProfile → Service        1 : N
  ProfessionalProfile → Availability   1 : N
  User → Booking                       1 : N
  ProfessionalProfile → Booking        1 : N
  Service → Booking                    1 : N
  Booking → Payment                    1 : 1
  User → Notification                  1 : N

------------------------------------------------------------------------

# 7. Decisiones de diseño

-   El MVP está orientado inicialmente al dominio de la astrología.
-   Un servicio puede entregarse mediante sesión en vivo
    (`LIVE_SESSION`) o informe PDF (`PDF_REPORT`).
-   Algunos servicios requieren fecha, hora y lugar de nacimiento
    (`requires_birth_data`).
-   Booking almacena un snapshot del servicio para preservar el
    historial.
-   El modelo fue diseñado para evolucionar a otros profesionales sin
    modificar su estructura principal.

------------------------------------------------------------------------

# 8. Definition of Done

-   [x] Entidades identificadas.
-   [x] Relaciones documentadas.
-   [x] Cardinalidades definidas.
-   [x] Claves primarias y foráneas documentadas.
-   [x] Decisiones de diseño registradas.
-   [x] Documento listo para implementación.
