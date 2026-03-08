# challenge2-data-science-LATAM
# 📊 Telecom X: Análisis de Evasión de Clientes (Churn)

## 🎯 Introducción
El *Churn* (evasión de clientes) es una de las métricas más críticas en la industria de las telecomunicaciones. Este proyecto tiene como objetivo analizar la base de datos de clientes de **Telecom X** para identificar los factores clave que impulsan a los usuarios a cancelar su servicio. Comprender estos patrones es el primer paso para diseñar estrategias de retención efectivas y proteger los ingresos de la compañía.

---

## 🛠️ Herramientas y Tecnologías Utilizadas
- **Python**: Lenguaje principal de análisis.
- **Pandas & Requests**: Para la extracción de datos desde la API y la manipulación tabular.
- **Matplotlib & Seaborn**: Para la visualización de datos y la creación del *Data Storytelling*.

---

## ⚙️ Proceso ETL (Extracción, Transformación y Carga)
Para garantizar la calidad del análisis, se implementó un pipeline ETL riguroso:
1. **Extracción (Extract):** Se consumió la base de datos en formato JSON a través de una API. Se utilizó la técnica de *flattening* (`pd.json_normalize`) para desanidar estructuras complejas y obtener un formato tabular plano.
2. **Transformación (Transform):** - Se tradujeron los nombres de las 20 columnas al español para facilitar la interpretación del negocio.
   - Se corrigieron errores de tipado (forzando valores numéricos en facturaciones totales) y se eliminaron valores nulos.
   - Se creó una nueva métrica de negocio: `Cuentas_Diarias`.
   - Se estandarizó la variable objetivo (`Churn`) a formato binario (1 y 0) para permitir análisis matemáticos.
3. **Carga (Load):** Se exportó el DataFrame limpio como `TelecomX_Limpio.csv`, dejándolo listo para su uso en análisis exploratorios o futuros modelos predictivos.

---

## 📈 Análisis Exploratorio de Datos (EDA) e Insights
A través de visualizaciones descriptivas y una **Matriz de Correlación**, se descubrieron los siguientes patrones críticos respecto a la fuga de clientes:

1. **El Riesgo del Contrato Mensual:** La inmensa mayoría de las deserciones provienen de clientes con contratos "Mes a mes" (*Month-to-month*). Los clientes con contratos anuales o bianuales presentan tasas de retención sumamente altas.
2. **Impacto Directo del Costo:** Existe una correlación positiva fuerte entre el cobro mensual (y las cuentas diarias) con la tasa de abandono. A mayor costo para el usuario, mayor es la probabilidad de fuga.
3. **El Factor "Cheque Electrónico":** Los clientes que utilizan "Electronic check" como método de pago cancelan sus servicios en una proporción alarmantemente mayor en comparación con los que utilizan pagos automáticos o tarjetas de crédito.
4. **Fidelidad como Escudo protector:** La variable de antigüedad (`Meses_Contrato`) tiene una correlación negativa con la evasión. Mientras más tiempo pasa un cliente en la compañía, más estable se vuelve y es menos propenso a cancelar el servicio.

---

## 💡 Recomendaciones Estratégicas
Basado en los datos analizados, se sugieren las siguientes acciones de negocio:
- **Incentivar la migración a Contratos a Largo Plazo:** Diseñar campañas de marketing que ofrezcan descuentos (ej. 10% off) o beneficios exclusivos a los clientes mensuales si deciden firmar contratos de 1 o 2 años.
- **Fomentar el Pago Automático:** Crear un programa de recompensas para los usuarios que actualicen su método de pago de "Cheque Electrónico" a "Transferencia Automática" o "Tarjeta de Crédito".
- **Atención Temprana (Onboarding):** Dado que los clientes más nuevos son los más propensos a irse, es vital implementar un seguimiento cercano e incentivos durante los primeros 6 meses de ciclo de vida del usuario.

---
*Proyecto desarrollado como parte del Challenge de Data Science.*
