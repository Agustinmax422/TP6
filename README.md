# 🛠️ TP N° 6: Gestión de Memoria Principal

**Universidad Nacional de Jujuy (UNJu) — Facultad de Ingeniería**  
**Cátedra:** Teoría de Sistemas Operativos (TSO)  
**Ciclo Lectivo:** 2026  
**Responsable de Cátedra:** Ing. María Fernanda Vázquez  
**JTP:** Ing. Fabio D. Argañaraz  

[![GitHub Classroom Autograding](https://github.com/UNJU-Teoria-de-Sistemas-Operativos/TP6/actions/workflows/classroom.yml/badge.svg)](https://github.com/UNJU-Teoria-de-Sistemas-Operativos/TP6/actions/workflows/classroom.yml)

---

## 🎯 Objetivos del Trabajo Práctico

- Analizar las distintas maneras de cargar y organizar procesos en la memoria principal (particiones fijas y variables).
- Comprender visual y cuantitativamente los fenómenos de **fragmentación interna**, **fragmentación externa** y el rol de la compactación de memoria.
- Dominar los algoritmos de colocación: **Primer Ajuste**, **Mejor Ajuste**, **Peor Ajuste**, **Siguiente Ajuste** y el **Sistema del Compañero (Buddy System)**.
- Comprender el funcionamiento de la **Unidad de Gestión de Memoria (MMU)** en esquemas no contiguos: **Paginación Simple**, **Segmentación Pura** y **Segmentación Paginada**.
- Validar las funciones de protección por hardware (límites y permisos) y detectar fallos de página y violaciones de acceso (*segmentation faults*).

---

## 📚 Mapa Bibliográfico Obligatorio

Para resolver los laboratorios interactivos y los problemas analíticos, consulta la siguiente bibliografía oficial:

| Tema | Libro de Referencia | Capítulo |
| :--- | :--- | :--- |
| **Requerimientos y Particiones** | Silberschatz, *Fundamentos de SO* (7ma Ed.) | Cap. 8.1 - 8.3 |
| **Estrategias de Colocación y Buddy System** | Tanenbaum, *Sistemas Operativos Modernos* / Stallings | Cap. 3.2 / Cap. 7.2 |
| **Paginación Simple y Tablas de Páginas** | Silberschatz, *Fundamentos de SO* (7ma Ed.) | Cap. 8.4 - 8.5 |
| **Segmentación Simple y Paginada** | Silberschatz / Tanenbaum | Cap. 8.6 - 8.7 / Cap. 3.4 |

> 💡 **Diapositivas Oficiales:** Guíate con las diapositivas de la cátedra: **U6 - Gestión de Memoria**.

---

## 🚀 Guía de Autoevaluación y Laboratorios Prácticos

### 1️⃣ Estructura del Trabajo Práctico

Este TP se desarrolla a través de un entorno interactivo visual de simulación y resolución conceptual analítica:

- **Simuladores Interactivos en `index.html`:**
  - 🧠 **Laboratorio 1: Colocación en Particiones Variables:** Comparativa visual en tiempo real de *Primer*, *Mejor*, *Peor* y *Siguiente Ajuste* con barra de memoria proporcional, detección de fragmentación externa y compactación dinámica.
  - 🌲 **Laboratorio 2: Sistema de Compañeros (Buddy System):** Árbol binario de partición en potencias de dos (2^k) partiendo de 512 KB, con división de bloques y fusión (*coalescing*) automática.
  - 📑 **Laboratorio 3: Traducción MMU en Paginación Simple:** Desglose binario de la dirección lógica en número de página (*p*) y desplazamiento (*d*), consulta interactiva de tabla de páginas, cálculo de dirección física en RAM y alerta de fallos de página.
  - 🛡️ **Laboratorio 4: Segmentación y Validación por Hardware:** Simulación del comparador MMU (*d < Límite*), cálculo de *DF = Base + d* y captura de trampas de excepción (*Segmentation Fault*).

- **Guía Práctica de Laboratorios (`guia_laboratorio.md`):**
  - Manual de experimentación guiada con valores numéricos específicos para cada simulador.
  - Fenómenos a observar (residuos, fragmentación interna, trampas de hardware).
  - Matriz de correspondencia directa con los 12 ejercicios de autoevaluación.

- **Modelado Lógico y Problemas Analíticos (`modelado_logico.md`):**
  - Demostración formal de la Regla del 50% de Donald Knuth.
  - Derivación matemática del tamaño óptimo de página ($s^* = \sqrt{2 \cdot p \cdot e}$).
  - Pseudocódigo algorítmico estructurado de la rutina de MMU para Segmentación Paginada.

---

### 2️⃣ Clonar y Configurar

```bash
git clone https://github.com/TU_USUARIO/TP6.git
cd TP6
```

---

### 3️⃣ Resolver la Evaluación Web Interactiva (`index.html`)

1. Abre `index.html` en cualquier navegador web moderno (no requiere instalar dependencias ni servidores).
2. Experimenta con los 4 simuladores y resuelve los **12 ejercicios conceptuales y prácticos**.
3. Ingresa tu Nombre, Apellido y Libreta Universitaria en el encabezado.
4. Cuando el progreso indique **100% Completado**, se habilitará el botón **Exportar Respuestas (.json)**.
5. Guarda el archivo descargado con el nombre exacto `respuestas_tp6.json` en la raíz de tu repositorio.

---

### 4️⃣ Probar la Autoevaluación en Local

Puedes verificar tu nota oficial en tu propia computadora ejecutando el evaluador automático:

```bash
python autograder_tp6.py
```

El script verificará tus respuestas contra la rúbrica criptográfica de cátedra y emitirá tu reporte oficial de autograding con tu puntaje sobre 10.0.

---

### 5️⃣ Entrega en GitHub Classroom

Cuando el evaluador local apruebe:

```bash
# 1. Agrega tu archivo de respuestas:
git add respuestas_tp6.json

# 2. Realiza el commit:
git commit -m "Entrega TP6 - [Tu Nombre y Apellido]"

# 3. Envía los cambios al repositorio remoto:
git push origin main
```

> 💡 **Nota:** Al hacer el `git push`, el workflow de GitHub Actions evaluará automáticamente tu entrega y registrará tu calificación final.
