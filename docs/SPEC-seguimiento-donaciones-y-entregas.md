# SPEC: Seguimiento de donantes, familias y entregas

**Producto:** DESPENSA  
**Estado:** Propuesta para validar con la organización comunitaria  
**Tipo:** Nueva característica  
**Usuarios principales:** Coordinación y voluntariado del banco de alimentos

## 1. Problema

DESPENSA registra familias, donaciones, inventario y entregas, pero necesita criterios claros para aceptar donaciones y registrar familias, además de indicadores que permitan saber si los alimentos se entregan de forma trazable, oportuna y equitativa. Sin esos criterios, los registros pueden ser incompletos y el equipo no puede evaluar los resultados de la distribución.

## 2. Objetivo

Definir un flujo sencillo para registrar y validar donantes, familias y entregas, y un resumen de métricas para que la organización pueda detectar brechas de atención, desperdicio y errores de inventario.

La herramienta ayuda a organizar la decisión; no reemplaza el criterio del equipo ni las políticas locales de elegibilidad.

## 3. Alcance

- Registrar donantes identificados o anónimos y asociarlos con sus donaciones.
- Aplicar criterios de recepción de alimentos antes de incorporarlos al inventario.
- Registrar familias con la información mínima necesaria y una decisión de elegibilidad tomada por personal autorizado.
- Registrar la entrega por familia, fecha, alimentos y cantidades, conservando el aviso existente de entregas recientes.
- Mostrar métricas de entregas y cobertura en el resumen.
- Mantener la operación simple y comprensible para voluntarios con poca experiencia digital.

### Fuera de alcance

- Recibos fiscales o comprobantes con validez tributaria.
- Evaluación automática de la situación socioeconómica de una familia.
- Rechazo automático de una entrega por una distribución reciente.
- Sincronización entre dispositivos, cuentas de usuario o almacenamiento en la nube. Actualmente los datos se guardan en el navegador de un dispositivo.

## 4. Perfiles y reglas operativas

### 4.1 Donantes y aceptación de donaciones

Una persona, comercio, organización o grupo comunitario puede donar. No se debe exigir información de contacto para aceptar una donación; el registro puede quedar como **donante anónimo**.

Una donación de alimentos se acepta para inventario cuando:

1. El producto está identificado y su cantidad es verificable.
2. Se conoce la unidad de medida de la cantidad.
3. El alimento está cerrado o en condiciones higiénicas y seguras para su distribución, según las normas locales aplicables.
4. Se registra una fecha de vencimiento o consumo preferente cuando corresponda. Si no puede determinarse y la organización no puede verificar su seguridad, no se incorpora al inventario distribuible.
5. Se registra el donante o se marca expresamente como anónimo.
6. El equipo puede almacenar y conservar el producto de forma segura, incluida la cadena de frío cuando sea necesaria.

Los productos vencidos, con envase dañado o señales de contaminación no se registran como disponibles para entrega. El sistema debe permitir dejar constancia de una donación rechazada y su motivo, sin sumarla al inventario.

### 4.2 Familias

La organización define y comunica sus reglas locales de elegibilidad antes de iniciar el registro. Las reglas deben ser consistentes, respetuosas y no discriminatorias. DESPENSA no determina por sí sola quién merece ayuda.

Una familia puede quedar registrada para evaluación cuando:

1. La persona responsable proporciona un nombre o identificador práctico para reconocer el registro.
2. Se registra el número de integrantes, si está disponible; si falta, se solicita completarlo antes de usar métricas por persona, pero no se bloquea por sí solo el registro de atención.
3. El personal autorizado confirma la elegibilidad según la política comunitaria, o deja el estado como **pendiente de revisión**.
4. Se revisa si ya existe un registro equivalente para evitar duplicados, sin impedir la atención urgente por una posible coincidencia.
5. Solo se recopilan datos necesarios para organizar la ayuda; la información sensible no es requisito predeterminado.

Los estados de familia deben distinguir **pendiente**, **elegible**, **no elegible** e **inactiva**, con motivo de decisión cuando corresponda. Una familia pendiente o inactiva no aparece como elegible en las métricas de cobertura. El equipo puede registrar una entrega excepcional y documentar el motivo.

## 5. Requisitos funcionales

### RF-1. Registro del donante

- Permitir identificar al donante por nombre o marcarlo como anónimo.
- Permitir guardar un medio de contacto opcional solo cuando sea necesario y autorizado.
- Asociar cada lote recibido con su donante, fecha de recepción, producto, cantidad, unidad y fecha de vencimiento cuando aplique.
- No solicitar ni generar datos para recibos fiscales.

### RF-2. Recepción de donaciones

- Registrar el resultado de recepción como **aceptada** o **rechazada**.
- Para una donación aceptada, validar los datos mínimos y sumar la cantidad al inventario disponible.
- Para una rechazada, guardar el motivo y no modificar el inventario.
- Excluir del flujo normal de entrega los lotes vencidos o no aptos.
- Registrar la baja de unidades vencidas o dañadas con lote, cantidad, fecha y motivo, sin contabilizarlas como entregadas.

### RF-3. Registro y elegibilidad de familias

- Capturar identificador/nombre y tamaño del hogar, manteniendo el tamaño como dato corregible.
- Guardar el historial de estados de elegibilidad con fecha y responsable; el motivo es obligatorio para decisiones de no elegibilidad y excepciones.
- Avisar de posibles duplicados para revisión humana.
- Restringir los datos visibles a los necesarios para la operación local; no exponer detalles sensibles en el resumen general.

### RF-4. Registro de entregas

- Exigir una familia, fecha no futura, al menos un producto disponible y una cantidad positiva que no exceda el inventario apto.
- Permitir entregas ordinarias a familias elegibles. Para una familia pendiente o no elegible, requerir autorización y motivo de excepción.
- Guardar familia, fecha, artículos, cantidades y voluntario responsable. La nota es opcional.
- Descontar del inventario exactamente las cantidades registradas y conservar el historial.
- Advertir si la familia recibió apoyo en los últimos siete días. La advertencia no bloquea la entrega; al continuar, se registra si fue una excepción y su motivo.
- Priorizar los lotes con vencimiento más próximo que sigan aptos para consumo.

### RF-5. Resumen de resultados

- Mostrar las métricas de éxito definidas en la sección 7, con período visible y denominadores consultables.
- Permitir distinguir familias elegibles, pendientes e inactivas para no presentar una cobertura engañosa.
- Mostrar un mensaje cuando no haya datos suficientes para calcular una métrica, en vez de mostrar cero como si fuera un resultado real.

## 6. Criterios de aceptación funcionales

### Donantes y donaciones

1. **Donante anónimo:** Dado que se recibe una donación sin datos de identidad, cuando el voluntario la registra como anónima con producto, cantidad y unidad, entonces se puede aceptar y asociar el lote con “Anónimo”.
2. **Datos incompletos:** Dado que falta producto, cantidad o unidad, cuando se intenta aceptar la donación, entonces el sistema señala el campo faltante y no suma existencias.
3. **Producto no apto:** Dado que el alimento está vencido, dañado o no puede verificarse como seguro, cuando se registra la recepción como rechazada, entonces se guarda el motivo y no queda disponible para entregas.
4. **Trazabilidad:** Dada una donación aceptada, cuando se consulta su lote, entonces se puede identificar su fecha de recepción, origen (donante o anónimo), cantidad y vencimiento cuando corresponda.
5. **Baja de inventario:** Dado un lote vencido o dañado, cuando el voluntario registra la cantidad retirada y su motivo, entonces esa cantidad deja de estar disponible, queda asociada al lote y no aparece como una entrega a una familia.

### Familias

1. **Registro pendiente:** Dado que una familia proporciona un identificador o nombre, cuando todavía no se ha evaluado su elegibilidad, entonces queda registrada como pendiente y no se cuenta como elegible en la cobertura.
2. **Elegibilidad:** Dada una familia evaluada por una persona autorizada según la política de la organización, cuando se marca elegible, entonces aparece como candidata a recibir entregas y se incluye en el denominador de cobertura del período en que esté activa.
3. **Datos mínimos:** Dado que no se conoce el tamaño del hogar, cuando se registra la familia, entonces se permite continuar sin inventar ese dato y se indica que falta para análisis por persona.
4. **Posible duplicado:** Dado que existe una familia con identificador similar, cuando se intenta crear otra, entonces se advierte al voluntario y se permite revisar o continuar con confirmación; no se fusionan registros automáticamente.
5. **No elegible:** Dada una decisión de no elegibilidad, cuando se guarda, entonces se requiere un motivo y la familia no se cuenta como elegible ni recibe entregas ordinarias.
6. **Atención excepcional:** Dada una familia pendiente o no elegible con una necesidad urgente, cuando el equipo autoriza una entrega, entonces se registra como excepción con motivo y no se altera silenciosamente su estado de elegibilidad.

### Entregas y métricas

1. **Validación y descuento:** Dada una entrega válida, cuando se confirma, entonces se guarda el detalle y el inventario disminuye por la cantidad exacta entregada.
2. **Inventario insuficiente o lote vencido:** Dado un lote sin cantidad suficiente o vencido, cuando se intenta entregar, entonces se impide guardar esa cantidad y no se modifica el inventario.
3. **Entrega reciente:** Dada una entrega previa a la misma familia dentro de siete días, cuando se registra otra, entonces se muestra una advertencia; si el equipo continúa, se solicita y guarda el motivo de excepción.
4. **Cálculo auditable:** Dado un período con entregas registradas, cuando se muestra una métrica, entonces se indica período, numerador y denominador, y el resultado coincide con el historial filtrado.
5. **Sin datos:** Dado que el denominador está vacío o no se han registrado entregas, cuando se muestran métricas, entonces se indica “Sin datos suficientes” y no se presenta un porcentaje calculado.

## 7. Métricas de éxito de las entregas

Los objetivos numéricos siguientes son **metas iniciales para un piloto**, no resultados actuales. Deben revisarse con la organización después de recopilar una línea base de al menos un mes. La cobertura se interpreta condicionada a que exista inventario apto suficiente.

| Métrica | Cálculo | Período | Meta inicial |
|---|---|---|---|
| Entregas trazables | Entregas con familia, fecha, al menos un artículo y cantidades válidas ÷ total de entregas registradas × 100 | Mensual | 100% |
| Cobertura de familias elegibles | Familias elegibles activas con al menos una entrega ÷ total de familias elegibles activas × 100 | Mensual | ≥ 80%, si hay existencias aptas suficientes |
| Brecha de atención | Familias elegibles activas sin entrega durante el período ÷ total de familias elegibles activas × 100 | Mensual | ≤ 20%, si hay existencias aptas suficientes |
| Exactitud del inventario | Registros de entrega cuyo descuento coincide con las cantidades confirmadas ÷ total de entregas × 100 | Mensual, mediante revisión de muestra | 100% |
| Desperdicio por vencimiento | Cantidad de una cohorte de recepción retirada por vencimiento sin entregarse ÷ cantidad aceptada en esa misma cohorte × 100 | Por cohorte, al vencer los lotes; por producto y unidad comparable | Reducir ≥ 20% frente a la línea base tras 3 meses |
| Atención repetida documentada | Entregas dentro de los siete días de otra entrega que guardan autorización/motivo ÷ total de entregas dentro de ese intervalo × 100 | Mensual | 100% |

**Reglas de interpretación:**

- Para cobertura y brecha, el denominador incluye únicamente familias elegibles y activas al cierre del período. Mostrar además el número excluido por estado pendiente o inactivo.
- Si no hay suficiente inventario apto, reportar la limitación junto al indicador; no atribuir automáticamente la brecha a una falla del equipo.
- No sumar unidades incompatibles (por ejemplo, kilogramos y paquetes) en un único total de desperdicio. Calcular por producto/unidad y agregar solo unidades comparables.
- La métrica de vencimiento requiere registrar las bajas del inventario y comparar cada cohorte de donaciones cuando sus lotes hayan vencido; no atribuir a una cohorte unidades de otra.
- La meta de reducción de vencimientos compara cohortes y categorías equivalentes con la línea base; si todavía no existe línea base, mostrar el valor observado sin calificarlo como éxito o fracaso.
- Las métricas se calculan con los registros locales del dispositivo y no representan datos de otros navegadores o voluntarios.

## 8. Requisitos no funcionales

- Interfaz en español, con etiquetas claras, mensajes de error accionables y controles accesibles desde celular o computadora.
- El flujo principal debe ser comprensible para voluntarios con poca experiencia digital.
- No guardar información de contacto ni datos sensibles sin necesidad operativa.
- Informar claramente que la información permanece en el navegador del dispositivo y no se comparte automáticamente.
- Las métricas deben poder verificarse contra el historial; los avisos no deben bloquear atención urgente por sí solos.

## 9. Supuestos y decisiones pendientes

- La organización definirá y documentará los alimentos aceptables, el manejo de productos perecederos y sus reglas locales de elegibilidad.
- La organización debe acordar quién puede aprobar familias y excepciones de entrega.
- Las metas de cobertura y reducción de vencimientos se validarán durante el piloto y se ajustarán a la disponibilidad real de alimentos.
- Para comparar resultados entre voluntarios y dispositivos será necesario definir, en una fase futura, una estrategia de sincronización y protección de datos.
