# Checkpoint 4 – Sincronización del Cerebro Agéntico con Ecosistemas de Negocio

## Descripción del proyecto

Este workflow forma parte del proyecto integrador desarrollado en n8n y evolucionado desde el Módulo 3.

Su objetivo es automatizar la recepción, interpretación y gestión inicial de consultas de clientes mediante un sistema multiagente conectado con herramientas externas.

## Arquitectura e integraciones

El sistema integra las siguientes herramientas:

- **Gmail:** recepción de correos electrónicos y generación de borradores para revisión humana.
- **Airtable:** almacenamiento, búsqueda, creación y actualización de contactos.
- **Telegram:** envío de notificaciones al canal de comunicación del proyecto mediante un bot.

## Funcionamiento del workflow

1. Gmail Trigger detecta nuevos correos.
2. Un nodo IF identifica y descarta respuestas automáticas y remitentes no-reply.
3. Edit Fields organiza los datos de entrada.
4. AI Agent interpreta el mensaje utilizando el contexto y la memoria del proyecto.
5. Edit Fields limpia y estructura el payload.
6. Airtable Search Records verifica si el contacto ya existe.
7. Un IF deriva el procesamiento hacia Update Record o Create Record.
8. Gmail Create Draft genera una respuesta pendiente de aprobación humana.
9. Telegram envía una notificación sobre el procesamiento realizado.

## Controles preventivos

- Filtro anti auto-reply para prevenir bucles infinitos.
- Búsqueda previa en Airtable para evitar contactos duplicados.
- Limpieza y selección de campos para reducir el tamaño del payload.
- Creación de borradores en lugar de envíos automáticos.
- Notificaciones internas para facilitar el seguimiento operativo.

## Pruebas realizadas

Se realizaron pruebas manuales de los siguientes escenarios:

- Procesamiento de un contacto nuevo.
- Actualización de un contacto existente.
- Filtrado de correos automáticos.
- Generación de borradores en Gmail.
- Recepción de notificaciones mediante Telegram.

## Archivos

- `checkpoint4_sebastian_rios.json`: workflow exportado desde n8n.

## Consideraciones de autenticación

Las conexiones de Gmail y Airtable utilizan las credenciales configuradas en n8n. Telegram utiliza un bot autenticado mediante token de acceso.

Las credenciales y secretos no forman parte de los archivos públicos del repositorio.


