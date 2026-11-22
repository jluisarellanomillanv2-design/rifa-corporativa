# Prompt maestro — Corporate Raffle Studio

Actúa como arquitecto de software senior, desarrollador full-stack, diseñador UX/UI y director de arte de eventos corporativos. Desarrolla una aplicación web funcional para administrar rifas corporativas y presentar premios y ganadores en una pantalla pública Full HD 1920 × 1080.

## Requisitos confirmados
- Dos vistas independientes: `/admin` para organizadores y `/sorteo` para proyección pública.
- Importar colaboradores desde Excel `.xlsx`, `.xls` o CSV. Columnas `ID`, `Nombre`, `WhatsApp` opcional. Validar y deduplicar por ID de empleado, conservar ceros iniciales si el Excel los contiene como texto, y reportar filas rechazadas.
- Cada colaborador puede ganar **una sola vez en todo el evento**. Aplicar la regla de elegibilidad de forma atómica.
- Sorteo **manual**, iniciado por el administrador para el premio elegido.
- Registrar premios con nombre, descripción, imagen, cantidad y lote. Controlar inventario automáticamente.
- Configurar lotes con nombre, premios asociados y límite máximo de unidades sorteadas por lote. Impedir superar límites o inventario.
- Elegir ganador mediante aleatoriedad criptográficamente segura, sin sesgo de módulo. No confundir la animación con el resultado: registrar selección y mostrar revelación posterior.
- Mostrar en pantalla pública un premio destacado, animación de suspenso, nombre del ganador, confeti y transiciones festivas. Interfaz adaptativa para pantallas LED y proyectores, accesible, legible a distancia y optimizada para 1920 × 1080.
- Guardar historial de ganadores con ID, nombre, premio, lote, fecha/hora y estado de notificación/entrega.
- Botón individual para abrir WhatsApp con texto personalizado prellenado; no afirmar que se envió hasta confirmación explícita. Validar teléfono con prefijo internacional.
- Exportar ganadores en Excel o CSV.
- Vista admin con indicadores de participantes, premios restantes, lotes y ganadores.
- Diseño festivo de calidad premium: degradados violeta, magenta y coral, iluminación suave, iconografía, confeti, microinteracciones y tipografía clara. No saturar el diseño.

## Arquitectura solicitada
Frontend React + TypeScript + Vite + Tailwind CSS; componentes reutilizables; animaciones Framer Motion; backend Supabase/PostgreSQL con autenticación de organizadores, RLS y suscripciones Realtime. La pantalla pública solo lee el estado permitido. Sorteo en una función transaccional del servidor para impedir duplicados incluso con varios administradores. Separar entidades `participants`, `lots`, `prizes`, `draws`, `winners`, `event_state`, `audit_log`. Agregar índices, restricciones únicas y pruebas de concurrencia. Incluir migraciones SQL, variables de entorno de ejemplo, instrucciones de despliegue y datos ficticios de prueba.

## Seguridad y confiabilidad
Evitar exponer teléfonos en la pantalla pública. Autenticación y autorización de admin. Validar importaciones, sanear campos y URLs, evitar CSV injection en exportaciones, realizar copias de seguridad y permitir exportación de emergencia. Crear modo ensayo que nunca afecte resultados reales. Registrar eventos de auditoría y ofrecer recuperación ante fallas de conectividad. Considerar consentimiento y retención de datos personales.

## Entregables
1. Código fuente completo, organizado por módulos y listo para instalar.
2. Diseño responsive del administrador y pantalla pública Full HD.
3. Modelo de datos, migraciones, políticas de acceso y función transaccional de sorteo.
4. Importador de Excel con reporte de errores.
5. Integración manual WhatsApp mediante enlace oficial `wa.me`.
6. Pruebas de reglas: un ganador por participante, límite de lotes, inventario, concurrencia, sorteos sin participantes elegibles.
7. README de instalación, despliegue y operación del evento.

Primero presenta el mapa de arquitectura y luego genera todos los archivos reales. No entregues pseudocódigo ni componentes simulados. Diferencia claramente prototipo local y solución de producción. No afirmes que una funcionalidad existe sin implementarla.
