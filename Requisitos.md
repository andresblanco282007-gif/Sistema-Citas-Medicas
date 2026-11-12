# Requisitos Funcionales del Sistema (Sistema-Citas)

* **RF-01: Registro y Autenticación de Usuarios**
  El sistema debe permitir el registro de nuevos usuarios (pacientes y personal médico) validando su correo electrónico y asignando un rol específico en la plataforma con diferentes niveles de acceso

* **RF-02: Búsqueda y Filtrado de Especialidades Médicas**
  El sistema debe permitir a los pacientes buscar profesionales de la salud filtrando por especialidad médica, ubicación del centro de salud, disponibilidad horaria y nombre del medico

* **RF-03: Agendamiento de Citas Médicas**
  El sistema debe permitir a los pacientes seleccionar un espacio de tiempo disponible en la agenda del médico seleccionado y confirmar la reserva de la cita, generando un comprobante digital

* **RF-04: Cancelación y Reprogramación de Citas**
  El sistema debe permitir a los usuarios cancelar o solicitar la reprogramación de una cita médica activa con un tiempo límite de anticipación de al menos 24 horas antes de la hora programada

* **RF-05: Generación de Notificaciones y Recordatorios**
  El sistema debe enviar notificaciones automáticas (por correo electrónico o SMS) al paciente para confirmar la creación de una cita y recordatorios programados 24 horas y 2 horas antes de la consulta
  
* **RF-06: Auditoría y Trazabilidad Avanzada de Cambios (Mejora)**
  El sistema debe registrar, almacenar y consultar de forma automatizada una bitácora detallada de auditoría para todas las acciones críticas ejecutadas por los usuarios (creaciones, modificaciones y eliminaciones), asegurando la trazabilidad estricta de los datos bajo estándares de calidad SQA
