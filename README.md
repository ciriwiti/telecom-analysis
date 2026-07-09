ConnectaTel - Análisis de uso de servicios móviles

Análisis exploratorio de datos de una empresa de telecomunicaciones: limpieza, detección de outliers y segmentación de clientes por edad y nivel de uso (llamadas/mensajes) con python, pandas y seaborn.

Análisis exploratorio de datos (EDA) sobre el comportamiento de uso de clientes de una empresa de telecomunicaciones con operaciones en México y Colombia. 
El proyecto integra tres fuentes de datos (usuarios, uso real y planes), realizando limpieza, validación de calidad construyendo segmentaciones de clientes para identificar oportunidades comerciales.

Contexto de negocio
ConnectaTel necesita entender cómo sus clientes usan realmente sus servicios móviles (llamadas y mensajes) para optimizar su oferta comercial y mejorar la experiencia del usuario. Este análisis responde cuatro preguntas de negocio:

1. ¿Qué segmentos de clientes muestran mayor o menor uso de llamadas y mensajes?
2. ¿Qué usuarios presentan valores atípicos que puedan indicar comportamientos inusuales, fraude o errores de registro?
3. ¿Cómo varía el uso según la edad y el tipo de plan contratado?
4. ¿Qué patrones pueden ayudar a diseñar mejores planes, optimizar la oferta y mejorar la satisfacción del cliente?

Datos
- plans.csv: Catálogo de planes (precio, minutos incluidos, GB, costo por extra) con 2 planes.
- users_latam.csv: Datos de clientes: edad, ciudad, fecha de registro, plan, churn con 4,000 usuarios.
- usage.csv: Detalle de uso real: llamadas (duración) y mensajes (longitud) con 40,000 registros

Metodología
1. Carga y exploración: estructura, tipos de dato y dimensiones de cada dataset.
2. Auditoría: nulos, sentinels (-999, "?") y fechas fuera de rango.
3. Limpieza de datos: imputación de age con la mediana, estandarización de city, corrección de fechas inválidas (reg_date: año 2026), conversión de tipos.
4. Estadística descriptiva: perfil de uso por cliente (mensajes, llamadas, minutos totales).
5. Visualización y outliers: histogramas por plan y método IQR + boxplots.
6. Segmentación: grupos de uso (bajo/medio/alto) y grupos de edad (joven/adulto/Persona mayor).
7. Insight ejecutivo: hallazgos y recomendaciones comerciales.

Hallazgos clave
El plan contratado no está correlacionado con el uso real ni con la edad del cliente: las proporciones de cada segmento de uso y de edad son prácticamente idénticas entre los planes básico y premium (diferencias menores a 2 puntos porcentuales).
El 73.6% de los clientes se ubica en un nivel de uso medio; solo el 7.0% es de alto uso, un segmento pequeño pero de mayor potencial de ingreso.
La variable con el sesgo y los outliers más marcados es la cantidad de minutos de llamada: el 2.7% de los usuarios supera el límite superior IQR (61.86 min), frente a menos del 1.2% en mensajes y llamadas.
Los nulos en duration y length son estructurales (dependen del tipo de registro: llamada vs mensaje), no representan un problema de calidad.

Herramientas
Python, Pandas, Numpy, Seaborn, Matplotlib, Jupyter, Notebook

Estructura del repositorio
S7_ConnectaTel_completo.ipynb ---- Notebook con el análisis completo
plans.csv ------------------------ Catálogo de planes
users_latam.csv ------------------ Datos de clientes
usage.csv ------------------------ Detalle de uso real
README.md

Ejecución
1. git clone https://github.com/<tu-usuario>/connectatel-analisis.git
2. cd connectatel-analisis
3. pip install pandas numpy seaborn matplotlib jupyter
4. jupyter notebook telecom-analysis.ipynb
