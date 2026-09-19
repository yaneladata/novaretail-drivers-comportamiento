# 🛍️ Factores de Comportamiento Asociados al Ingreso Anual en NovaRetail+

## 📌 Descripción
Análisis exploratorio y correlacional sobre 15,000 clientes de una plataforma de e-commerce en Latinoamérica, con el objetivo de identificar qué variables de comportamiento están más fuertemente asociadas al ingreso anual generado por cliente.

## 🎯 Objetivo
Identificar qué factores de comportamiento están más asociados al ingreso anual de clientes.

Este es un análisis **correlacional (exploratorio)** — no busca ni permite establecer relaciones de causalidad, solo identificar asociaciones que orienten futuras estrategias e hipótesis de negocio.

---

## 📂 Conjunto de datos
**Archivo:** `novaretail_comportamiento_clientes_2024.csv` — 15,000 registros, 12 columnas, sin valores nulos.

**Columnas:**
- `id_cliente`: Identificador único del cliente  
- `edad`: Edad del cliente  
- `nivel_ingreso`: Ingreso anual estimado (poder adquisitivo)  
- `visitas_mes`: Número de visitas mensuales a la app/sitio web  
- `compras_mes`: Número de compras realizadas en el mes  
- `gasto_publicidad_dirigida`: Gasto en anuncios asignado al usuario  
- `satisfaccion`: Calificación de satisfacción (escala 1-5)  
- `miembro_premium`: Suscripción premium (1 = sí, 0 = no)  
- `abandono`: Abandono de la plataforma (1 = sí, 0 = no)  
- `tipo_dispositivo`: Dispositivo utilizado (móvil, escritorio, tablet)  
- `region`: Región geográfica (norte, sur, este, oeste)  
- `ingreso_anual`: Métrica principal — ingreso anual generado por el cliente  

---

## 🛠️ Herramientas y librerías
- Python (pandas, numpy)  
- `scipy.stats` — Pearson, Spearman, punto-biserial, chi-cuadrado  
- Seaborn / Matplotlib — heatmap de correlación, scatterplots  

---

## 🔬 Metodología
1. Carga y exploración inicial de datos  
2. Preparación y documentación de supuestos  
3. Visualización de relaciones (heatmap y scatterplots)  
4. Cuantificación de correlaciones (Pearson, Spearman, punto-biserial, V de Cramér)  
5. Interpretación de negocio  
6. Limitaciones y próximos pasos  

---
## 📊 Visualizaciones
- **Correlación Heatmap**: Matriz de correlación
- **Scatterplot**: Visita_Mes vs Ingreso_Anual
- **Scatterplot**: Visita_Mes vs Gasto_publicidad
- **Scatterplot**: Compra_mes vs Ingreso_Anual
- **Scatterplot**: Visita_mes vs Compra_Mes

---

## 📊 Hallazgos principales
**Correlaciones numéricas (mapa de calor):**
- `compras_mes – ingreso_anual`: **0.97 (muy fuerte)**  
- `visitas_mes – gasto_publicidad_dirigida`: 0.58 (moderada-fuerte)  
- `visitas_mes – ingreso_anual`: 0.34 (moderada)  
- `visitas_mes – compras_mes`: 0.35 (moderada)  
- `gasto_publicidad_dirigida – ingreso_anual`: 0.20 (débil)  
- `satisfaccion`, `edad`, `nivel_ingreso` vs. `ingreso_anual`: ≤ 0.06 (prácticamente nulas)  

---

## 💡 Implicaciones de negocio
- Segmentar clientes según **compras_mes** para diseñar incentivos diferenciados.  
- No enfocarse únicamente en aumentar visitas: un cliente con pocas visitas puede ser más rentable si su ticket promedio es alto.  

---

## ⚠️ Limitaciones
- Correlación ≠ causalidad.  
- Las visitas explican solo una parte de la variación del ingreso anual.  
- El análisis es agregado; las relaciones podrían variar por segmento (ej. clientes nuevos vs. recurrentes).  

---

## 🔜 Próximos pasos
- Segmentar clientes por nivel de actividad de compra.  
- Analizar el efecto de `miembro_premium` dentro de cada segmento.  
- Explorar `nivel_ingreso` como variable adicional para explicar `ingreso_anual`.
  
---
## 📂 Estructura del repositorio
- `readme.md`
- `data/` → datasets original.
- `notebook/` → notebook de análisis.
- `visualizaciones/` → gráficos generados.

---

Este proyecto forma parte de mi portfolio de análisis de datos, con énfasis en el rigor metodológico al distinguir correlación de causalidad y en traducir hallazgos estadísticos en implicaciones de negocio accionables.
