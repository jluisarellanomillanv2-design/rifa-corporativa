# Corporate Raffle Studio

Aplicación web de rifas corporativas con panel administrativo y pantalla pública festiva.

## Requisitos
Node.js 20+ y npm.

## Inicio
```bash
npm install
npm run dev
```
Abrir `http://localhost:5173/admin` para gestionar y `http://localhost:5173/sorteo` en otra pestaña del **mismo navegador** para proyectar. `npm run build` genera `dist/`.

## Excel
Primera fila con columnas `ID`, `Nombre`, `WhatsApp` (opcional). Los IDs deben ser únicos. Para WhatsApp, usa número internacional con código de país, sin espacios ni signos, por ejemplo `5215512345678` según el número aplicable.

## Funcionamiento
1. Importa participantes.
2. Crea lotes (0 significa sin límite de sorteos).
3. Registra premios, cantidad y lote.
4. Abre la pantalla pública antes de iniciar el sorteo.
5. Selecciona premio y pulsa Iniciar sorteo.
6. Consulta ganadores, exporta CSV o abre WhatsApp con mensaje precargado.

La selección usa `crypto.getRandomValues` con rechazo para evitar sesgo de módulo. Se excluyen personas previamente ganadoras. El ganador se registra al pulsar Iniciar sorteo y la animación de la pantalla pública revela el resultado tras ~4.2 segundos.

## Limitaciones y producción
Esta versión almacena datos en `localStorage`, sin autenticación ni base de datos. Las pestañas del mismo origen y perfil de navegador comparten estado mediante eventos `storage`; **no hay sincronización entre equipos ni garantía transaccional entre operadores simultáneos**. El sorteo se debe operar desde una sola consola. El modo incógnito, borrar datos del navegador o cambiar de equipo puede perder información. Para eventos reales con varios dispositivos: Supabase/PostgreSQL, autenticación, políticas RLS, transacciones del sorteo en servidor, auditoría, sincronización en tiempo real, copias de seguridad y controles de acceso. WhatsApp se abre con texto precargado; el usuario debe confirmar el envío y la app no puede verificar su entrega. Los números personales requieren tratamiento conforme a la normativa de privacidad aplicable.
