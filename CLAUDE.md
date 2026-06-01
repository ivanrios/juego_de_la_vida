# CLAUDE.md — Juego de la Vida

## Qué es este proyecto

Implementación del autómata celular de Conway en un único archivo `index.html` sin dependencias externas. El objetivo es mantenerlo simple y autocontenido: todo el HTML, CSS y JS vive en ese archivo.

## Arquitectura

- **Un solo archivo**: `index.html` contiene todo. No hay build, bundler ni framework.
- **Canvas API**: el tablero se renderiza con `<canvas>`. El loop usa `requestAnimationFrame` con control de fps manual.
- **Representación de celdas**: `Set<string>` donde cada string es `"row,col"`. Evita un array 2D y permite tableros grandes con poblaciones dispersas.
- **Algoritmo de paso**: se recorren solo las celdas vivas y sus vecinas (candidatos), no toda la cuadrícula. Complejidad O(células vivas), no O(filas × columnas).

## Decisiones de diseño

- El tablero se ajusta automáticamente al tamaño de la ventana (`resize()`). `ROWS` y `COLS` se recalculan en función de `CELL` (tamaño de celda en px).
- Los bordes son **muros**: las células no envuelven al otro lado. Los vecinos fuera de rango se ignoran.
- Las celdas se dibujan con padding de 1px cuando `CELL >= 6`, lo que da aspecto de cuadrícula sin necesidad de dibujar líneas en densidades altas.
- La cuadrícula de fondo solo se dibuja cuando `CELL >= 7` para evitar ruido visual a escalas pequeñas.

## Patrones disponibles

Definidos en el objeto `PATTERNS` dentro del script. Cada patrón tiene:
- `desc`: string descriptivo que se muestra bajo los controles.
- `shape`: array de `[row, col]` relativo a la esquina superior-izquierda del patrón, centrado automáticamente por `loadShape()`.
- O bien `load()`: función personalizada (usado por "aleatorio").

Para añadir un nuevo patrón: agregar una entrada en `PATTERNS`, añadir el `<option>` correspondiente en `#sel-pattern`.

## Estilo visual

- Fondo: `#0d0d14` (azul muy oscuro)
- Células vivas: `#4ade80` (verde)
- Cuadrícula: `#12121e` (apenas visible)
- Paleta de UI: grises azulados, acentos en verde `#4ade80` y azul `#60a5fa`
- Fuente: `Segoe UI`, system-ui

## Lo que NO tiene (decisiones conscientes)

- Sin wrap-around de bordes (se puede añadir como opción)
- Sin historial / undo
- Sin zoom/pan del canvas
- Sin persistencia de estado
- Sin soporte táctil (mobile)
- Sin tests

## Comandos útiles

```bash
# Abrir en Chrome (macOS)
open -a "Google Chrome" index.html

# Servir localmente si se quiere
python3 -m http.server 8080
```
