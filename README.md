# 🛍️ Factores de Comportamiento Asociados al Ingreso Anual en NovaRetail+

> 👤 **Rol:** Analista de Datos de Crecimiento y Retención (Proyecto Individual)  
> 🏢 **Contexto:** Caso de Negocio / Proyecto de Portafolio (Bootcamp Analytics - Proyecto 7)  
> 🎯 **Alcance:** Análisis exploratorio y correlacional multivariable sobre 15,000 clientes de e-commerce en LATAM para identificar drivers de comportamiento vinculados al ingreso anual, evaluando métricas numéricas, binarias y categóricas sin asumir causalidad.  
> 🛠️ **Stack Técnico:** Python (`pandas`, `numpy`, `scipy.stats`, `seaborn`, `matplotlib`), Jupyter Notebook, Estadística Descriptiva e Inferencial.

---
## 📌 Descripción
Análisis exploratorio y correlacional sobre 15,000 clientes de una plataforma de e-commerce en Latinoamérica, con el objetivo de identificar qué variables de comportamiento están más fuertemente asociadas al ingreso anual generado por cliente.

## 🎯 Objetivo
Identificar qué factores de comportamiento están más asociados al ingreso anual de clientes.

Este es un análisis **correlacional (exploratorio)** — no busca ni permite establecer relaciones de causalidad, solo identificar asociaciones que orienten futuras estrategias e hipótesis de negocio.

---

## 📂 Conjunto de Datos

* **Dataset:** `/datasets/novaretail_comportamiento_clientes_2024.csv`
* **Volumen:** 15,000 registros de clientes (año 2024), 12 columnas, 100% libre de valores nulos.
* **Variable Objetivo (Foco):** `ingreso_anual` (Valor económico total generado por cliente en USD).

---

## ⚙️ Metodología y Pruebas Estadísticas Aplicadas

El flujo de análisis en **Jupyter Notebook** incluyó la evaluación de distribución y la elección de coeficientes específicos según la naturaleza de cada par de variables:

```text
                  ┌─── Numérica vs. Numérica (Lineal) ────────► Coeficiente de Pearson
                  ├─── Numérica vs. Numérica (Monotónica) ────► Coeficiente de Spearman
Tipo de Relación ─┼─── Binaria vs. Numérica ──────────────────► Correlación Punto-Biserial
                  └─── Categórica vs. Categórica ─────────────► V de Cramér (Chi-Cuadrado)


---
## 🛠️ Herramientas y Librerías
- **Python:** `pandas`, `numpy`
- **Estadística Inferencial (`scipy.stats`):** Coeficientes de Pearson, Spearman, punto-biserial y V de Cramér
- **Visualización:** `seaborn`, `matplotlib`
- **Entorno:** Jupyter Notebook

---

## 🔬 Metodología
1. Carga y exploración inicial de datos.
2. Preparación y documentación de supuestos.
3. Visualización de relaciones (heatmap y scatterplots).
4. Cuantificación de correlaciones ajustadas al tipo de variable (Pearson, Spearman, punto-biserial, V de Cramér).
5. Interpretación de negocio sin asumir causalidad.
6. Identificación de limitaciones y definición de próximos pasos.

---

## 📊 Hallazgos Principales

### Correlaciones Numéricas (Mapa de Calor):
- `compras_mes – ingreso_anual`: **0.97 (muy fuerte)**
- `visitas_mes – gasto_publicidad_dirigida`: **0.58 (moderada-fuerte)**
- `visitas_mes – ingreso_anual`: **0.34 (moderada)**
- `visitas_mes – compras_mes`: **0.35 (moderada)**
- `gasto_publicidad_dirigida – ingreso_anual`: **0.20 (débil)**
- `satisfaccion`, `edad`, `nivel_ingreso` vs. `ingreso_anual`: **≤ 0.06 (prácticamente nulas)**

---

## 💡 Análisis Detallado e Interpretación de Negocio

### 1. Transacciones Mensuales vs. Ingreso Anual (`r = 0.97`)
- **Evidencia visual:** Scatterplot con dirección positiva, dispersión muy baja (los puntos siguen una línea casi recta) y presencia de pocos outliers.
- **Evidencia numérica:** Coeficiente de correlación de 0.97.
- **Interpretación:** Ambas variables se mueven juntas de forma casi perfecta; cuando una aumenta, la otra lo hace casi en la misma proporción.
- **No podemos afirmar:** Que `compras_mes` cause directamente el `ingreso_anual` o viceversa, o que no exista una tercera variable influyendo en ambas, o que estén derivadas matemáticamente dentro del dataset.
- **Implicación de negocio:** El equipo debe segmentar a los clientes según su nivel de compras para identificar si la relación global es homogénea, reduciendo la fricción en clientes inactivos, aumentando la frecuencia en medianamente activos y protegiendo la lealtad de los activos.

### 2. Frecuencia de Visitas vs. Ingreso Anual (`r = 0.34`)
- **Evidencia visual:** Scatterplot con dirección positiva, dispersión media y presencia de outliers.
- **Evidencia numérica:** Coeficiente de correlación de 0.34.
- **Interpretación:** Hay una relación real pero moderada y con alta dispersión. No permite predecir con confianza una variable a partir de la otra.
- **No podemos afirmar:** Que conseguir más visitas garantice un mayor ingreso anual.
- **Implicación de negocio:** No es suficiente enfocarse únicamente en aumentar visitas (*vanity metrics*). Un cliente puede visitar poco pero tener un alto ticket promedio y ser más rentable que uno que visita con frecuencia pero gasta poco.

---

## ⚠️ Limitaciones
- **Correlación ≠ Causalidad:** Que dos variables estén correlacionadas no implica causa-efecto; pueden intervenir factores no observados como la antigüedad o el tipo de producto.
- **Capacidad Explicativa Limitada:** La correlación de 0.34 explica solo una fracción pequeña de la variación del ingreso anual entre clientes.
- **Análisis Agregado:** El estudio contempla a todos los clientes en conjunto ($N = 15,000$), por lo que las relaciones podrían ser más fuertes en ciertos subgrupos (ej. nuevos) y más débiles en otros.

---

## 🔜 Próximos Pasos
1. **Segmentación por Nivel de Actividad:** Dividir a los clientes en tres grupos según `compras_mes` (*inactivo*, *medianamente activo*, *activo*) mediante terciles, para verificar si la correlación de 0.97 se mantiene en todos los segmentos.
2. **Revisión de Visitas por Segmento:** Analizar si la correlación entre `visitas_mes` e `ingreso_anual` (0.34) cambia de fuerza al aislar cada nivel de actividad.
3. **Efecto Controlado de `miembro_premium`:** Evaluar el impacto de la membresía premium dentro de cada segmento de actividad para evitar variables de confusión.
4. **Exploración de Poder Adquisitivo:** Analizar la relación con `nivel_ingreso` (poder adquisitivo del cliente) bajo la hipótesis de que clientes con mayor capacidad económica generan mayor ingreso independientemente de su frecuencia de visita.

## 📊 Visualizaciones Generadas
- **Correlación Heatmap:** Matriz global de correlación para variables numéricas y binarias.
- **Scatterplot:** `compras_mes` vs. `ingreso_anual`
- **Scatterplot:** `visitas_mes` vs. `ingreso_anual`
- **Scatterplot:** `visitas_mes` vs. `gasto_publicidad_dirigida`
- **Scatterplot:** `visitas_mes` vs. `compras_mes`

---

## 📂 Estructura del repositorio
- `readme.md`
- `data/` → datasets original.
- `notebook/` → notebook de análisis.
- `visualizaciones/` → gráficos generados.

---

Este proyecto forma parte de mi portfolio de análisis de datos, con énfasis en el rigor metodológico al distinguir correlación de causalidad y en traducir hallazgos estadísticos en implicaciones de negocio accionables.
