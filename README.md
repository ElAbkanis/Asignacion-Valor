# 🧪 Caracterización y Asignación de Valor de un Material de Referencia (MR)

Este repositorio documenta el procedimiento seguido para la **caracterización de un Material de Referencia (MR)**.  
El objetivo es asignar un valor mediante la media y sus límites de confianza, sin llegar aún a la certificación completa (MRC).

---

## 🔬 Pasos realizados

1. 📊 **Caracterización de la muestra**  
   - Se analizaron réplicas de resultados obtenidos por distintos analistas.  
   - Se utilizó un **MRC como patrón trazable** para garantizar la trazabilidad metrológica.  

2. 🧹 **Detección y eliminación de outliers**  
   - Aplicación de pruebas estadísticas para identificar valores atípicos.  

3. 📈 **Análisis de distribución**  
   - Histograma → visualización de la forma de la distribución.  
   - QQ-plot → verificación contra la normal teórica.  
   - KDE → comparación de la densidad observada con la distribución normal.  

4. 📐 **Cálculo de estadísticos principales**  
   - Media, desviación estándar y coeficiente de variación (CV).  
   - Contraste del **CV** con la **trompeta de Horwitz** para validar coherencia entre precisión y concentración.  

5. ✅ **Intervalos de confianza (95%)**  
   - Cálculo de los límites de confianza basados en la media y variabilidad experimental.  
   - Visualización mediante gráfico de Stewart (±2σ).  

6. 📝 **Asignación de valor del MR**  
   El valor se reporta como:  

🧪 Valor asignado del MR: X = X̄ ± IC₉₅%


   donde X̄ es la media experimental y IC₉₅% el intervalo de confianza al 95%.

---

## 📌 Resultado

- Se obtiene un **Material de Referencia (MR)** caracterizado por su valor asignado con límites de confianza.  
- ❗ No incluye aún la incertidumbre completa (**homogeneidad, estabilidad, calibración**), que serían necesarias para convertirlo en un **MRC** según **ISO 17034 / ISO Guide 35**.

---

## 💻 Código de ejemplo en Python

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Cargar datos
data = pd.read_csv("Data.csv")
col = "Cu %"

# Bootstrap
n_iterations = 1000
bootstrap_samples = [
    np.mean(np.random.choice(data[col].dropna(), size=len(data), replace=True))
    for _ in range(n_iterations)
]

# Estadísticos
mean = data[col].mean()
conf_int = np.percentile(bootstrap_samples, [2.5, 97.5])

print(f"Valor asignado (MR): {mean:.4f} ± {((conf_int[1]-conf_int[0])/2):.4f}")

# Visualización
sns.histplot(bootstrap_samples, kde=True)
plt.axvline(conf_int[0], color="red", linestyle="--")
plt.axvline(conf_int[1], color="red", linestyle="--")
plt.title(f"Distribución bootstrap - {col}")
plt.show()
