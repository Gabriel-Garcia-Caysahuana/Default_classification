# Proyecto: Predicción de Incumplimiento de Deuda de Tarjeta de Crédito

Este proyecto tiene como objetivo predecir qué clientes incumplirán con su deuda de tarjeta de crédito utilizando un conjunto de datos simulados que contiene información de 10,000 clientes. Se implementan diferentes modelos de aprendizaje supervisado para realizar las predicciones.

## Descripción del Dataset

El conjunto de datos **Default.csv** contiene las siguientes variables:

- **default:** Indica si el cliente incumplió con el pago de su deuda (`No`, `Yes`).
- **student:** Indica si el cliente es estudiante (`No`, `Yes`).
- **balance:** Saldo promedio en la tarjeta de crédito después del pago mensual.
- **income:** Ingresos del cliente.

### Referencia
James, G., Witten, D., Hastie, T., and Tibshirani, R. (2013). *An Introduction to Statistical Learning with Applications in R*, Springer-Verlag, New York. Disponible en: [https://www.statlearning.com](https://www.statlearning.com).

---

## Estructura del Proyecto

### Preprocesamiento de Datos

1. **Cargar archivo:**
   - Verificación de datos faltantes y tipos de variables.

2. **Análisis exploratorio de datos:**
   - Estadísticos descriptivos de las variables categóricas y continuas.
   - Visualización gráfica:
     - Gráficos de torta para variables categóricas (`default`, `student`).
     - Histogramas para variables continuas (`balance`, `income`).
     - Gráficos multivariados como pares y gráficos tridimensionales.

3. **Transformaciones:**
   - Asignación de variables dummy para las categóricas.
   - Transformación de variables continuas con logaritmos (Box-Cox).
   - Creación de variables de interacción como:
     - `ln_balance_ln_income`: Interacción entre `ln_balance` e `ln_income`.
     - `ln_balance_student`: Interacción entre `ln_balance` y `student`.

---

### Modelado

Se entrenaron y evaluaron los siguientes modelos:

1. **Regresión Logística:**
   - Modelo entrenado con balanceo de datos (`SMOTE`).
   - Variables de interacción incluidas.
   - Métrica AUC: 0.97.

2. **Árbol de Decisión:**
   - Optimizado con validación cruzada para parámetros de profundidad y nodos hoja.
   - Métrica AUC: 0.84.

3. **Gaussian Naive Bayes:**
   - Modelo entrenado con datos balanceados.
   - Métrica AUC: 0.92.

---

## Resultados

### Comparación de Modelos

| Modelo                   | Precisión | Recall | F1-Score | AUC  |
|--------------------------|-----------|--------|----------|------|
| Regresión Logística      | 1.00      | 0.86   | 0.92     | 0.97 |
| Árbol de Decisión        | 0.99      | 0.88   | 0.93     | 0.84 |
| Gaussian Naive Bayes     | 1.00      | 0.72   | 0.84     | 0.92 |

### Visualización de Curvas ROC

Se generaron las curvas ROC para los tres modelos, evidenciando el desempeño de cada uno según sus valores de AUC.

---

## Conclusiones

- La **regresión logística** fue el modelo más efectivo con un AUC de 0.97, indicando un alto desempeño para predecir incumplimientos.
- Aunque el **árbol de decisión** tuvo un buen desempeño en precisión y recall, su AUC fue menor, lo que lo hace menos robusto para este problema.
- **Gaussian Naive Bayes** presentó un desempeño intermedio, especialmente útil en recall para identificar a los clientes que incumplirán.

---

