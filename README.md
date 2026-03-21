# 🗄️ Gestión de Bases de Datos - ClimAir S.L.

Este módulo contiene el diseño, implementación y administración del sistema de base de datos relacional para **ClimAir S.L.**, sustituyendo la gestión mediante archivos planos por una infraestructura robusta en **MySQL**.

## 📊 1. Análisis de Datos
El sistema centraliza la información crítica para garantizar la integridad y el cumplimiento de la normativa **ISO 27001**:
* [cite_start]**Técnicos**: Registro del personal operativo vinculado a sus usuarios de sistema (ISO) para asegurar el no repudio [cite: 96-99, 1076-1079].
* [cite_start]**Clientes**: Directorio de instalaciones (viviendas y centros comerciales como CC Islazul) para optimizar la logística [cite: 1043-1046, 1083-1087].
* [cite_start]**Intervenciones**: Núcleo de la actividad donde se monitorizan equipos y estados de trabajo (Pendiente, Activo, Finalizado) [cite: 1047-1053, 1088-1095].
* [cite_start]**Facturación**: Gestión financiera con relación 1:1 respecto a las intervenciones finalizadas [cite: 1080-1082, 1099].

## 📐 2. Diseño de la Base de Datos
La estructura ha sido diseñada siguiendo un modelo relacional normalizado (3FN) para eliminar redundancias:
* [cite_start]**Diagrama Entidad-Relación**: Diseñado en Draw.io con cardinalidades 1:N (Técnico-Intervención) y 1:1 (Intervención-Factura) [cite: 1098-1100].
* **Integridad Referencial**: Implementación de Claves Primarias (PK) y Claves Foráneas (FK) para asegurar la coherencia de los datos.

## 💻 3. Implementación SQL
El despliegue en el entorno **localhost** incluye:
* [cite_start]**Tipos de Datos Óptimos**: Uso de `DECIMAL(10,2)` para precisión en facturas y `ENUM` para estados de trabajo[cite: 1082, 1092].
* **Script de Creación**: Definición de tablas con el motor de almacenamiento estándar del servidor.
* **Script de Inserción**: Carga inicial de datos basada en el histórico del proyecto (Pepe, María, Juan).

## 🔐 4. Control de Acceso (DCL)
Se aplica el principio de **mínimo privilegio** para proteger los activos de la empresa:
* [cite_start]**ana_admin**: Acceso total (`ALL PRIVILEGES`) para la gestión administrativa y financiera [cite: 1063-1066].
* **pepe_tecnico**: Permisos restringidos. [cite_start]Solo lectura de clientes e intervenciones, y actualización limitada a los campos de estado y descripción [cite: 1063-1066].

## 🔍 5. Consultas de Administración
El sistema permite la extracción de información estratégica mediante:
* **JOINs Complejos**: Relación entre técnicos, equipos y estados de intervención.
* **Filtros Operativos**: Identificación de trabajos pendientes y cálculo de facturación mensual.

## 💾 6. Tareas de Administración
* **Backups**: Generación de copias de seguridad lógicas mediante `mysqldump`.
* **Exportación**: Capacidad de volcar datos a CSV/SQL para reportes externos.

---
**Tecnología**: MySQL / MariaDB  
**Diseño**: Draw.io  
**Entorno**: Localhost / Ubuntu 24.04 LTS
