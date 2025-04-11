Descripción del Dataset

El dataset utilizado proviene del repositorio de enfermedades cardíacas y contiene variables relevantes que permiten predecir la probabilidad de enfermedad. Columnas del dataset final tras la limpieza:

Variables Numéricas

age: Edad del paciente.

trestbps: Presión arterial en reposo.

chol: Colesterol sérico.

thalch: Frecuencia cardíaca máxima alcanzada.

oldpeak: Depresión del ST.

num: Variable objetivo que indica la presencia de enfermedad cardíaca (0 = No enfermedad, 1 = Enfermedad).

Variables Categóricas

sex: Sexo del paciente (0 = Female, 1 = Male).

cp: Tipo de dolor en el pecho (0 = Typical angina, 1 = Atypical angina, 2 = Non-anginal, 3 = Asymptomatic).

fbs: Azúcar en sangre en ayunas (0 = <120 mg/dl, 1 = >120 mg/dl).

restecg: Resultados del electrocardiograma en reposo (0 = Normal, 1 = ST-T abnormality, 2 = LV hypertrophy).

exang: Ejercicio inducido angina (0 = No, 1 = Sí).

Flujo del 

1. Carga y Preparación de Datos
El dataset fue cargado desde heart_disease_uci.csv.

Se seleccionaron únicamente las columnas necesarias para análisis y modelado.

Se realizaron las siguientes transformaciones:

Codificación de variables categóricas (sex, fbs, exang) a formato binario.

Mapeo ordinal en las variables cp y restecg.

Escalado de variables numéricas usando StandardScaler y MinMaxScaler.

Transformaciones estadísticas (logarítmica y Box-Cox) para corregir sesgos.

2. División del Dataset

Separación de variables independientes (X) y variable objetivo (y):

X: Variables predictoras.

y: Variable objetivo num.

División en conjuntos de entrenamiento (80%) y prueba (20%) utilizando train_test_split para evaluar el modelo con datos no vistos.

3. Entrenamiento de Modelos

Se construyeron varios modelos de Machine Learning para evaluar cuál se adapta mejor al problema:

Regresión Lineal (LinearRegression): Modelo base para regresión.

Regresión Logística (LogisticRegression): Modelo para clasificación binaria.

Árbol de Decisión (DecisionTreeClassifier): Modelo interpretable con estructura jerárquica.

Bosque Aleatorio (RandomForestClassifier): Combina múltiples árboles para mejorar la precisión.

Máquina de Soporte Vectorial (SVC): Encuentra el mejor hiperplano para separar clases.

Vecinos Más Cercanos (KNeighborsClassifier): Clasifica según los puntos más cercanos en el espacio de características.

4. Evaluación de Modelos

Métricas de Regresión:

MSE (Mean Squared Error): Error cuadrático medio.

MAE (Mean Absolute Error): Error absoluto medio.

R² (Coeficiente de Determinación): Explica la variabilidad ajustada por el modelo.

Métricas de Clasificación:

Precisión (accuracy_score)

Recall y Precision

F1 Score

Matriz de Confusión: Evaluación de aciertos y errores.

Curva ROC y AUC

5. Visualización

Se generaron las siguientes visualizaciones para interpretar los resultados:

Scatter Plot: Comparación entre valores reales y predicciones.

Residual Plot: Análisis de errores para detectar patrones.

Matriz de Confusión: Heatmap de aciertos y errores.

Curva ROC: Representación del rendimiento en clasificaciones binarias.

Importancia de Características: Factores más relevantes según el modelo.

6. Predicciones

Se realizaron predicciones sobre registros aleatorios:

Selección aleatoria de un registro en el conjunto de prueba.

Predicción del resultado utilizando el modelo entrenado.

7. Conclusiones

Lo que funcionó:
El modelo de Bosque Aleatorio tuvo el mejor rendimiento debido a su capacidad para manejar datos heterogéneos y multiclase.

Las transformaciones y el escalado mejoraron significativamente el desempeño en SVM y KNN.

La Curva ROC mostró buen AUC (Área Bajo la Curva), destacando la capacidad discriminativa del modelo.

Lo que no funcionó:
El modelo KNN tuvo bajo desempeño en datos de alta dimensionalidad.

El desbalanceo de clases en y afectó el Recall para clases minoritarias.

Mejoras Propuestas:

Implementar técnicas de balanceo como SMOTE para mejorar el rendimiento en clases minoritarias.

Experimentar con modelos avanzados como XGBoost o Gradient Boosting.

Ajustar los hiperparámetros de los modelos con GridSearchCV.
