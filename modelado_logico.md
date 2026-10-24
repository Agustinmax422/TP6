# 📐 Modelado Lógico y Problemas Analíticos - TP N° 6
## Cátedra de Teoría de Sistemas Operativos — UNJu FI 2026

Este documento contiene los problemas analíticos formales y de modelado lógico de gestión de memoria. Deberás resolverlos en pseudocódigo o mediante deducción matemática formal en tu cuaderno de cátedra o informe adjunto.

---

### Problema 1: Demostración Analítica de la Regla del 50% (Donald Knuth)
En un sistema con asignación contigua mediante particiones variables e intercambio (*swapping*) continuo en estado estacionario:
1. Sea $N$ el número promedio de procesos cargados en memoria física.
2. Cada proceso se encuentra ubicado de forma contigua en RAM.
3. Se asume que la probabilidad de que un proceso sea adyacente a un hueco libre o a otro proceso es equilibrada, y que dos huecos contiguos siempre se fusionan inmediatamente (*coalescing*).
4. **Consigna:**
   - Demuestra analíticamente por qué la cantidad esperada de huecos libres dispersos tiende asintóticamente a $H \approx 0.5 \times N$.
   - Calcula qué porcentaje del número total de particiones de memoria representan los huecos libres.
   - Explica el impacto de este fenómeno sobre el rendimiento de las estrategias de *Primer Ajuste* y *Mejor Ajuste*.

---

### Problema 2: Derivación Matemática del Tamaño Óptimo de Página
La elección del tamaño de página ($s$ bytes) en un sistema con paginación simple representa un compromiso de diseño de hardware:
- Si las páginas son muy grandes, aumenta el desperdicio por **fragmentación interna** en el último marco del proceso (que en promedio es $s / 2$ bytes por proceso).
- Si las páginas son muy pequeñas, la fragmentación interna disminuye, pero la **tabla de páginas** crece significativamente, ocupando memoria física valiosa: cada entrada de la tabla requiere $e$ bytes, y para un proceso de tamaño medio $p$ bytes se necesitan $p / s$ entradas, requiriendo un espacio de $(p \cdot e) / s$ bytes por proceso.
- **Consigna:**
   - Plantea la función de pérdida de memoria total $f(s) = \frac{s}{2} + \frac{p \cdot e}{s}$.
   - Deriva formalmente respecto de $s$ para encontrar el tamaño óptimo de página $s^*$ que minimiza la pérdida global.
   - Aplica la fórmula obtenida para un proceso de tamaño medio $p = 2\text{ MB}$ ($2^{21}$ bytes) con entradas de tabla de $e = 4\text{ bytes}$. Redondea a la potencia de dos más cercana.

---

### Problema 3: Arquitectura de Segmentación Paginada y Traducción en Dos Niveles
Considera un procesador con arquitectura de 32 bits que implementa **Segmentación Paginada**:
- La dirección lógica consta de 3 campos: $\langle s, p, d \rangle$, donde:
  - $s$: 8 bits para el número de segmento (indexa la Tabla de Segmentos).
  - $p$: 12 bits para el número de página dentro del segmento (indexa la Tabla de Páginas del segmento).
  - $d$: 12 bits para el desplazamiento dentro de la página.
- **Consigna:**
   1. Determina el tamaño de página y el tamaño máximo de cada segmento.
   2. Calcula la cantidad máxima de segmentos por proceso y la cantidad máxima de páginas por segmento.
   3. Diseña en pseudocódigo algorítmico estructurado la rutina de la MMU que toma una dirección lógica $\langle s, p, d \rangle$, consulta el registro base de la tabla de segmentos (`STBR`), verifica el límite de páginas del segmento, traduce a la dirección física de 32 bits y genera las trampas (*traps*) correspondientes si se detecta un acceso inválido.
