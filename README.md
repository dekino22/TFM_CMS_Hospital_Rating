# Sistema de Auditoría Predictiva y Simulador Interactivo What-If (CMS Hospital Rating)

Este repositorio contiene el desarrollo técnico del Trabajo Fin de Máster en **Data Science, Big Data and Business Analytics** (Universidad Complutense de Madrid / NTIC Master) realizado por **Diego Sosa Arteaga**, titulado:
> *"Diseño e Implementación de un Sistema de Auditoría Predictiva y Simulador Interactivo What-If para el Hospital Overall Rating de la CMS"*.

## Descripción del Proyecto

El proyecto desarrolla una solución analítica de extremo a extremo para predecir, auditar y simular la calificación de calidad (*Hospital Overall Rating*, 1 a 5 estrellas) otorgada por los *Centers for Medicare & Medicaid Services* (CMS) a más de 3.000 hospitales estadounidenses.

A través de un enfoque integrado de Ciencia de Datos e Ingeniería Biomédica, la herramienta rompe la "caja negra" de la metodología de evaluación estatal, permitiendo a las direcciones hospitalarias anticipar su puntuación, identificar palancas críticas de mejora y simular el impacto financiero y reputacional de inversiones operativas.

## Tecnologías y Metodología

* **Entorno y Lenguaje:** Python 3.x (Jupyter Notebook / Google Colab)
* **Preprocesamiento y ETL:** `pandas`, `numpy` (Filtros de cobertura >50% nulos, eliminación de multicolinealidad $|r| > 0.85$, imputación por mediana segmentada y división estratificada Train-Test 80/20).
* **Machine Learning Supervisado:** `scikit-learn` (Random Forest Classifier, Support Vector Machines - SVC, Regresión Logística Multinomial, Redes Neuronales MLP).
* **Optimización y Tuning:** Búsqueda en rejilla (`GridSearchCV`) con Validación Cruzada Estratificada ($K=5$) sobre métricas `F1-Weighted` y `F1-Macro`.
* **Explicabilidad AI (XAI):** `shap` (SHapley Additive exPlanations) mediante *TreeExplainer* para análisis de impacto direccional global (Beeswarm) y local (Waterfall plots) basado en teoría de juegos.
* **Productivización y Simulador:** `streamlit` (Cuadro de mando interactivo con simulador de escenarios *What-If* y despliegue mediante túneles HTTPS con `cloudflared`).

## Principales Resultados

1. **Modelo Óptimo:** Random Forest optimizado ($N=500$ árboles, $F_1\text{-Weighted} = 0.52$ en Test independiente) con un 0% de confusión entre categorías extremas (1 vs 5 estrellas).
2. **Factores Determinantes:** 
   * **Riesgo (1 Estrella):** Impulsado por elevadas tasas de mortalidad a 30 días por neumonía (`MORT_30_PN`), complicaciones quirúrgicas e indicadores combinados de reingreso desfavorables (`Hybrid_HWM`).
   * **Excelencia (5 Estrellas):** Liderado por la alta percepción y recomendación del paciente (`H_RECMND_DY`) y la calidad de comunicación del personal sanitario.

## Estructura del Repositorio

* `tfm_notebook_diego_sosa.ipynb`: Cuaderno de trabajo principal que contiene el flujo completo desde el Análisis Exploratorio de Datos (EDA), limpieza, entrenamiento de modelos, evaluación y gráficos explicativos SHAP.
* `README.md`: Resumen ejecutivo y guía técnica del proyecto.
