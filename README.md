# Análisis de Clientes y Patrones de Uso — ConnectaTel

## 🎯 Objetivo del proyecto
Analizar la calidad de los datos, los patrones de uso y la segmentación de clientes de **ConnectaTel** en Python para traducir los hallazgos en conclusiones accionables y recomendaciones sobre la oferta de planes (`Basico` y `Premium`).

## 📂 Datasets utilizados
* **`plans.csv`**: Catálogo de planes (`Basico` y `Premium`).
* **`users_latam.csv`**: Información de usuarios (`4,000` registros) con edad, ciudad, fecha de registro, fecha de baja y plan.
* **`usage.csv`**: Registro de actividad (`40,000` eventos de llamadas y mensajes de texto).

## 🧪 Etapas del análisis realizadas
1. **Carga y exploración inicial:** Revisión de estructura, tipos de datos y resumen estadístico de los archivos.
2. **Calidad y limpieza de datos:**
   - Reemplazo del valor centinela `-999` en `age` por la mediana (`48.0`).
   - Conversión del centinela `'?'` en `city` a `pd.NA`.
   - Conversión de fechas futuras (`2026`) en `reg_date` a `NaT`.
   - Conservación de nulos en `duration` y `length` (`usage`) al identificar un patrón *Missing At Random* (MAR) según el tipo de evento (`call` vs. `text`).
3. **Consolidación de perfil y distribuciones:** Agregación de `usage` por `user_id` (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`), unión hacia `users` en `user_profile` y visualización de distribuciones por plan.
4. **Análisis de outliers:** Identificación de valores extremos mediante boxplots y cálculo de límites superiores con IQR (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`), manteniéndolos por corresponder a consumo elevado real.
5. **Segmentación de clientes:** Creación de las variables `grupo_uso` (`Bajo uso`, `Uso medio`, `Alto uso`) y `grupo_edad` (`Joven`, `Adulto`, `Adulto Mayor`) junto con sus gráficos de distribución.
6. **Insight ejecutivo:** Síntesis de problemas de datos, comportamiento por segmentos, clientes de mayor valor, implicaciones de los *outliers* y propuestas de mejora para los planes.

## ▶️ Cómo ejecutar el notebook
1. Entra al archivo `.ipynb` dentro de este repositorio en **GitHub**.
2. Ábrelo en **Google Colab** (o descárgalo/clónalo para abrirlo en Jupyter Notebook o VS Code).
3. Asegúrate de tener instaladas `pandas`, `numpy`, `matplotlib` y `seaborn` (ya disponibles en Google Colab).

## 🔁 Guía de reproducción
1. Abre el notebook en el entorno de tu preferencia (por ejemplo, Google Colab).
2. Coloca `plans.csv`, `users_latam.csv` y `usage.csv` en la ruta esperada por el código.
3. Ejecuta las celdas de forma secuencial (o usa *Run all*) para reproducir la limpieza, la creación de `user_profile`, los gráficos y el análisis ejecutivo.
