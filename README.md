# 💄 Aura Beauty Co. — Dashboard de Ventas Omnicanal y Análisis de Devoluciones

![Power BI](https://img.shields.io/badge/Power_BI-F2C94C?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)

## 📌 Resumen del Proyecto

Este proyecto analiza el rendimiento comercial omnicanal de **Aura Beauty Co.**, una empresa de productos cosméticos con presencia en tres canales principales: **Retail Store (Tienda Física)**, **E-commerce** y **Distribuidores**.

El objetivo central es optimizar la estrategia de ventas y el margen de ganancia por canal y categoría de producto, identificando de forma cuantitativa el impacto financiero que generan las devoluciones sobre la rentabilidad del negocio.

---

## 📊 Vistas del Dashboard

> 🔗 **¡Explora el reporte interactivo en vivo!** Puedes interactuar con los filtros y la visualización completa haciendo clic en el siguiente enlace:
> [👉 Ver Dashboard Interactivo de Aura Beauty Co. en Power BI](https://app.powerbi.com/view?r=eyJrIjoiMTZlNGJmZTUtZTA0Yi00Y2QzLWFmZDItNmJkMGI5MzAwYjhmIiwidCI6IjE0ZjNhOWRhLWQ5OWMtNGZjMi1iNTFlLTlkMGQxZGNkNWNhMCJ9)

![Dashboard Overview](assets/dashboard_overview.png)

---

## 🎯 Preguntas de Negocio Respondidas

1. **Rendimiento por Categoría:** ¿Qué categoría (*Skin Care, Makeup, Hair Care, Fragrance*) genera el mayor volumen de ventas en comparación con su margen de beneficio?
2. **Comparativa de Canales:** ¿Cómo se distribuyen los ingresos entre Retail, E-commerce y Distribuidores, y cuál presenta mayor rentabilidad?
3. **Impacto Financiero de Devoluciones:** ¿Cuánto dinero se pierde directamente en devoluciones por categoría y cuál presenta la tasa porcentual más crítica?

---

## 💡 Hallazgos Clave (Insights de Negocio)

### 1. Salud Financiera y Comportamiento Omnicanal
* **Desempeño Global:** Ventas netas totales de **\$199.40K**, con una ganancia bruta de **\$119.84K** y un **margen promedio del 60.10%**.
* **Dominio del Canal Digital:** El canal **E-commerce lidera las ventas con el 50% del total (\$100K)**, seguido por Retail Stores (\$80K / 40%). El canal de Distribuidores mantiene una participación marginal (\$19K / 10%).
* **Estacionalidad:** La tendencia mensual refleja caídas pronunciadas en marzo (\$14K), julio y septiembre (\$15.2K), contrastando con picos en abril, agosto y noviembre (\$17.5K - \$18.5K).

### 2. Análisis por Categoría (Volumen vs. Rentabilidad)
* **Skin Care como Motor Comercial:** Aporta el mayor volumen de ingresos (\$77K) con un margen alineado al promedio general (60.59%).
* **Makeup Diluye el Margen:** Segunda categoría en volumen (\$63K), pero registra el margen de ganancia más bajo del catálogo (58.08%).
* **Oportunidad en Fragrance y Hair Care:** Registran los márgenes más altos (61.70% y 61.59%), aunque Fragrance se encuentra subexplotada en volumen (\$19K).

### 3. Fuga Financiera por Devoluciones
* **Tasa Global:** La tasa general de devolución es del **7.53%**, representando un impacto directo sobre la utilidad neta.
* **Skin Care Lidera Pérdidas Monetarias:** Genera la mayor pérdida absoluta (\$6.6K perdidos) con una tasa de devolución del 8.11%.
* **Hair Care con la Tasa más Crítica:** Presenta la tasa de devolución porcentual más alta (9.72%), sumando \$4.0K perdidos.
* **Makeup es la más Estable:** Registra la tasa de devolución más baja del catálogo (5.32%, \$3.1K perdidos).

---

## 🚀 Recomendaciones Estratégicas

1. **Intervención Operativa en Hair Care y Skin Care:**
   * Auditar causas raíz de devolución en E-commerce (posibles fallas en empaque/sellado en tránsito o discrepancias en la ficha del producto).
   * Mejorar descripciones web e incluir guías claras de aplicación para reducir insatisfacción.
2. **Optimización del Margen en Makeup:**
   * Revisar costos de adquisición o reducir descuentos directos para elevar el margen (58.08%) hacia el promedio general (~60%).
3. **Estrategia de Venta Cruzada (*Bundling* en Fragrance):**
   * Aprovechar el margen del 61.70% en Fragrance creando paquetes promocionales combinados con productos estrella de Skin Care en el canal E-commerce.
4. **Mitigación de Estacionalidad Baja:**
   * Diseñar campañas de lealtad y promociones exclusivas para amortiguar los valles de facturación de marzo, julio y septiembre.
5. **Reevaluación del Canal Distribuidores:**
   * Evaluar si la contribución neta del canal (\$19K / 10%) compensa los costos operativos y logísticos asociados, o si conviene reasignar presupuesto a E-commerce y Retail.

---

## 🛠️ Tecnologías y Herramientas Utilizadas

* **Python (Pandas, NumPy):** Limpieza, imputación de valores nulos, estandarización de tipos de datos y estructuración del conjunto de datos.
* **Power BI Desktop:** Modelado de datos (Esquema en Estrella), arquitectura visual y diseño UX/UI.
* **DAX (Data Analysis Expressions):** Creación de medidas explícitas para cálculo de ventas netas, márgenes y tasa de devoluciones.

---

## 📐 Medidas Clave en DAX

```dax
// 1. Ventas Netas Totales
Ventas Netas = SUM(Ventas[Venta_Neta])

// 2. Ganancia Total
Ganancia Total = SUM(Ventas[Ganancia_Bruta])

// 3. Tasa de Devolución (%)
Tasa Devolución % = 
DIVIDE(
    CALCULATE(COUNTROWS(Ventas), Ventas[Devuelto] = 1),
    COUNTROWS(Ventas),
    0
)

// 4. Monto Perdido por Devoluciones
Monto Perdido Devoluciones = 
SUMX(
    FILTER(Ventas, Ventas[Devuelto] = 1),
    Ventas[Venta_Neta]
)
