#  Gestión de Bases de Datos - ClimAir S.L.

Este módulo contiene el diseño, implementación y administración del sistema de base de datos relacional para **ClimAir S.L.**, sustituyendo la gestión mediante archivos planos por una infraestructura robusta en **MySQL**.

##  1. Análisis de Datos
El sistema centraliza la información crítica para garantizar la integridad y el cumplimiento de la normativa **ISO 27001**:
* **Técnicos**: Registro del personal operativo vinculado a sus usuarios de sistema (ISO) para asegurar el no repudio 
* **Clientes**: Directorio de instalaciones (viviendas y centros comerciales como CC Islazul) para optimizar la logística 
* **Intervenciones**: Núcleo de la actividad donde se monitorizan equipos y estados de trabajo (Pendiente, Activo, Finalizado)
* **Facturación**: Gestión financiera con relación 1:1 respecto a las intervenciones finalizadas

##  2. Diseño de la Base de Datos
La estructura ha sido diseñada siguiendo un modelo relacional normalizado (3FN) para eliminar redundancias:
* **Diagrama Entidad-Relación**: Diseñado en Draw.io con cardinalidades 1:N (Técnico-Intervención) y 1:1 (Intervención-Factura) 
* **Integridad Referencial**: Implementación de Claves Primarias (PK) y Claves Foráneas (FK) para asegurar la coherencia de los datos.

##  3. Implementación SQL
El despliegue en el entorno **localhost** incluye:
* **Tipos de Datos Óptimos**: Uso de `DECIMAL(10,2)` para precisión en facturas 
* **Script de Creación**: Definición de tablas con el motor de almacenamiento estándar del servidor.
* **Script de Inserción**: Carga inicial de datos basada en el histórico del proyecto (Pepe, María, Juan).

##  4. Control de Acceso (DCL)
Se aplica el principio de **mínimo privilegio** para proteger los activos de la empresa:
* [cite_start]**ana_admin**: Acceso total (`ALL PRIVILEGES`) para la gestión administrativa y financiera 
* **pepe_tecnico**: Permisos restringidos. [cite_start]Solo lectura de clientes e intervenciones, y actualización limitada a los campos de estado y descripción 

##  5. Consultas de Administración
El sistema permite la extracción de información estratégica mediante:
* **JOINs Complejos**: Relación entre técnicos, equipos y estados de intervención.
* **Filtros Operativos**: Identificación de trabajos pendientes y cálculo de facturación mensual.

---
**Tecnología**: MySQL 
**Diseño**: Draw.io  
**Entorno**: Localhost / Ubuntu 24.04 LTS

Responsable: Alejandro Sánchez Abellán Proyecto: Intermodular ASIR 2025-2026
