## Módulos y cohesión

| Proceso de nivel 1 | En una oración | Cohesión | Decisión de diseño |
|---|---|---|---|
| 1 Gestionar inventario | Registra movimientos de stock y registra apartados de productos. | Comunicacional: las dos tareas usan el almacén Productos. | Se divide en los submódulos de su nivel 2 (1.1 a 1.5), que son funcionales. Razón: la oración lleva «y» y son dos eventos distintos (movimiento y apartado). El proceso 1 queda solo como agrupador. |
| 2 Generar reportes de ganancias | Calcula las ganancias y entrega el corte diario y el reporte de ganancias. | Comunicacional: las dos tareas leen el almacén Movimientos. | Se divide en dos módulos: Generar corte diario y Generar reporte de ganancias, cada uno funcional. Razón: son eventos distintos (fin de día y fin de mes) con destinatarios distintos (Usuario Final y Administrador). Un solo módulo «generar reporte(tipo)» caería en cohesión lógica. |
| 3 Administrar cuentas y suscripciones | Guarda la configuración de una cuenta y registra la contratación de un cliente. | Comunicacional: las dos tareas escriben el almacén Cuentas. | Se divide en dos módulos: Configurar cuenta y Registrar contratación, cada uno funcional. Razón: los dispara gente distinta (Administrador y Cliente) y tienen respuestas distintas. |

## Acoplamiento

| Entre | Qué comparten | Acoplamiento | Decisión de diseño |
|---|---|---|---|
| 1.3 Actualizar existencias → 1.5 Emitir alerta de stock crítico | Datos de existencia (nombre del producto, existencia actual, stock mínimo) | De datos | Se queda así. Razón: solo viajan los tres datos que la alerta necesita, no el registro completo del producto, así que no cae en acoplamiento estampado. |
| 1.2 Clasificar instrucción → 1.3 Actualizar existencias y 1.4 Registrar apartado | Movimiento a registrar o apartado a registrar (producto, cantidad y, en el movimiento, si es entrada o salida) | De datos | Se queda así. Razón: 1.2 llama directamente al módulo que corresponde según lo que dijo el usuario, y no le manda una bandera que le diga cómo comportarse. Si 1.3 cambiara todo su comportamiento según una bandera, sería de control. |
| 1.3 Actualizar existencias y 1.4 Registrar apartado | Los dos escriben en Productos | Común | 1.3 es el dueño de Productos. 1.4 solo le pide descontar la cantidad apartada y no escribe el almacén por su cuenta. Razón: así hay un solo módulo responsable de ese almacén. |
| 1 Gestionar inventario y 2 Generar reportes de ganancias | Los dos usan Movimientos | Común, aunque solo uno escribe | 1.3 es el único módulo que escribe Movimientos. El proceso 2 solo lo consulta pidiendo «los movimientos del día» o «del mes» y no accede por su cuenta. Razón: así no se rompe si cambia cómo se guardan los movimientos. |
| Configurar cuenta y Registrar contratación | Los dos escriben en Cuentas | Común | Configurar cuenta es el dueño de Cuentas. Registrar contratación le pide crear la suscripción y no escribe el almacén directamente. Razón: igual que en Productos, un solo dueño por almacén. |

### Dueños de los almacenes

| Almacén | Módulo dueño (único que lo escribe) |
|---|---|
| Productos | 1.3 Actualizar existencias |
| Movimientos | 1.3 Actualizar existencias |
| Apartados | 1.4 Registrar apartado |
| Cuentas | Configurar cuenta |

## Uso de IA

| Herramienta | Para qué la usaron | Qué verificaron |
|---|---|---|
| Claude | Apoyo para proponer la clasificación de cohesión, los pares de acoplamiento y las decisiones de diseño a partir de nuestro DFD de nivel 1 y nivel 2 | Que cada oración de la tabla de cohesión describiera lo que hace el proceso en nuestro DFD, que los nombres de procesos, submódulos y almacenes coincidieran con los diagramas, que cada decisión de dividir tuviera una razón y que cada almacén escrito por dos módulos tuviera un solo dueño |