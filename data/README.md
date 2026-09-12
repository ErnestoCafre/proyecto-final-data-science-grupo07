# Gobernanza de Datos (Data Governance)

Este directorio gestiona los datos del proyecto siguiendo las mejores prácticas de la industria en Data Science:

```text
data/
├── raw/         # Datos originales e inmutables
└── processed/   # Datos limpios, transformados y listos para modelado
```

---

## 📂 Subdirectorios

### 1. `data/raw/`
* **Definición:** Contiene el dataset original sin ninguna modificación (tal como fue descargado de la fuente: BA Data, Kaggle, Google Dataset Search, etc.).
* **Regla de oro:** **Nunca modificar ni sobreescribir los archivos en esta carpeta**. Es la única fuente de verdad para garantizar la reproducibilidad.

### 2. `data/processed/`
* **Definición:** Datos resultantes luego de las etapas de:
  - Limpieza (imputación/eliminación de nulos, corrección de tipos).
  - Normalización o estandarización.
  - Feature Engineering (creación de nuevas variables, codificación one-hot, etc.).
* **Uso:** Es el dataset que consumen directamente los notebooks de modelos supervisados (`02_pre_entrega_3_supervisado`) y no supervisados (`03_pre_entrega_4_no_supervisado`).

---

> [!NOTE]  
> Si el dataset es liviano (<100 MB), se versiona en este repositorio conforme a la pauta de entrega final. Si en algún momento se trabaja con un dataset pesado (>100 MB), se recomienda colocarlo aquí localmente y dejarlo excluido en el `.gitignore` indicando la URL de descarga.
