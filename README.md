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
> *(Requerimiento de rúbrica: máximo un párrafo por ítem)*

### 1. Resumen del Proyecto
> *[Breve descripción general del proyecto: contexto de la problemática que se busca abordar, relevancia del sector energético o del dominio elegido, y alcance del análisis desarrollado de punta a punta].*

### 2. Origen del Dataset
> *[Descripción del origen de los datos: fuente de procedencia (BA Data, Kaggle, Google Dataset Search, etc.), método de obtención, enlace directo a la fuente y justificación de por qué resulta representativo para responder las preguntas del proyecto].*

### 3. Objetivo Propuesto
> *[Definición clara y concisa de la meta principal del estudio: qué variable clave se desea analizar/predecir, qué hipótesis se plantean y qué valor práctico o de negocio aporta la solución].*

### 4. Hallazgos del Análisis Exploratorio (AED)
> *[Principales descubrimientos obtenidos en la etapa exploratoria: correlaciones destacadas, patrones o tendencias temporales, anomalías identificadas y conclusiones clave que guiaron la etapa de modelado].*

### 5. Detalle de los Modelos Ajustados
> *[Síntesis técnica de los modelos entrenados: algoritmos supervisados aplicados (regresión/clasificación), métricas de rendimiento alcanzadas tras la optimización de hiperparámetros y conclusiones cualitativas derivadas del clustering no supervisado].*

---

## 🗺️ Mapeo del Pipeline y Entregas Académicas

Este repositorio implementa una arquitectura híbrida que vincula las pre-entregas académicas con un pipeline profesional de Ciencia de Datos:

| Hito Académico | Etapa del Pipeline | Directorio | Estado |
| :--- | :--- | :--- | :---: |
| **1ª Pre-entrega** (Clase 5/7) | Desafíos de Notebooks 5 y 7 | [`notebooks/00_pre_entrega_1_desafios/`](notebooks/00_pre_entrega_1_desafios/) | 🟡 Pendiente |
| **2ª Pre-entrega** (Clase 10) | Análisis Exploratorio de Datos (AED) | [`notebooks/01_pre_entrega_2_aed/`](notebooks/01_pre_entrega_2_aed/) | 🟡 Pendiente |
| **3ª Pre-entrega** (Clase 18/19) | Modelo de Aprendizaje Supervisado | [`notebooks/02_pre_entrega_3_supervisado/`](notebooks/02_pre_entrega_3_supervisado/) | 🟡 Pendiente |
| **4ª Pre-entrega** (Clase 25) | Modelo No Supervisado (Clustering) | [`notebooks/03_pre_entrega_4_no_supervisado/`](notebooks/03_pre_entrega_4_no_supervisado/) | 🟡 Pendiente |
| **Entrega Final** | Exposición Oral de 15 minutos | [`presentacion/`](presentacion/) | 🟡 Pendiente |

---

## 📂 Estructura del Repositorio

```text
proyecto-final-datascience-grupo07/
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
├── docs/                                  # Documentación y lineamientos del curso
│   ├── EnergIA Digital Data Science.pdf   # Guía original en PDF
│   └── GUIA_PROYECTO.md                   # Guía interactiva en Markdown con fechas y checklist
│
└── tools/                                 # Herramientas de soporte desacopladas
    └── extractor/                         # Utilidad para extracción de texto en UTF-8
```

---

## ✅ Checklist de Entrega Final

- [ ] Grupo informado a la tutora Belén.
- [ ] Tema y dataset publicados en el foro del aula virtual.
- [ ] Repositorio estructurado y ambiente de trabajo configurado.
- [ ] Resumen ejecutivo del `README.md` completado (los 5 puntos requeridos).
- [ ] Dataset incluido en `data/raw/`.
- [ ] Notebook de AED (Pre-entrega 2) reproducible.
- [ ] Notebook de Modelo Supervisado (Pre-entrega 3) con métricas y tuning.
- [ ] Notebook de Modelo No Supervisado (Pre-entrega 4) con análisis de clusters.
- [ ] Presentación oral armada (diapositivas en `presentacion/`).
- [ ] Enlace al repositorio cargado en el aula virtual para la certificación.

---

> [!TIP]  
> Para consultar el detalle completo de los criterios pedagógicos, consulta la [Guía del Proyecto](docs/GUIA_PROYECTO.md).
