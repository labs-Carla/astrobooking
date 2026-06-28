## WF-005 Comprar un informe PDF

### Objetivo

Permitir que un cliente solicite y compre un informe personalizado en formato PDF ofrecido por un profesional, proporcionando la información necesaria para su elaboración.

---

### Actores

* **Principal:** Cliente
* **Secundario:** Sistema
* **Secundario:** Profesional

---

### Precondiciones

* El cliente ha iniciado sesión.
* La cuenta del cliente se encuentra activa.
* El perfil del profesional está publicado.
* El servicio seleccionado se encuentra activo.
* El servicio corresponde al tipo **PDF_REPORT**.

---

### Flujo principal

1. El cliente accede al perfil del profesional.
2. El sistema muestra los servicios disponibles.
3. El cliente selecciona un servicio de tipo **PDF_REPORT**.
4. El sistema muestra la descripción, tiempo estimado de entrega y precio del servicio.
5. Si el servicio requiere datos natales, el sistema solicita:

   * Fecha de nacimiento.
   * Hora de nacimiento.
   * Lugar de nacimiento.
6. El cliente puede agregar notas adicionales o preguntas para el profesional.
7. El cliente confirma la solicitud.
8. El sistema valida la información ingresada.
9. El sistema crea la reserva con estado **PENDING_PAYMENT**.
10. El sistema almacena un snapshot del servicio (nombre, precio, tiempo estimado de entrega y tipo de entrega).
11. El sistema redirige al cliente al proceso de pago.

---

### Flujos alternativos

#### A1. Datos natales incompletos

1. El sistema detecta que faltan datos obligatorios.
2. El sistema informa los campos requeridos.
3. El cliente completa la información.
4. El flujo retorna al paso 7.

---

#### A2. El servicio ya no se encuentra disponible

1. El sistema detecta que el servicio fue desactivado.
2. El sistema informa la situación.
3. El proceso finaliza.

---

#### A3. Información inválida

1. El sistema detecta errores en la información proporcionada.
2. El sistema informa los errores encontrados.
3. El cliente corrige la información.
4. El flujo retorna al paso 7.

---

### Postcondiciones

* Se crea una nueva reserva.
* La reserva queda en estado **PENDING_PAYMENT**.
* Se almacena un snapshot del servicio.
* Se inicia el proceso de pago.

---

### Reglas de negocio

* RN-025 Solo los servicios de tipo **PDF_REPORT** siguen este flujo.
* RN-026 Los servicios que requieren datos natales no podrán solicitarse sin dicha información.
* RN-027 Los informes PDF no requieren seleccionar una fecha ni un horario.
* RN-028 La reserva debe almacenar un snapshot del servicio adquirido.
* RN-029 Toda solicitud inicia con estado **PENDING_PAYMENT**.
* RN-030 Una vez confirmado el pago, la reserva cambiará al estado **CONFIRMED** y quedará disponible para que el profesional inicie su elaboración.

---

### Requerimientos funcionales relacionados

* FR-04 Servicios
* FR-06 Reservas
* FR-07 Pagos

---

### Historias de usuario relacionadas

* US-006 Consultar servicios.
* US-009 Comprar un informe PDF.
* US-010 Realizar el pago de un servicio.
