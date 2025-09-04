# Caracterización y Asignación de Valor de un Material de Referencia (MR)

Este repositorio documenta el procedimiento seguido para la **caracterización de un Material de Referencia (MR)**, en el cual se asigna un valor mediante el cálculo de la media y sus límites de confianza, sin llegar a la etapa de certificación completa (MRC).

## Pasos realizados

1. **Caracterización de la muestra**  
   - Se analizaron las réplicas de los resultados obtenidos por distintos analistas utilizando un MRC como patrón trazable.  
   - Se consolidaron los datos en un único conjunto para su tratamiento estadístico.

2. **Detección y tratamiento de outliers**  
   - Se aplicaron pruebas estadísticas para identificar y eliminar valores atípicos.  

3. **Análisis de distribución**  
   - Cálculo de histograma para visualizar la forma de la distribución.  
   - QQ-plot para verificar la alineación de los datos con la normal teórica.  
   - KDE (Kernel Density Estimation) para observar la similitud entre la distribución observada y una distribución normal ideal.  

4. **Cálculo de estadísticos principales**  
   - Media, desviación estándar y coeficiente de variación.  
   - Contraste del CV con la **trompeta de Horwitz** para validar la coherencia entre precisión y nivel de concentración.

5. **Intervalos de confianza (95%)**  
   - Se calcularon los límites de confianza basados en la media y la variabilidad experimental.  
   - Se representaron mediante gráficos (Stewart plot) mostrando la dispersión de resultados dentro de ±2σ.

6. **Asignación de valor**  
   - El valor del MR se reporta como:  

$X_{MR} = \bar{x} \; \pm \; IC_{95\%}$

   donde \(\bar{x}\) es la media experimental y \(IC_{95\%}\) corresponde al intervalo de confianza al 95%.

---

## Resultado

- El **MR queda caracterizado** por su valor asignado con límites de confianza.  
- Este procedimiento constituye la base para un **Material de Referencia (MR)**, pero **no incluye aún** la incertidumbre completa (homogeneidad, estabilidad, calibración), que serían necesarios para un **MRC** según ISO 17034 / ISO Guide 35.
