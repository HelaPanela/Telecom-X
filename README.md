# Telecom-X
Se analizó la evasión de clientes en una empresa de telecomunicaciones. Se limpiaron y transformaron los datos, se exploraron patrones con gráficos y se identificaron factores clave asociados a la cancelación, como el tipo de contrato, los servicios contratados y la antigüedad. El análisis ofrece insights útiles para reducir la tasa de cancelación.

# 1. Introducción

El presente análisis tiene como objetivo identificar patrones asociados a la cancelación de servicios por parte de los clientes en una empresa de telecomunicaciones. Se busca comprender los factores que influyen en la evasión (churn) para tomar decisiones que mejoren la retención de clientes.

# 2. Limpieza y Tratamiento de Datos

Durante esta etapa se realizaron varias acciones clave para garantizar que los datos fueran fiables, consistentes y adecuados para el análisis:

## Revisión de Valores Faltantes y Duplicados
Se detectaron valores ausentes únicamente en la columna Cancelacion (224 registros), los cuales fueron marcados como NaN para su posterior análisis o eliminación.
No se encontraron duplicados en la columna de identificador de cliente (ID_Cliente), asegurando que cada registro representa a un cliente único.

## Transformación de Datos
Se convirtieron varias columnas que contenían valores categóricos como "Yes"/"No" a variables binarias (1 para "Yes" y 0 para "No"), lo cual facilita su análisis estadístico y el modelado posterior.
Las columnas que inicialmente contenían respuestas mixtas como "No phone service" o "No internet service" fueron homogeneizadas y transformadas en respuestas válidas para evitar inconsistencias semánticas. Por ejemplo:
"No internet service" fue convertido a "No" en columnas como StreamingTV, OnlineSecurity, TechSupport, etc.

## Conversión de Tipos de Datos
Se convirtieron las columnas numéricas como SeniorCitizen, tenure, Charges.Monthly y Charges.Total al tipo float o int según correspondía, asegurando que estuvieran listas para cálculos y visualizaciones.

## Creación de Nuevas Variables
Se creó una columna adicional llamada Factura_Diaria, que calcula el valor diario promedio a partir de la facturación mensual (Factura_Mensual / 30). Esta variable permite observar con más detalle el comportamiento financiero de los clientes.

## Renombrado de Columnas
Para facilitar la comprensión, todas las columnas fueron traducidas al español con nombres descriptivos. Ejemplo:

gender → Genero
tenure → Meses_Antiguedad
PaperlessBilling → Factura_Electronica

Este tratamiento permitió transformar un conjunto de datos con múltiples inconsistencias en una base estructurada, limpia y estandarizada para su análisis exploratorio.

# 3. Análisis Exploratorio de Datos
Se aplicaron diversas técnicas estadísticas y gráficas para explorar los datos y detectar patrones asociados a la cancelación del servicio. Se dividió el análisis en dos partes: variables categóricas y numéricas.

# Distribución General de Cancelación
Se identificó que aproximadamente 26.5% de los clientes cancelaron el servicio, mientras que el 73.5% permanecieron. Esta proporción sugiere que existe una base sólida de usuarios fieles, aunque una cuarta parte representa un riesgo de fuga.

# Análisis de Variables Categóricas
Se examinaron múltiples variables para detectar cómo se comportan frente a la cancelación.

### Tipo de Contrato:

Los clientes con contrato mensual (Month-to-month) tienen una tasa de cancelación significativamente más alta que quienes tienen contratos de un año o dos años.
Esto sugiere que la flexibilidad del contrato mensual también facilita la baja.

### Método de Pago:
El método Electronic check está asociado con la mayor tasa de cancelación.
En contraste, clientes con pagos automáticos (Bank transfer, Credit card) tienden a quedarse más tiempo.

### Adulto Mayor:
No hay diferencias drásticas entre adultos mayores y no mayores en cuanto a cancelación, aunque los adultos mayores tienden a permanecer un poco más.

### Factura Electrónica:
Los clientes que usan factura electrónica presentan una ligera mayor propensión a cancelar, lo que podría estar asociado al perfil digital de usuario o menor compromiso con el servicio.

### Servicios Adicionales (StreamingTV, Soporte Técnico, etc.):
Aquellos que no usan servicios adicionales como StreamingTV, Soporte Técnico, Protección de Dispositivos o Seguridad Online, muestran mayor tasa de cancelación.

Esto indica que mientras más servicios consume un cliente, mayor es su permanencia, posiblemente por mayor satisfacción o dependencia del paquete.

## Análisis de Variables Numéricas
### Factura Diaria (Factura_Diaria):
Los clientes que cancelaron tienden a tener una factura diaria ligeramente menor, lo que puede indicar que los clientes que menos gastan también son más propensos a dejar el servicio.

### Meses de Antigüedad (Meses_Antiguedad):
Los usuarios que han estado menos tiempo en la compañía presentan tasas de cancelación mucho más altas, especialmente durante los primeros meses.

Esto sugiere que existe una alta rotación temprana, y que los primeros meses son críticos para la fidelización del cliente.

# 4. Conclusiones
- El tipo de contrato influye fuertemente en la cancelación: los clientes con contrato mes a mes cancelan con mayor frecuencia.
- Los clientes con menos tiempo en la empresa (menor antigüedad) tienden a cancelar más que aquellos con mayor permanencia.
- El método de pago también está relacionado: quienes usan “Electronic Check” presentan una tasa de cancelación más alta.
- Los servicios adicionales como respaldo online, soporte técnico y protección de dispositivos están asociados con menor cancelación.
- La facturación diaria más baja es común entre quienes cancelan, lo que puede reflejar menor compromiso con el servicio.

# 5. Recomendaciones
- Fomentar contratos a largo plazo (anuales o bianuales) con incentivos como descuentos o beneficios exclusivos.
- Ofrecer promociones o asesoría personalizada a clientes nuevos para aumentar la permanencia durante los primeros meses.
- Incentivar métodos de pago automáticos como transferencias o tarjetas, que se asocian con menor cancelación.
- Promover el uso de servicios adicionales mediante paquetes o pruebas gratuitas que aumenten el valor percibido.
- Segmentar y contactar a clientes con bajo gasto y poca antigüedad, para prevenir su posible cancelación.
