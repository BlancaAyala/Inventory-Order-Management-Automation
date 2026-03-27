📊 Automatización de gestión de pedidos e inventario

n8n • Google Sheets • PostgreSQL • Email Automation


📖 Overview

Este proyecto implementa un sistema de automatización de gestión de pedidos e inventario, diseñado para procesar solicitudes registradas en Google Sheets y mantener actualizado el inventario de forma automática.
El sistema elimina la necesidad de revisar manualmente cada pedido, permitiendo:
validar solicitudes
comprobar disponibilidad de stock
actualizar inventario en tiempo real
registrar resultados automáticamente
enviar notificaciones por correo
El workflow está desarrollado en n8n, actuando como motor de automatización entre Google Sheets, base de datos e integración de correo electrónico.


🚀 Features

Procesamiento automático de pedidos desde Google Sheets
Validación de datos (filtrado de registros incompletos)
Consulta de inventario en base de datos
Actualización automática de stock
Registro de resultados en la hoja de cálculo
Gestión de errores (productos sin stock)
Envío de resumen por email
Procesamiento en bucle de múltiples solicitudes


🏗️ System Architecture

Google Sheets (Orders)


        ↓
n8n Trigger (on update)

        ↓
Data Filtering (valid records)

        ↓
Loop (each order)

        ↓
Inventory Check (Database)

        ↓
Decision:
   → Stock available → Update inventory
   → No stock → Mark as error
   
        ↓
Update Google Sheets

        ↓
Aggregate results

        ↓
Send Email Notification


⚙️ Workflow Explanation

1. Google Sheets Trigger
El flujo se activa automáticamente cuando se detecta una actualización en la hoja de cálculo que contiene las solicitudes de pedidos.
2. Data Filtering
Se filtran los registros para procesar únicamente aquellos que contienen información válida (por ejemplo, solicitudes con correo electrónico).
3. Loop Processing
El sistema recorre cada solicitud individualmente mediante un bucle, permitiendo procesar múltiples pedidos de forma escalable.
4. Inventory Query
Para cada solicitud, se consulta la base de datos para verificar la disponibilidad del producto, teniendo en cuenta atributos como:
producto
talla o variante
cantidad solicitada
5. Availability Check
Se evalúa si existe suficiente inventario:
Si hay stock → se continúa con el proceso
Si no hay stock → se marca la solicitud como error
6. Inventory Update
Cuando hay disponibilidad:
se calcula el nuevo stock
se actualiza la base de datos
7. Google Sheets Update
Se actualiza la hoja de cálculo con el resultado:
pedido procesado correctamente
error por falta de stock
8. Error Handling
Las solicitudes sin disponibilidad se registran como incidencias para su revisión posterior.
9. Data Aggregation & Notification
Una vez procesadas todas las solicitudes:
se agrupan los resultados
se envía un email con el resumen de operaciones


🛠️ Technologies Used

n8n — automatización de workflows
Google Sheets API — gestión de pedidos
PostgreSQL / Database — control de inventario
Email Service (SMTP / Gmail) — notificaciones
Custom Logic (n8n nodes) — validación y procesamiento


▶️ Setup & Installation

Requisitos
Instancia de n8n (self-hosted o cloud)
Cuenta de Google con acceso a Google Sheets
Base de datos (PostgreSQL recomendado)
Servicio de correo electrónico (SMTP o Gmail)
Pasos
1. Importar el workflow en n8n
2. Configurar credenciales de Google Sheets
3. Configurar conexión a la base de datos
4. Configurar servicio de correo electrónico
5. Definir estructura de la hoja de pedidos
6. Activar el workflow

   
📌 Use Cases

Gestión automatizada de pedidos en e-commerce
Procesamiento de solicitudes internas de productos
Control de inventario en tiempo real
Automatización de formularios conectados a Google Sheets
Sistemas de gestión sin ERP complejo


📈 Future Improvements

Integración con sistemas de pago
Notificaciones automáticas al cliente
Dashboard de inventario en tiempo real
Sistema de alertas por bajo stock
Integración con CRM o ERP
Gestión de múltiples almacenes


🧩 Key Highlights

Este proyecto demuestra:
Automatización de procesos operativos reales
Integración de múltiples sistemas (Sheets + DB + Email)
Diseño de workflows escalables
Manejo de lógica condicional y control de errores
Aplicación directa en entornos empresariales


📄 License

Uso educativo y demostrativo. Adaptable a entornos empresariales.
