# F1 Telemetry Panel

Panel web para controlar el mod **F1 Telemetry** por WebSocket. Es un solo archivo (`index.html`), sin dependencias ni compilación, y no forma parte del mod.

## Uso

1. En Minecraft: `/f1 token create admin` (o `read` para solo mirar).
2. Abre `index.html` en el navegador (doble clic, o sírvelo con `python3 -m http.server`).
3. Pon host, puerto (por defecto 8765) y el token, y pulsa **Conectar**.

También sirve un enlace directo: `index.html#host=mi.servidor&port=8765&token=XXXX` conecta al abrirlo y borra el token de la barra de direcciones.

El token es de **un solo uso**: si te desconectas, hay que generar otro.

## Qué hace

- **Directo**: clasificación con gaps e intervalos en vivo, vueltas, mejor vuelta (morado la de la sesión), boxes y sanciones; reloj, vuelta del líder y bandera. Mapa con la trazada, los checkpoints y los coches moviéndose (interpolados); rueda para zoom, arrastrar para mover, y opción de pegar los coches a la línea.
- **Sesión**: crear sesión, preparar parrilla, salida, finalizar y abortar; banderas; inscribir, reordenar y quitar pilotos de la parrilla.
- **Equipos y pilotos**: crear, editar color y borrar equipos; registrar, editar, cambiar de equipo o estado, y quitar pilotos.
- **Sanciones**: emitir, marcar como cumplidas y anular.
- **Registro**: eventos del servidor (vueltas, sectores, boxes, sanciones, eventos personalizados).

Con un token `read` todo se ve pero los botones de cambio quedan desactivados.

## Notas

- El mapa necesita que la pista tenga vuelta de referencia, y los coches solo se ven con la sesión en `GRID` o `RUNNING` y pilotos inscritos y conectados.
- El mod usa `ws://` sin cifrar. Si sirves la web por `https://`, el navegador bloqueará `ws://`: usa un proxy con TLS y marca `wss`, o abre la web desde un archivo local o `http://`.
- El mapeo de pista (crear pistas y checkpoints) solo existe como comandos de Minecraft.
