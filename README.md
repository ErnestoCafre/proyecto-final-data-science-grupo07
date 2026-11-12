# ⚡ Proyecto Final — Data Science (Grupo 07)
### **Programa EnergIA Digital | Fundación YPF**

[![Python Version](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-orange.svg?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Status](https://img.shields.io/badge/Estado-En_Desarrollo-yellow.svg)]()

---

## 👥 Integrantes del Grupo 07
* **Integrante 1:** Emilia Munaretto - [@emiliamunaretto-max](https://github.com/emiliamunaretto-max)
* **Integrante 2:** Santiago Tuñón - [@santiagotunon-prog](https://github.com/santiagotunon-prog)
* **Integrante 3:** Ernesto Cafre - [@ErnestoCafre](https://github.com/ErnestoCafre)

---

## 📝 Resumen Ejecutivo del Proyecto

### 1. Resumen del Proyecto
> El proyecto aborda el análisis operativo y de eficiencia en intervenciones de estimulación hidráulica (*fracking*) en pozos de hidrocarburos de Argentina

### 2. Origen del Dataset
> Los datos provienen del portal oficial de datos abiertos de la República Argentina ([datos.gob.ar](https://datos.gob.ar/dataset/datos-de-fractura-de-pozos-adjunto-iv/resource/3d19ba75-3a93-597a-b4f2-49be87b75358)), provisto por la Secretaría de Energía de la Nación bajo el registro *"Datos de fractura de pozos de hidrocarburos"*. El conjunto abarca un histórico representativo de 4.890 declaraciones juradas presentadas por empresas operadoras (YPF, Pampa Energía, etc.). **Qué es un registro:** cada fila es la declaración jurada de un trabajo de fractura sobre un pozo y resume todas sus etapas (la columna `cantidad_fracturas` cuenta esas etapas: mediana de 17 y máximo de 105 por registro). No es un pozo único ni una etapa individual: tras la limpieza, los 4.888 registros corresponden a 4.644 pozos distintos (`idpozo`). Hay 183 pozos con más de un registro (427 filas, es decir 244 más que pozos), casi todos convencionales o *tight*: en 95 son re-fracturas separadas por más de un año y en 55 es un mismo trabajo declarado en varias filas dentro de un mes. Además, 8 declaraciones figuran cargadas dos veces con los mismos valores operativos; las conservamos sin modificar. En los pozos horizontales registro y pozo prácticamente coinciden (2.671 registros en 2.651 pozos).

### 3. Objetivo Propuesto
> Anticipar la demanda de insumos de cada fractura para planificar la logística de arena, que se trae desde Entre Ríos o se importa y recorre más de 1.000 km hasta el pozo. Para eso planteamos dos preguntas: **(a)** ¿se puede predecir la arena total que requerirá una fractura (`arena_total_tn`) a partir de variables conocidas al diseñarla (etapas, rama horizontal, agua, presión, potencia, formación)? y **(b)** si agrupamos los registros sólo por sus medidas operativas, sin mirar la geología, ¿aparecen perfiles naturales de fractura (chicos, medianos y grandes) útiles para dimensionar arena, agua y equipos?

### 4. Hallazgos del Análisis Exploratorio (AED)
> La actividad está muy concentrada: el 83,6% de los registros es de la cuenca Neuquina, el 61,4% de la formación Vaca Muerta y el 45,5% fue informado por YPF. La arena tiene una distribución bimodal (mediana de 20 tn en convencionales contra 6.601 tn en no convencionales) y está fuertemente correlacionada con la cantidad de etapas (r = 0,98), la longitud de la rama horizontal (0,96) y el agua inyectada (0,92). En los pozos horizontales se ve una clara evolución tecnológica: la rama mediana pasó de unos 900 m en 2012 a unos 3.000 m en 2025, y la arena mediana de 1.840 tn a 11.700 tn. En la limpieza tratamos como faltantes las presiones imposibles (más de 20.000 psi o menos de 1.000 psi) y las potencias fuera de rango, y las imputamos con la mediana de su tipo y subtipo de reservorio. También recalculamos 67 ramas horizontales en 0 o menores a 50 m multiplicando la cantidad de etapas por el espaciado mediano de su cuenca. En todos los casos dejamos columnas que marcan qué valores se imputaron. También eliminamos 2 registros de GeoPark con arena fuera de escala y detectamos que los 303 registros restantes con agua y CO2 en 0 (302 de Tecpetrol) no son fracturas secas sino agua no informada: 233 tienen arena bombeada y 70 no declaran ningún insumo. Los dejamos como faltantes, marcados con la columna `agua_no_informada`. Por último, corregimos fechas invertidas. El dataset limpio (4.888 registros) quedó en `data/processed/pozos_fractura_limpio.csv`.

### 5. Detalle de los Modelos Ajustados
> **Supervisado (regresión de `arena_total_tn`):** con `Pipeline` + `ColumnTransformer`, una separación 80/20 y validación cruzada de 5 pliegues comparamos un `DummyRegressor`, una Regresión Lineal y un Random Forest. Después optimizamos el Random Forest con Optuna (40 pruebas, minimizando el RMSE de validación cruzada). En test, el modelo final obtuvo **MAE = 299 tn, RMSE = 561 tn y R² = 0,988**, contra MAE = 498 tn y R² = 0,974 de la regresión lineal: un 40% menos de error típico, equivalente a cerca del 6% de la arena promedio. Las variables más influyentes fueron la cantidad de etapas, el agua inyectada y la longitud de la rama. **No supervisado (clustering):** aplicamos K-Means sobre 6 variables operativas transformadas con `log1p` + `StandardScaler` (4.585 registros con agua informada) y elegimos K = 3 por el método del codo y la silueta (0,621). Los tres perfiles fueron: *chicos* (20%, mayormente verticales, mediana de 33 tn de arena, concentrados en las cuencas Austral y Golfo San Jorge), *medianos* (24%, unas 800 tn, pozos tight y primeros pozos verticales de Vaca Muerta) y *grandes* (56%, rama de unos 2.500 m, 41 etapas y unas 9.300 tn, 99,7% shale neuquino). Contrastados con el subtipo de reservorio, que no participó del agrupamiento, obtuvieron una pureza de 0,819 y un ARI de 0,632: el perfil operativo reproduce en gran medida la geología.

---

## 🗺️ Mapeo del Pipeline y Entregas Académicas

Este repositorio implementa una arquitectura híbrida que vincula las pre-entregas académicas con un pipeline profesional de Ciencia de Datos:

| Hito Académico | Etapa del Pipeline | Directorio | Estado |
| :--- | :--- | :--- | :---: |
| **1ª Pre-entrega** (Clase 5/7) | Desafíos de Notebooks 5 y 7 | [`notebooks/00_pre_entrega_1_desafios/`](notebooks/00_pre_entrega_1_desafios/) | 🟢 Completada |
| **2ª Pre-entrega** (Clase 10) | Análisis Exploratorio de Datos (AED) | [`notebooks/01_pre_entrega_2_aed/`](notebooks/01_pre_entrega_2_aed/) | 🟢 Completada |
| **3ª Pre-entrega** (Clase 18/19) | Modelo de Aprendizaje Supervisado | [`notebooks/02_pre_entrega_3_supervisado/`](notebooks/02_pre_entrega_3_supervisado/) | 🟢 Completada |
| **4ª Pre-entrega** (Clase 25) | Modelo No Supervisado (Clustering) | [`notebooks/03_pre_entrega_4_no_supervisado/`](notebooks/03_pre_entrega_4_no_supervisado/) | 🟢 Completada |
| **Entrega Final** | Exposición Oral de 15 minutos | [`presentacion/`](presentacion/) | 🟢 Completada |

---

## 📂 Estructura del Repositorio

```text
proyecto-final-data-science-grupo07/
│
├── .gitignore                             # Filtros para cachés, temporales y modelos pesados
├── README.md                              # Ficha técnica y resumen ejecutivo (Rúbrica oficial)
│
├── data/                                  # Gobernanza de datos
│   ├── raw/                               # Dataset original inmutable
│   └── processed/                         # Datos transformados y preprocesados
│
├── notebooks/                             # Flujo secuencial y pre-entregas
│   ├── 00_pre_entrega_1_desafios/         # Desafíos resueltos (notebooks 5 y 7)
│   ├── 01_pre_entrega_2_aed/              # AED y visualizaciones con Pandas
│   ├── 02_pre_entrega_3_supervisado/      # Modelo Supervisado (Clasif./Regresión)
│   └── 03_pre_entrega_4_no_supervisado/   # Modelo No Supervisado (Clustering)
│
├── presentacion/                          # Material de apoyo para la defensa oral (15 min)
│   └── README.md                          # Enlace a Canva/Slides y pautas de Storytelling
│
└── docs/                                  # Documentación y lineamientos del curso
    ├── EnergIA Digital Data Science.pdf   # Guía original en PDF
    └── GUIA_PROYECTO.md                   # Guía interactiva en Markdown con fechas y checklist
```

---

## ✅ Checklist de Entrega Final

- [x] Grupo informado al equipo docente.
- [x] Tema y dataset publicados en el foro del aula virtual.
- [x] Repositorio estructurado y ambiente de trabajo configurado.
- [x] Resumen ejecutivo del `README.md` completado (los 5 puntos requeridos).
- [x] Dataset incluido en `data/raw/`.
- [x] Notebook de AED (Pre-entrega 2) reproducible.
- [x] Notebook de Modelo Supervisado (Pre-entrega 3) con métricas y tuning.
- [x] Notebook de Modelo No Supervisado (Pre-entrega 4) con análisis de clusters.
- [x] Presentación oral armada (diapositivas en `presentacion/`).
- [ ] Enlace al repositorio cargado en el aula virtual para la certificación.

---

> [!TIP]  
> Para consultar el detalle completo de los criterios pedagógicos, consulta la [Guía del Proyecto](docs/GUIA_PROYECTO.md).
