## Agrupación del nivel 1

| Proceso de nivel 1 | Agrupa (procesos preliminares) | Criterio |
|---|---|---|
| 1 Gestionar inventario | 1 Registrar movimiento de stock + 2 Registrar apartado | Misma entidad externa (Usuario Final), mismo almacén (Productos) y misma área de negocio (inventario) |
| 2 Generar reportes de ganancias | 3 Generar corte diario + 5 Generar reporte de ganancias | Ambos son eventos temporales que leen el almacén Movimientos y calculan ganancias |
| 3 Administrar cuentas y suscripciones | 4 Configurar cuenta + 6 Registrar contratación | Ambos escriben el almacén Cuentas y pertenecen al área de cuentas y suscripciones |

Almacenes en el nivel 1: Movimientos (lo escribe el 1 y lo lee el 2) y Cuentas (lo escribe el 3 y lo lee el 2). Productos y Apartados solo los usa el proceso 1, por eso aparecen hasta su nivel 2.

## Balanceo del nivel 1

| Flujo del contexto | Dirección | Proceso del nivel 1 |
|---|---|---|
| Registro de movimiento de stock | Usuario Final → Sistema | 1 Gestionar inventario |
| Solicitud de apartado | Usuario Final → Sistema | 1 Gestionar inventario |
| Alerta de stock crítico | Sistema → Usuario Final | 1 Gestionar inventario |
| Interpretación de mensaje/audio | Sistema → Servicio de IA | 1 Gestionar inventario |
| Texto interpretado | Servicio de IA → Sistema | 1 Gestionar inventario |
| Corte diario | Sistema → Usuario Final | 2 Generar reportes de ganancias |
| Reporte de ganancias | Sistema → Administrador | 2 Generar reportes de ganancias |
| Configuración de cuentas | Administrador → Sistema | 3 Administrar cuentas y suscripciones |
| Datos de contratación y pago | Cliente → Sistema | 3 Administrar cuentas y suscripciones |
| Confirmación de suscripción | Sistema → Cliente | 3 Administrar cuentas y suscripciones |

Están los 10 flujos del contexto, con los mismos nombres y las mismas entidades. No hay entidades nuevas. El nivel 1 está balanceado.

## Balanceo del nivel 2 – proceso 1

| Flujo del proceso 1 (nivel 1) | Subproceso del nivel 2 |
|---|---|
| Registro de movimiento de stock (entra, de Usuario Final) | 1.1 Enviar mensaje a interpretación |
| Solicitud de apartado (entra, de Usuario Final) | 1.1 Enviar mensaje a interpretación |
| Interpretación de mensaje/audio (sale, al Servicio de IA) | 1.1 Enviar mensaje a interpretación |
| Texto interpretado (entra, del Servicio de IA) | 1.2 Clasificar instrucción |
| Movimiento registrado (sale, al almacén Movimientos) | 1.3 Actualizar existencias |
| Alerta de stock crítico (sale, al Usuario Final) | 1.5 Emitir alerta de stock crítico |

Están los 6 flujos del padre con el mismo nombre. Los flujos entre subprocesos (Movimiento a registrar, Apartado a registrar, Datos de existencia) y los de los almacenes Productos y Apartados son internos y no cruzan la frontera del proceso 1.

## Uso de IA

| Herramienta | Para qué la usaron | Qué verificaron |
|---|---|---|
| Claude | Apoyo para proponer la agrupación del nivel 1 y generar el código de los diagramas de nivel 1 y nivel 2 | (completen ustedes: por ejemplo, que los 10 flujos del contexto aparezcan con el mismo nombre, que ningún proceso quede sin entrada o salida y que no haya flechas entre procesos ni entre almacenes) |