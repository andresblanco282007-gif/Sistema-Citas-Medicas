# Plan de Pruebas - Sistema de Citas Médicas

* **CP-01: Validación de Registro de Usuario**
  * **Requisito asociado:** RF-01
  * **Descripción:** Registrar un nuevo usuario con datos válidos en el formulario de inscripción.
  * **Resultado esperado:** El sistema crea el usuario exitosamente, envía un correo de activación y permite iniciar sesión.

* **CP-02: Filtrado por Especialidad Médica**
  * **Requisito asociado:** RF-02
  * **Descripción:** Seleccionar la especialidad "Cardiología" en el buscador de médicos.
  * **Resultado esperado:** El sistema despliega únicamente la lista de médicos activos adscritos a dicha especialidad con sus horarios disponibles.

* **CP-03: Agendamiento Exitoso de Cita**
  * **Requisito asociado:** RF-03
  * **Descripción:** Seleccionar un horario libre de un médico y hacer clic en "Confirmar Cita".
  * **Resultado esperado:** El estado de la cita cambia a "Confirmada", se bloquea el espacio en el calendario del médico y se genera el código de reserva.

* **CP-04: Restricción en Cancelación Fuera de Plazo**
  * **Requisito asociado:** RF-04
  * **Descripción:** Intentar cancelar una cita con menos de 2 horas de anticipación a la hora pactada.
  * **Resultado esperado:** El sistema bloquea la acción de cancelación directa y muestra un mensaje informando que debe comunicarse con el centro médico.

* **CP-05: Envío de Recordatorio Automático**
  * **Requisito asociado:** RF-05
  * **Descripción:** Simular la llegada del hito temporal de 24 horas antes de una cita confirmada.
  * **Resultado esperado:** El sistema despacha de manera automática el correo electrónico de recordatorio al buzón del paciente.

* **CP-06: Verificación de Registro en Bitácora de Auditoría**
  * **Requisito asociado:** RF-06
  * **Descripción:** Simular una modificación de datos críticos en el sistema y comprobar que el módulo registre de forma automática la fecha, el usuario  responsable y los detalles de la acción en la bitácora.
