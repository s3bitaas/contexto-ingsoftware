## Lista de eventos

| # | Evento | Tipo | Flujo de entrada | Respuesta del sistema |
|---|--------|------|------------------|-----------------------|
| 1 | Usuario Final registra un movimiento de stock | Flujo | Registro de movimiento de stock | Envía el mensaje o audio al Servicio de IA para interpretarlo, actualiza las existencias del producto, guarda el movimiento y entrega al Usuario Final una alerta de stock crítico si la existencia queda por debajo del mínimo. |
| 2 | Usuario Final aparta un producto para un cliente | Flujo | Solicitud de apartado | Envía el mensaje o audio al Servicio de IA para interpretarlo, verifica que haya existencia, guarda el apartado y descuenta la cantidad apartada del stock disponible. |
| 3 | Es fin de día | Temporal | (ninguno) | Suma las ventas y los movimientos del día, calcula las ganancias brutas y netas y entrega el corte diario al Usuario Final. |
| 4 | Administrador configura la cuenta de un negocio | Flujo | Configuración de cuentas | Guarda los datos de la cuenta, el plan contratado y el estado de la suscripción. |
| 5 | Es fin de mes | Temporal | (ninguno) | Calcula las ganancias brutas y netas de cada negocio y entrega el reporte de ganancias, con el estado de las bases de datos de sus clientes, al Administrador. |
| 6 | Cliente contrata el servicio | Flujo | Datos de contratación y pago | Registra al cliente y su suscripción, habilita el acceso al sistema y entrega al Cliente la confirmación de suscripción. |

## Notas

- El flujo «Texto interpretado» (Servicio de IA → Sistema) no es un evento aparte: es la respuesta del Servicio de IA a una petición del propio sistema («Interpretación de mensaje/audio»). Forma parte de la respuesta de los eventos 1 y 2.
- Todos los demás flujos de entrada del diagrama de contexto tienen su evento: Registro de movimiento de stock (1), Solicitud de apartado (2), Configuración de cuentas (4) y Datos de contratación y pago (6).

## Pendientes para el contexto

- La tabla A del contexto menciona «confirmaciones de registro» y «solicitudes de corte diario» del Usuario Final y «solicitudes de soporte» del Administrador, pero no tienen flecha en el diagrama. Si se quedan en el alcance, hay que agregar los flujos al contexto y sus eventos; si no, quitarlos de la tabla A.

## Uso de IA

| Herramienta | Para qué la usaron | Qué verificaron |
|---|---|---|
| Claude | Apoyo para redactar la lista de eventos y armar el código del DFD preliminar a partir del diagrama de contexto | (completen ustedes: por ejemplo, que cada flujo de entrada tenga evento, que ningún evento esté redactado como proceso y que los nombres de flujo coincidan con el contexto) |