# challenger_telecomX1
Telecom X - Análisis de Evasión de Clientes




# 📝 Informe de Análisis de Evasión de Clientes (Churn)

## 1. 📌 Introducción

El objetivo de este análisis es entender los factores que influyen en la evasión de clientes (`Churn`) en una empresa de telecomunicaciones. La evasión representa la pérdida de clientes, lo cual impacta directamente en los ingresos. A través de este análisis, se buscan patrones que expliquen el abandono del servicio para diseñar estrategias de retención.

---

## 2. 🧹 Limpieza y Preparación de Datos

**Acciones realizadas:**

- Conversión de columnas numéricas como `Charges.Total` y `Charges.Monthly` a tipo `float`.
- Reemplazo de valores nulos y espacios en blanco.
- Estandarización de la columna `Churn`, asignando `"Sin registro"` a datos faltantes.
- Creación de la variable `Cuentas_Diarias` = `Charges.Monthly` / 30.

---

## 3. 📊 Análisis Exploratorio de Datos (EDA)

### 🔸 Distribución de `Churn`
- Se visualizó con `countplot`, diferenciando tres categorías: `Yes`, `No`, y `Sin registro` (colores: verde, rojo y amarillo).
- Se observó un balance moderado entre quienes se quedan y se van, con algunos sin registro.

### 🔸 Variables Categóricas
Se analizaron variables como:
- **Género (`gender`)**
- **Tipo de contrato (`Contract`)**
- **Método de pago (`PaymentMethod`)**

**Insight:** Los clientes con contratos mensuales y métodos de pago electrónicos muestran más probabilidad de evasión.

### 🔸 Variables Numéricas
Se compararon entre grupos de `Churn`:
- `Charges.Total`
- `tenure` (meses de contrato)
- `Charges.Monthly`
- `Cuentas_Diarias`

**Insight:** Clientes que cancelan tienden a tener menor antigüedad (`tenure`) y gasto total.

---

## 4. 📈 Estadísticas Descriptivas por Grupo de Churn

Se calcularon: **media, mediana, desviación estándar, mínimo y máximo** por grupo (`Yes`, `No`, `Sin registro`) para variables numéricas.

```python
df_final.groupby('Churn')[['Charges.Total', 'Charges.Monthly', 'tenure', 'Cuentas_Diarias']].agg(
    ['mean', 'median', 'std', 'min', 'max']).round(2)


