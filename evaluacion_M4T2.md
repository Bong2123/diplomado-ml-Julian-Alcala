# Evaluación — Módulo 4 · Tema 2: GLM con Python

**Alumno:** José Julián
**Variable asignada:** `uso`  (uso)
**Fecha de entrega:** 13-09-2026

> **Instrucciones.** Este archivo evalúa las tres sesiones del tema. Las tablas ya vienen
> calculadas; tu trabajo es **responder las preguntas de interpretación** en el espacio
> "**Tu respuesta:**". Se evalúa la interpretación, no el código. Máx. 4–6 líneas por respuesta.
> Todas tus preguntas usan **tu variable asignada** (`uso`). Guarda y sube este archivo a tu repositorio.

---

## Parte 1 · Sesión 1 — Modelo de Frecuencia

**Diagnóstico del supuesto de Poisson (modelo completo):**

| métrica | valor |
| --- | --- |
| φ de Pearson | 1.1664 |
| Cameron-Trivedi α | 0.0744 |
| z | 15.80 |
| p-value | 3.7e-56 |

**Rating factors de frecuencia para `uso`** (base × RF reproduce la tasa empírica; diferencia máx = 1.7e-05):

| nivel | RF_frec | IC_inf | IC_sup | p | tasa_emp |
| --- | --- | --- | --- | --- | --- |
| Particular (ref) | 1 | 1 | 1 | 0 | 0.1393 |
| Trabajo | 0.9887 | 0.9272 | 1.0542 | 0.7281 | 0.1377 |

**P1.** ¿Se cumple la equidispersión? Justifica con φ **y** con Cameron-Trivedi, y di qué familia usarías.
**Tu respuesta:** No se cumple estrictamente la equidispersión. El parámetro de Pearson es φ =1.1664>1, lo que indica sobredispersión leve. La prueba de Cameron–Trivedi lo confirma: α =0.0744>0 y p-value=3.7e-56, por lo que se rechaza la hipótesis de equidispersión. Dado que φ <1.5, utilizaría QuasiPoisson, ya que permite corregir la dispersión sin modificar la estructura media del modelo Poisson.

**P2.** Interpreta los rating factors de tu variable: nivel más alto y más bajo, traducidos a % de
recargo/descuento. ¿Algún IC cruza 1 o tiene p > 0.05? ¿Qué harías con ese nivel?
**Tu respuesta:** Trabajo presenta un RF de 0.9887, equivalente a una frecuencia esperada 1.13% menor respecto a Particular. Sin embargo, su IC 95% [0.9272, 1.0542] cruza 1 y su p-value = 0.7281 > 0.05, por lo que la diferencia no es estadísticamente significativa. Por ello, agruparía Trabajo con la categoría de referencia, ya que no existe evidencia suficiente para justificar una diferenciación tarifaria por uso

**P3.** ¿Por qué el GLM one-way reproduce exactamente la tasa empírica, y qué aporta el GLM que una
tabla empírica no puede dar?
**Tu respuesta:** El GLM one-way reproduce la tasa empírica porque, en un Poisson con liga log y offset de exposición, las ecuaciones de score obligan a que la suma de siniestros predichos iguale a la observada en cada nivel; por ello, $e^{\eta_g} = \frac{\sum_i n_i}{\sum_i e_i}$, que es exactamente la tasa empírica ponderada. La ventaja del GLM es que permite combinar varias variables de forma multiplicativa y, además, obtener intervalos de confianza y pruebas de significancia para los rating factors, algo que una tabla empírica simple no ofrece.

---

## Parte 2 · Sesión 2 — Severidad y Selección de Modelos

**Comparación de modelos de frecuencia:**

| modelo | AIC | BIC | pseudoR2_McF |
| --- | --- | --- | --- |
| Poisson | 125,081.7 | 125,261.7 | 0.0198 |
| Binomial Negativa | 124,925.7 | 125,105.8 | 0.021 |

**Rating factors de severidad (Gamma) para `uso`:**

| nivel | RF_sev | severidad_emp |
| --- | --- | --- |
| Particular (ref) | 1 | 1,310 |
| Trabajo | 0.9868 | 1,293 |

**P4.** ¿Por qué se usa **Gamma** para severidad y no una regresión lineal sobre log(Y)? (menciona la
propiedad del CV y por qué Lognormal no es GLM).
**Tu respuesta:** Se utiliza Gamma porque es adecuada para severidades positivas y supone un CV constante, ya que $ Var(Y)=\phi\mu^2 $ y por tanto $ CV=\sqrt{\phi}$, consistente con una variabilidad relativa similar entre niveles. La Lognormal no pertenece a la familia exponencial natural utilizada por los GLM. Además, una regresión sobre $ \log(Y)$ modela $E[\log(Y)]$, no $E[Y]$, por lo que al regresar a la escala original requiere una corrección por sesgo. En cambio, Gamma con liga log modela directamente la severidad media E[Y]

**P5.** Según la tabla de comparación, ¿qué modelo elegirías? Justifica con AIC/BIC. ¿Por qué el pseudo R²
es tan bajo y eso NO significa que el modelo sea malo?
**Tu respuesta:** Elegiría la Binomial Negativa, ya que presenta menor AIC (124,925.7 vs 125,081.7) y menor BIC (125,105.8 vs 125,261.7), por lo que ofrece un mejor ajuste penalizando la complejidad. El pseudo $R^2$ es bajo (~0.02), pero esto es normal en modelos de frecuencia de seguros debido a la alta aleatoriedad irreducible de los siniestros.

**P6.** Compara tus rating factors de frecuencia (Parte 1) con los de severidad para `uso`. ¿Apuntan en
la misma dirección? ¿Qué implica eso para separar Frecuencia × Severidad?
**Tu respuesta:** Los rating factors de uso apuntan en la misma dirección: para Trabajo, el RF de frecuencia es 0.9887, equivalente a una reducción aproximada de 1.13%, y el RF de severidad es 0.9868, una reducción aproximada de 1.32% respecto a Particular. Ambos efectos son muy pequeños, por lo que uso muestra poca capacidad de diferenciación del riesgo. Aun así, separar Frecuencia × Severidad es importante porque una variable puede afectar de forma distinta el número y el costo de los siniestros, aunque en este caso ambos efectos sean similares.

---

## Parte 3 · Sesión 3 — Validación y Tarifa

**Validación out-of-sample del modelo de frecuencia:**

| metrica | valor | ideal |
| --- | --- | --- |
| Gini (test) | 0.2315 | > 0.30 aceptable |
| Ratio pred/obs (test) | 1.0249 | ≈ 1.00 |

**Prima pura por nivel de `uso`** (Frecuencia × Severidad, con su factor de tarifa):

| nivel | prima_pura_modelo | factor_tarifa |
| --- | --- | --- |
| Particular (ref) | 182.53 | 1.0011 |
| Trabajo | 178.57 | 0.9794 |

**P7.** Interpreta las métricas de validación: ¿el modelo está bien calibrado (ratio pred/obs)? ¿discrimina
bien el riesgo (Gini)? ¿Qué mide cada una?
**Tu respuesta:** El modelo está bien calibrado globalmente, ya que el ratio pred/obs es 1.0249, muy cercano a 1, lo que indica que el total predicho difiere poco del observado. Sin embargo, el Gini es 0.2315, por debajo del umbral de 0.30, por lo que la capacidad de discriminación es modesta. La calibración mide qué tan bien se reproduce el nivel total de riesgo, mientras que el Gini mide qué tan bien el modelo ordena y separa riesgos bajos y altos.

**P8.** Lee la tabla de tarifa: ¿qué nivel de tu variable paga la prima pura más alta y cuál la más baja?
Traduce el factor de tarifa a un recargo/descuento sobre la prima promedio.
**Tu respuesta:** El nivel Particular presenta la prima pura más alta, con $182.53, mientras que Trabajo tiene la más baja, con $178.57. El factor de tarifa de Particular es 1.0011, equivalente a un recargo aproximado de 0.11% sobre la prima promedio; para Trabajo, el factor es 0.9794, equivalente a un descuento de aproximadamente 2.06%. En ambos casos, el efecto de uso sobre la tarifa es reducido.

**P9. (Conclusión de nota técnica).** En 3–4 líneas, redacta cómo `uso` afecta la tarifa, integrando
frecuencia, severidad y prima pura, en estilo defendible ante la CNSF.
**Tu respuesta:** La variable uso presenta un efecto reducido sobre la tarifa. Para Trabajo, la frecuencia esperada es 1.13% menor que en Particular (RF = 0.9887; IC 95% [0.9272, 1.0542]), sin evidencia de una diferencia estadísticamente significativa, mientras que la severidad estimada es 1.32% menor. Al combinar ambos componentes, la prima pura disminuye de $182.53 en Particular a $178.57 en Trabajo, por lo que uso muestra una capacidad limitada de diferenciación tarifaria.

---
*Evaluación generada automáticamente · Diplomado ML en Seguros · FC UNAM · Módulo 4 · Tema 2*
