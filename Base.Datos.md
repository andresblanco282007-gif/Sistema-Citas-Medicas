# Esquema de Base de Datos - Sistema de Citas Médicas (`citas_medicas_db`)

## 📋 Descripción General
El sistema utiliza una base de datos relacional en MySQL / MariaDB bajo acceso por PDO, optimizada para gestionar la información de usuarios, roles, pacientes, médicos, agendas de citas, pagos, medicamentos y la bitácora de auditoría exigida por los estándares SQA.

---

## 🛠️ Estructura de Tablas

### 1. Tabla: `roles`
Almacena los perfiles de acceso y permisos del sistema.
* `id` (INT, PK, Auto-increment)
* `nombre` (VARCHAR 50) — Ej: *Administrador, Médico, Paciente, Recepcionista*
* `descripcion` (TEXT)

### 2. Tabla: `usuarios`
Gestiona las credenciales de acceso y la relación con los roles.
* `id` (INT, PK, Auto-increment)
* `rol_id` (INT, FK hacia `roles`)
* `email` (VARCHAR 100, UNIQUE)
* `password` (VARCHAR 255, Hashed)
* `estado` (ENUM: *activo, inactivo*)
* `created_at` (TIMESTAMP)

### 3. Tabla: `pacientes`
Información detallada de los pacientes registrados en el sistema.
* `id` (INT, PK, Auto-increment)
* `usuario_id` (INT, FK hacia `usuarios`)
* `nombres` (VARCHAR 100)
* `apellidos` (VARCHAR 100)
* `telefono` (VARCHAR 20)
* `fecha_nacimiento` (DATE)
* `archivo_adjunto` (VARCHAR 255) — Ruta del documento o historia clínica adjunta.

### 4. Tabla: `especialidades`
Catálogo de especialidades médicas disponibles en la clínica.
* `id` (INT, PK, Auto-increment)
* `nombre` (VARCHAR 100)
* `descripcion` (TEXT)

### 5. Tabla: `medicos`
Información de los profesionales de la salud adscritos.
* `id` (INT, PK, Auto-increment)
* `usuario_id` (INT, FK hacia `usuarios`)
* `especialidad_id` (INT, FK hacia `especialidades`)
* `nombres` (VARCHAR 100)
* `apellidos` (VARCHAR 100)
* `horario_atencion` (TEXT)

### 6. Tabla: `citas`
Control de agendamiento, reprogramación y estado de las consultas médicas.
* `id` (INT, PK, Auto-increment)
* `paciente_id` (INT, FK hacia `pacientes`)
* `medico_id` (INT, FK hacia `medicos`)
* `fecha_hora_cita` (DATETIME)
* `estado` (ENUM: *pendiente, confirmada, cancelada, completada*)
* `codigo_reserva` (VARCHAR 50, UNIQUE)

### 7. Tabla: `pagos`
Registro financiero asociado a las consultas o servicios médicos prestados.
* `id` (INT, PK, Auto-increment)
* `cita_id` (INT, FK hacia `citas`)
* `monto` (DECIMAL 10,2)
* `metodo_pago` (ENUM: *efectivo, tarjeta, transferencia*)
* `estado_pago` (ENUM: *pendiente, pagado, reembolsado*)
* `fecha_pago` (TIMESTAMP)

### 8. Tabla: `medicamentos`
Catálogo farmacéutico gestionado por la clínica.
* `id` (INT, PK, Auto-increment)
* `nombre_comercial` (VARCHAR 100)
* `principio_activo` (VARCHAR 100)
* `stock` (INT)

### 9. Tabla: `auditoria_sistema` (Relacionada con RF-06)
Bitácora de trazabilidad para registrar acciones críticas de los usuarios en cumplimiento con las normas SQA.
* `id` (INT, PK, Auto-increment)
* `usuario_id` (INT, FK hacia `usuarios`)
* `accion` (VARCHAR 100) — Ej: *INSERT, UPDATE, DELETE*
* `tabla_afectada` (VARCHAR 50)
* `detalle_cambio` (TEXT)
* `fecha_registro` (TIMESTAMP)
