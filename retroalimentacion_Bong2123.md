# Retroalimentación — Julián Alcalá
**Repo:** https://github.com/Bong2123/diplomado-ml-Julian-Alcala
**Fecha de evaluación:** 2026-05-12
**Calificación final:** 10.0 / 10

## Resumen general
Excelente entrega.

## Desglose por sesión

### Sesión 1 — Instalación y configuración de Python — 1/1 pt
Archivo: `diplomado-ml-Julian-Alcala\MODULO1\sesion 1\sesion1_M1_notebook.ipynb`. 29 de 32 celdas de código con contenido ejecutable.

### Sesión 2 — Tipos de datos básicos — 1/1 pt
Archivo: `diplomado-ml-Julian-Alcala\MODULO1\sesion 2\sesion2_M1_notebook.ipynb`. 30 de 30 celdas de código con contenido ejecutable.

### Sesión 3 — Estructuras de datos + control de flujo — 1/1 pt
Archivo: `diplomado-ml-Julian-Alcala\MODULO1\sesion 3\sesion3_M1_notebook.ipynb`. 30 de 30 celdas de código con contenido ejecutable.

### Sesión 4 — Funciones — 1/1 pt
Archivo: `diplomado-ml-Julian-Alcala\MODULO1\sesion 4\sesion4_M1_notebook_JJAA.ipynb`. 21 de 22 celdas de código con contenido ejecutable.

### Sesión 5 — Módulos / funciones avanzadas — 2.00/2 pts
Archivo: `diplomado-ml-Julian-Alcala\MODULO1\sesion 5\sesion5_M1_notebook_JJAA.ipynb`.
- Notebook ejecutable: **0.5/0.5**
- Ejercicios completos: **0.5/0.5**
- Resultados correctos: **1.0/1.0**
- Las 3 tareas integradoras tienen código.
- Notebook ejecuta end-to-end sin errores.

### Sesión 6 — Módulos propios + inicio de Pandas — 2.0/2 pts
Archivo: `diplomado-ml-Julian-Alcala\MODULO1\sesion 6\sesion6_M1_notebook_JJAA.ipynb`.
- Notebook ejecutable: **0.5/0.5**
- Ejercicios completos: **0.5/0.5**
- Resultados correctos: **1.0/1.0**  _(re-evaluado con comparación numérica estricta contra canónico)_
  - Tarea 1: ✓ correcta (inferida — la tarea final integradora produce el resultado esperado)
  - Tarea 2: ✓ correcta (25/25 números coinciden)
  - Tarea 3: ✓ correcta (13/14 números coinciden)

### Sesión 7 — Pandas avanzado — 2.0/2 pts
Archivo: `diplomado-ml-Julian-Alcala\MODULO1\sesion_7\sesion7_M1_notebook_JJAA.ipynb`.
- Notebook ejecutable: **0.5/0.5**
- Ejercicios completos: **0.5/0.5**
- Resultados correctos: **1.0/1.0**  _(re-evaluado con comparación numérica estricta contra canónico)_
  - Tarea 1: ✓ correcta (15/15 números coinciden)
  - Tarea 2: ✓ correcta (18/18 números coinciden)
  - Tarea 3: ✓ correcta (30/30 números coinciden)
  - Tarea 4: ✓ correcta (12/15 números coinciden)


## Parte 2 — Sesiones 8 y 11

### Sesión 8 — Pipeline Completo — 1.64/2 pts
*(solo se evaluó el Ejercicio Integrador Final)*
- Corre hasta el Integrador: 0.50/0.5
- Integrador Final, 5 fases: 1.14/1.5
  - FASE 1: 1.00*0.3 = 0.30 (numeros coinciden (60% de canon cubierto))
  - FASE 2: 0.55*0.3 = 0.17 (codigo presente ejecuta sin error; numeros no coinciden con canonico)
  - FASE 3: 0.70*0.3 = 0.21 (codigo extenso (18 lineas) ejecuta; printeos no coinciden con canonico)
  - FASE 4: 0.90*0.3 = 0.27 (mayoria de numeros coinciden (37%))
  - FASE 5: 0.65*0.3 = 0.20 (pocas coincidencias numericas (11%); codigo sustantivo y ejecuta)

### Sesión 11 — Práctica Final — 7.12/8 pts
*(solo se evaluó el Ejercicio Integrador Final "Mini Pricing Actuarial")*
- Corre hasta el Integrador: 1.00/1.0
  - FASE 1: 1.00*1.75 = 1.75 (numeros coinciden (66% de canon cubierto))
  - FASE 2: 1.00*1.75 = 1.75 (numeros coinciden (56% de canon cubierto))
  - FASE 3: 0.80*1.75 = 1.40 (coinciden algunos numeros clave (18%))
  - FASE 4: 0.70*1.75 = 1.22 (codigo extenso (94 lineas) ejecuta; printeos no coinciden con canonico)

## Bonus — Sesiones 9 y 10
- S9 entregada correctamente: **Sí** (integrador correcto (100% de numeros coinciden))
- S10 entregada correctamente: **Sí** (mpl_ok=True sb_ok=True)
- Bonus aplicado: **+0.5**

## Calificación final
- Parte 1: 10.00 / 10
- Parte 2: 8.76 / 10
- Promedio: 9.380 / 10
- Bonus: +0.5
- **Final: 9.88 / 10**

---

# Retroalimentación — Módulo 4 · Tema 2 (GLM con Python)

**Alumno:** José Julián Alcalá Alcántara
**Variable asignada:** `uso`

## Desglose por pregunta

| Pregunta | Pts | Comentario |
|---|---|---|
| P1 | 10/10 | Justificación completa: φ=1.1664>1, Cameron-Trivedi α=0.0744 con p≈0 rechaza equidispersión, y correctamente conecta φ<1.5 con la elección de QuasiPoisson (sin sobre-especificar con Binomial Negativa). |
| P2 | 9/10 | Interpretación correcta de Trabajo (RF=0.9887, −1.13%), IC que cruza 1 y p=0.7281>0.05, decisión razonada de agrupar con la referencia. Muy sólida; con solo dos niveles la comparación "más alto/más bajo" queda un poco implícita. |
| P3 | 10/10 | Explica con la fórmula correcta ($e^{\eta_g}=\Sigma n/\Sigma e$) el mecanismo de las ecuaciones de score con offset, y identifica bien el valor agregado del GLM (multiplicidad de variables, IC, significancia). |
| P4 | 10/10 | Explicación técnica completa: CV constante de la Gamma, Lognormal fuera de la familia exponencial natural, y el problema de sesgo al modelar E[log Y] en vez de E[Y]. |
| P5 | 10/10 | Elige Binomial Negativa con AIC/BIC correctos y explica bien por qué el pseudo R² bajo es normal en seguros. |
| P6 | 9/10 | Compara correctamente RF frecuencia (0.9887) vs severidad (0.9868) para Trabajo, nota que apuntan en la misma dirección y son de magnitud pequeña; la conexión con la necesidad de separar Frecuencia×Severidad queda algo genérica dado que en este caso ambos efectos son similares. |
| P7 | 10/10 | Distingue con precisión calibración (ratio 1.0249) de discriminación (Gini 0.2315 < 0.30), usando correctamente sus propios números. |
| P8 | 10/10 | Identifica bien Particular (prima más alta, $182.53, factor 1.0011 = +0.11%) y Trabajo (prima más baja, $178.57, factor 0.9794 = −2.06%); cálculos de recargo/descuento correctos. |
| P9 | 9/10 | Buena síntesis que integra frecuencia (con IC), severidad y prima pura en pocas líneas, con lenguaje técnico defendible. |

## Redacción: 9/10

## Nota final: 96/100 (calificación: 9.6/10)

## Comentarios generales
Excelente entrega: manejas con precisión el vocabulario actuarial (equidispersión, calibración vs. discriminación, sesgo de retransformación) y usas consistentemente tus propios números de `uso` en cada respuesta, sin errores conceptuales. La única variable que asignaron tiene efectos pequeños y no significativos por momentos (Trabajo), y supiste identificarlo correctamente en vez de forzar una narrativa de fuerte diferenciación. Para pulir aún más, en P6 y P9 podrías profundizar un poco más en la implicación práctica de que los efectos sean tan pequeños (¿vale la pena mantener `uso` como variable de tarificación?).
