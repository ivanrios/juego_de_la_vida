# Juego de la Vida · Conway

Implementación del autómata celular de John Conway en un único archivo HTML, ejecutable directamente en el navegador sin dependencias.

---

## ¿Qué es el Juego de la Vida?

Creado por el matemático **John Conway** en 1970, el Juego de la Vida es un *autómata celular*: un universo simulado en una cuadrícula infinita donde cada celda puede estar **viva** o **muerta**. El tiempo avanza en generaciones discretas y la evolución completa del sistema queda determinada por cuatro reglas simples aplicadas simultáneamente a todas las celdas.

No hay jugadores ni objetivos. Es un ejemplo canónico de **emergencia**: comportamientos complejos que surgen de reglas elementales.

---

## Las cuatro reglas

| # | Regla | Condición | Resultado |
|---|-------|-----------|-----------|
| 1 | **Supervivencia** | Celda viva con 2 o 3 vecinos vivos | Sobrevive |
| 2 | **Soledad** | Celda viva con < 2 vecinos vivos | Muere |
| 3 | **Superpoblación** | Celda viva con > 3 vecinos vivos | Muere |
| 4 | **Nacimiento** | Celda muerta con exactamente 3 vecinos vivos | Nace |

Los vecinos se cuentan en las 8 direcciones (Moore neighborhood).

---

## Patrones incluidos

### Naves espaciales
- **Glider** — La nave más famosa: 5 células que viajan en diagonal indefinidamente. Fue el primer patrón móvil descubierto (Richard Guy, 1970).
- **Nave espacial ligera (LWSS)** — El oscilador desplazante más pequeño posible, período 4. Se mueve horizontalmente.

### Osciladores
- **Pulsar** — El oscilador más célebre: período 3, simetría cuádruple, 48 células. Pulsa entre tres estados distintos.

### Crecimiento infinito
- **Cañón de Gliders (Gosper)** — El primer patrón con crecimiento infinito de población (1970). Dispara un nuevo glider cada 30 generaciones sin detenerse jamás.
- **Crecimiento infinito (10 células)** — Solo 10 células en línea que producen crecimiento ilimitado.

### Patrones caóticos / metaestables
- **R-pentominó** — Solo 5 células que tardan **1 103 generaciones** en estabilizarse, generando gliders y estructuras complejas en el proceso.
- **Bellota (Acorn)** — 7 células que tardan **5 206 generaciones** en estabilizarse, produciendo 633 células vivas y 13 gliders libres.
- **Diehard** — Un patrón que desaparece completamente en exactamente **130 generaciones**, sin dejar ningún rastro.

---

## Uso

Abre `index.html` en cualquier navegador moderno. No requiere servidor ni instalación.

```
open index.html
```

### Controles

| Acción | Control |
|--------|---------|
| Jugar / Pausar | Botón o `Espacio` |
| Avanzar un paso | Botón o `S` |
| Limpiar tablero | Botón o `C` |
| Dibujar células | Clic o arrastrar sobre el canvas |
| Borrar células | Clic sobre una célula viva |
| Cargar patrón | Seleccionar en el menú y pulsar "Cargar" |
| Ajustar velocidad | Deslizador (1–60 fps) |
| Ajustar tamaño de celda | Deslizador (4–24 px) |

---

## Propiedades teóricas notables

- **Turing-completo**: el Juego de la Vida puede simular cualquier máquina de Turing. Se han construido computadoras, procesadores y hasta el propio Juego de la Vida dentro de él.
- **Problema de la parada**: es indecidible en general saber si un patrón inicial estabilizará o crecerá infinitamente.
- **Jardín del Edén**: existen configuraciones que no pueden surgir de ningún estado anterior (sin preimagen).

---

## Estructura del proyecto

```
juego_de_la_vida/
└── index.html    # Todo el juego: HTML + CSS + JS en un único archivo
```
