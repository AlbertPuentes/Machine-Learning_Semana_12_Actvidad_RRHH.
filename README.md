# Machine-Learning_Semana_12_Actvidad_RRHH.
Semana 12: Ejercicio de Aplicación (Caso de estudio RRHH) ML Supervisado
# Análisis de los Resultados caso de estudio de RRHH

## 1. Interpretar: FN, FP, TP, TN 
En la matriz de confusión se evalúo los aciertos y errores del modelo comparando las predicciones con la realidad: 1 = Renuncia, 0 = Permanece

* **TP (Verdadero Positivo):** El modelo predijo que el empleado renunciaría 1, y el empleado renunció.
* **TN (Verdadero Negativo):** El modelo predijo que el empleado se quedaría 0, y el empleado permaneció en la empresa.
* **FP (Falso Positivo):** El modelo predijo que el empleado renunciaría 1, pero en realidad decidió quedarse 0. Es una falsa alarma.
* **FN (Falso Negativo):** El modelo predijo que el empleado se quedaría 0, pero sorpresivamente renunció 1. Es el error más crítico en este escenario lo que genera costos imprevistos.

## 2. ¿Por qué es importante predecir la rotación de empleados?
Predecir la rotación permite a la gerencia pasar de ser reactiva a proactiva. Facilita la identificación de talento en riesgo antes de que se presente una carta de renuncia, brindando a Recursos Humanos una ventana de tiempo para intervenir con mejores condiciones, planes de carrera o ajustes, logrando así retener al personal clave.
Reducción de costos: Evita gastos de reclutamiento y capacitación.
Preservación del conocimiento: Se Minimiza la pérdida de experiencia.
Productividad: Mantiene la continuidad operativa y evita curvas de aprendizaje.
Clima laboral: Reduce el impacto negativo en la moral del equipo.

## 3. ¿Qué impacto económico puede generar la renuncia de personal?
La fuga de talento tiene un costo elevado para la organización, dividido en dos categorías:
* **Costos Directos:** 
• Reclutamiento: anuncios, headhunters, tiempo de selección
• Onboarding: capacitación, mentoría, materiales
• Productividad perdida: tiempo de capacitacion para alcanzar pleno rendimiento

* **Costos Indirectos:** 
• Sobrecarga al equipo restante, más rotación
• Pérdida de relaciones con clientes, proveedores
• Impacto en reputación marca empleadora

## 4. ¿Por qué este problema corresponde a un problema de clasificación supervisada?
Este caso corresponde a un problema supervisado porque alimentamos al algoritmo con datos históricos que ya poseen una etiqueta de respuesta correcta la columna, renuncia. 
Es de clasificación porque la variable objetivo es categórica y discreta las opciones son excluyentes: 0 = permanece, 1 = renuncia, a diferencia de la regresión que estima valores numéricos continuos.

## 5. Entre las variables (edad, salario, años de permanencia en la empresa, nivel de satisfacción, horas extras) ¿cuáles de ellas tendrán mayor influencia sobre la renuncia de un empleado y por qué?

### Variables con mayor influencia
De acuerdo al dataset, las variables más determinantes son:
1. **Nivel de satisfacción:** Refleja el clima y estado emocional. Valores bajos suelen correlacionarse con renuncias.
2. **Horas extras:** Indican sobrecarga y riesgo de *burnout*. 
3. **salario:** Salarios por debajo del mercado incentivan la búsqueda externa
4. **edad** perfiles jóvenes con salarios bajos tienden a rotar con mayor frecuencia en busca de nuevas oportunidades.

## 6. Agregue al modelo dos variables (entre: clima laboral, liderazgo, modalidad de trabajo, evaluación de desempeño). ¿Considera ud que el modelo predictivo podría mejorar? ¿Por qué si y por qué no?

Sí, el modelo podría mejorar sustancialmente. Variables como el liderazgo son razones primarias de renuncia a nivel global, y la modalidad de trabajo aporta contexto actual de gran valor. 

**Posibles limitaciones**:
Dificultad para medir objetivamente.
Riesgo de multicolinealidad con satisfacción.
Requieren recolección de datos adicional.

## 7. Al ejecutar el algoritmo, ¿cuál sería la interpretación de cada una de las métricas?
* **Accuracy (Exactitud):** Total de predicciones correctas. Engañosa si hay desbalance de clases.
* **Precision (Precisión):** La calidad de los positivos. De todos los que predijo que renunciarían, ¿cuántos realmente lo hicieron?. Penaliza los Falsos Positivos.
* **Recall (Sensibilidad):** La capacidad de hallazgo. De todos los que realmente renunciaron, ¿cuántos logró detectar el modelo?. Penaliza los Falsos Negativos.
* **F1-Score:** La media armónica entre Precisión y Recall. Ideal para evaluar modelos con datos desbalanceados.

## 8. Suponga que uno de los modelos obtuvo: Accuracy = 0.90, precisión = 0.70, recall = 0.95, F1-Score = 0.80. ¿Es un buen modelo?
Es un excelente modelo para Recursos Humanos. Aunque la Precisión del 0.70 indica que genera algunas falsas alarmaspredice que alguien se va cuando en realidad se queda, el Recall de 0.95 indica que es capaz de detectar al 95% de las personas que realmente se van a ir, el F1-Score 0.80 indica que es equilibrado lo que da un balance entre no alarmar innecesariamente y no perder casos reales.

## 9. ¿Cuál de las métricas considera más importante y cuál sería el motivo?
La métrica más importante para este caso es Recall. 
Motivo: es preferible lidiar con un Falso Positivo que sufrir un Falso Negativo.
En RRHH, el costo de un Falso Negativoes mucho mayor que el de un Falso Positivo.

## 10. Si el modelo presenta muchos “Falsos Negativos”, ¿qué consecuencias podría tener para la empresa?

###Consecuencias de los Falsos Negativos
Si existen muchos Falsos Negativos, la gerencia tendría una falsa sensación de seguridad. El modelo predice que el personal es estable, pero habra renuncias que seguirían ocurriendo sorpresivamente. De esta manera el algoritmo perdería credibilidad y la empresa seguiría absorbiendo los altos costos de rotación.

## 11. Después de ejecutar el algoritmo con los diferentes modelos,¿cuál fue el mejor modelo según la métrica F1-Score? ¿Por qué cree que este modelo tuvo el mejor desempeño?

El mejor modelo según F1-Score.
Al ejecutar los algoritmos con el dataset educativo adjunto, modelos como Regresión Logística, Árboles de Decisión y Random Forest obtienen un F1-Score (1.0). Se debe a que el dataset de prueba es extremadamente pequeño apenas 20 registros y las variables clave como el nivel de satisfacción y las horas extras separan a los empleados que renuncian de los que se quedan de una manera muy clara y evidente. En un entorno real con miles de registros y datos se genera mas ruido, lo cual ocasiona que los resultados varien y modelos como Random Forest o SVM destacarían por encima de los más simples.

¿Por qué tuvo el mejor desempeño?
No fue por superioridad algorítmica, sino por un dataset demasiado pequeño, patrones linealmente separables en la muestra, y azar en la partición de datos. En un entorno real con más datos, Random Forest o Gradient Boosting suelen superar a LR en problemas no lineales, mientras que LR sigue siendo preferible por interpretabilidad.

## 12. Aunque Random Forest tenga mejor Accuracy, ¿en qué escenario sería más conveniente utilizar un Árbol de Decisión?
Aunque un Random Forest suele ser más exacto, se elegiría un Árbol de Decisión cuando la interpretabilidad sea prioritaria. Random Forest funciona como una caja negra en contraste, un Árbol de Decisión simple permite extraer reglas de negocio claras para presentar.
En datasets pequeños, un árbol de Decisión puede generalizar mejor que un ensemble que busca patrones complejos. 

## 13. Desde el punto de vista de la ética, ¿Considera ético utilizar Machine Learning para predecir la renuncia de empleados?

Depende del uso que se le da al ML,  es ético si los datos utilizados se manejan en totales con el fin de mantener en minimos la tasa de renincias, generando estrategias que aumenten lamotivacion de los empleados de forma general, y no es ético si las predicciones son utilizadas de forma individual con cada empleado por ejemplo negar ascensos o despedir anticipadamente a un empelado al que el ML predijo tendria posibilidad de una pronta renuncia. 

## 14. Si estuviéramos analizando 10.000 empleados y la mayoría NO renuncia, ¿Qué problema podría presentarse?
 
Si el 95% del personal nunca renuncia, nos enfrentamos a un problema de Desbalanceo de Clases. El modelo podría predecir que nadie renuncia y aún así obtener un Accuracy del 95%, siendo completamente inútil al fallar en detectar al 5% crítico. Requiere el uso de métricas como el F1-Score y técnicas de remuestreo como SMOTE.

## 15. Explique el concepto de “Overfitting”. ¿Esto podría ocurrir en este caso de estudio?

El Overfitting sucede cuando el algoritmo memoriza los datos de entrenamiento incluyendo ruido y patrones aleatorios, perdiendo capacidad de generalizar a nuevos datos. En este caso de estudio es muy seguro que ocurra, ya que entrenar modelos con apenas 20 registros resultaría en la memorización de empleados específicos en lugar de patrones reales.

## 16. Si ud fuera el (la) gerente de RRHH, ¿prefería un modelo más preciso pero difícil de explicar? o ¿preferiría un modelo menos preciso pero fácil de interpretar?
Si fuese Gerente de RRHH, Preferiria un modelo que sea fácil de interpretar aunque sea menos preciso, ya que para justificar cambios en la empresa se hace  necesario explicar el por qué y si el modelo es fácil de interpretar seria mucho mas sencillo realizar esta actividad de lo predicho por el modelo, lo cual no seria sencillo con un modelo mas complejo aunque sea mas preciso.

## 17. ¿Cuál considera es el mejor algoritmo para este caso de estudio? ¿Cuál es la justificación?
Para este dataset educativo en particular, la Regresión Logística asi como un Árbol de Decisión de poca profundidad son las mejores opciones. 
Son menos propensos al sobreajuste en muestras pequeñas, altamente interpretables y, dado que la relación de variables es clara, ofrecen resultados perfectos o cuasi-perfectos sin la sobrecarga de computación de modelos más densos.
El Árbol de Decisión es elseria la mejor opción porque logra el equilibrio entre aciertos de las predicciones en este escenario, no requiere un poder computacional alto y traduce los datos en información que cualquier gerente sin conocimientos especiales como en  Machine Learning lo que le permite entender de forma mas sencilla.
