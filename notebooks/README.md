# 📓 Directorio de Cuadernos (Notebooks)

En este directorio se desarrollan los cuadernos interactivos de Jupyter para el proyecto final de **EnergIA Digital — Data Science (Grupo 07)**.

La numeración secuencial (`00`, `01`, `02`, `03`) define el orden del flujo de trabajo, manteniendo a la vez correspondencia directa con cada una de las **pre-entregas académicas**.

---

## 🗺️ Mapa de Cuadernos y Entregas

| Carpeta | Hito Académico | Clases | Objetivo Principal |
| :--- | :---: | :---: | :--- |
| [`00_pre_entrega_1_desafios/`](file:///c:/Users/Ernes/Git-Cursos/FundacionYPF/proyecto-final-datascience-grupo07/notebooks/00_pre_entrega_1_desafios) | **1ª Pre-entrega** | Clase 5 / 7 | Desafíos resueltos de las notebooks 5 y 7. |
| [`01_pre_entrega_2_aed/`](file:///c:/Users/Ernes/Git-Cursos/FundacionYPF/proyecto-final-datascience-grupo07/notebooks/01_pre_entrega_2_aed) | **2ª Pre-entrega** | Clase 10 | Análisis Exploratorio de Datos (AED): limpieza, transformaciones con Pandas y visualizaciones. |
| [`02_pre_entrega_3_supervisado/`](file:///c:/Users/Ernes/Git-Cursos/FundacionYPF/proyecto-final-datascience-grupo07/notebooks/02_pre_entrega_3_supervisado) | **3ª Pre-entrega** | Clase 18 / 19 | Modelo de Aprendizaje Supervisado (clasificación/regresión), métricas de evaluación y optimización de hiperparámetros. |
| [`03_pre_entrega_4_no_supervisado/`](file:///c:/Users/Ernes/Git-Cursos/FundacionYPF/proyecto-final-datascience-grupo07/notebooks/03_pre_entrega_4_no_supervisado) | **4ª Pre-entrega** | Clase 25 | Modelo de Aprendizaje No Supervisado (*clustering*), justificación del algoritmo y análisis cualitativo de clusters. |

---

## 📌 Pautas de Buenas Prácticas
1. **Reproducibilidad:** Cada notebook debe poder ejecutarse de inicio a fin (*Restart & Run All*) sin errores.
2. **Caminos relativos:** Para cargar datos, utiliza rutas relativas estandarizadas, por ejemplo:
   ```python
   import pandas as pd
   df_raw = pd.read_csv("../../data/raw/tu_dataset.csv")
   ```
3. **Comentarios y Storytelling:** Complementar las celdas de código con celdas de texto en Markdown que expliquen el *por qué* de las decisiones tomadas y las conclusiones intermedias.
