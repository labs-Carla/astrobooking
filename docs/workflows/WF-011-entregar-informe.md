## WF-011 Entregar informe PDF

### Objetivo

Permitir que un profesional entregue un informe personalizado en formato PDF al cliente una vez finalizada su elaboración, notificando la disponibilidad del documento.

---

### Actores

* **Principal:** Profesional
* **Secundario:** Sistema
* **Secundario:** Cliente

---

### Precondiciones

* Existe una reserva en estado **CONFIRMED**.
* La reserva corresponde a un servicio de tipo **PDF_REPORT**.
* El pago fue realizado exitosamente.
* El informe ha sido elaborado por el profesional.

---

### Flujo principal

1. El profesional accede al detalle de la reserva.
2. El sistema muestra la información del servicio solicitado.
3. El profesional adjunta el informe en formato PDF.
4. El profesional confirma la entrega.
5. El sistema valida el archivo.
6. El sistema almacena el informe.
7. El sistema cambia el estado de la reserva a **DELIVERED**.
8. El sistema registra la fecha de entrega.
9. El sistema genera una notificación para el cliente.
10. El cliente accede a la plataforma.
11. El cliente descarga el informe PDF.
12. El proceso finaliza.

---

### Flujos alternativos

#### A1. Archivo inválido

1. El sistema detecta un archivo inválido o no soportado.
2. El sistema informa el error.
3. El profesional adjunta un nuevo archivo.
4. El flujo retorna al paso 4.

---

#### A2. La reserva fue cancelada

1. El sistema detecta que la reserva fue cancelada.
2. El sistema impide la entrega del informe.
3. El proceso finaliza.

---

#### A3. Error al almacenar el archivo

1. El sistema detecta un error durante el almacenamiento.
2. El sistema registra el incidente.
3. El estado de la reserva permanece sin cambios.
4. El proceso finaliza.

---

#### A4. Error al enviar la notificación

1. El informe se almacena correctamente.
2. El sistema no logra enviar la notificación.
3. El sistema registra el incidente.
4. El proceso finaliza.

---

### Postcondiciones

* El informe queda almacenado en la plataforma.
* La reserva cambia al estado **DELIVERED**.
* El cliente puede descargar el informe.
* El profesional conserva el historial de entregas.

---

### Reglas de negocio

* RN-056 Solo las reservas de tipo **PDF_REPORT** pueden finalizar mediante la entrega de un informe.
* RN-057 El informe solo puede entregarse cuando la reserva se encuentre en estado **CONFIRMED**.
* RN-058 El sistema debe almacenar el documento antes de cambiar el estado de la reserva.
* RN-059 Toda entrega debe generar una notificación al cliente.
* RN-060 El cliente podrá acceder al informe desde el historial de reservas.

---

### Requerimientos funcionales relacionados

* FR-04 Servicios
* FR-06 Reservas
* FR-08 Notificaciones

---

### Historias de usuario relacionadas

* US-009 Comprar un informe PDF.
* US-010 Realizar el pago de un servicio.
* US-015 Descargar un informe PDF.
