# Práctica 4 — Diagrama de contexto

**Equipo:** SIX SEVENS
**Sistema:** Socio Agente IA
**Integrantes:** Salazar Camargo Sebastián, Migoya Suárez Daniela Valentina

---

## Parte A — Entidades externas y flujos

| Entidad externa | Datos que le entrega al sistema | Datos que recibe del sistema |
|---|---|---|
| Usuario Final | Movimientos de stock, mensajes/audios con pedidos o apartados, solicitudes de corte diario | Confirmaciones de registro, alertas de stock crítico, resumen de corte diario |
| Administrador | Solicitudes de soporte, configuración de cuentas y suscripciones | Reportes de ganancias brutas y netas, estado de las bases de datos de sus clientes |
| Cliente | Datos de pago y contratación del servicio | Confirmación de suscripción activa, acceso habilitado al sistema |
| Servicio de IA (API externa) | Audio o texto interpretado que reenvía al sistema | Audio o mensaje coloquial del Usuario Final que necesita interpretación |

**¿Qué quedó fuera del sistema y por qué?**

> Consideramos a Telegram como entidad externa, pero lo descartamos porque no es un participante con necesidades propias: es únicamente el canal por el que el Usuario Final envía y recibe información. Los datos reales viajan entre el Usuario Final y el sistema; Telegram solo los transporta, por lo que no aporta ni recibe información en nombre propio.

---

## Parte C — Declaración de propósito

> Socio Agente IA existe para ayudar a negocios pequeños de catálogo, que aún llevan sus cuentas en papel, a controlar su stock, apartados y finanzas de forma automática y sencilla. Sirve principalmente al dueño o encargado del negocio (Usuario Final), y su beneficio es ahorrarle tiempo y reducir errores al reemplazar el cuaderno y las cuentas manuales por un asistente accesible desde el chat.

---

## Parte D — Contenido de los flujos

| Flujo | Origen → Destino | Datos que contiene |
|---|---|---|
| Registro de movimiento de stock | Usuario Final → Sistema | Nombre del producto, cantidad, tipo de movimiento (entrada/salida) |
| Solicitud de apartado | Usuario Final → Sistema | Producto, cantidad, nombre del cliente que aparta |
| Alerta de stock crítico | Sistema → Usuario Final | Nombre del producto, cantidad actual, stock mínimo |
| Corte diario | Sistema → Usuario Final | Total de ventas, movimientos del día, ganancias brutas y netas |
| Configuración de cuentas | Administrador → Sistema | Datos de la cuenta del negocio, plan contratado, estado de la suscripción |
| Reporte de ganancias | Sistema → Administrador | Ganancias brutas y netas por negocio, estado de las bases de datos de sus clientes |
| Interpretación de mensaje/audio | Sistema → Servicio de IA (API externa) | Audio o texto coloquial enviado por el Usuario Final |
| Texto interpretado | Servicio de IA (API externa) → Sistema | Comando o instrucción ya interpretada en texto estructurado |
| Datos de contratación y pago | Cliente → Sistema | Nombre del cliente, plan elegido, datos de pago |
| Confirmación de suscripción | Sistema → Cliente | Estado de la suscripción, acceso habilitado |

---

## Declaración de uso de IA

| Herramienta | Para qué la usaron | Qué verificaron |
|---|---|---|
| Claude | Apoyo para estructurar la tabla de entidades externas y flujos del diagrama de contexto a partir del E1 ya elaborado | Que las entidades, roles y datos coincidieran con los participantes y funciones reales definidos en E1, sin inventar información nueva |