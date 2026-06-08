# Proyecto 6 – Análisis de Clientes y Uso de Servicios en ConnectaTel

## 📌 Descripción del Proyecto

Este proyecto tiene como objetivo analizar el comportamiento de uso de los clientes de ConnectaTel, una empresa de telecomunicaciones con operaciones en México y Colombia.

A partir de información sobre clientes, planes contratados y uso real de servicios móviles (llamadas y mensajes), se realizó un proceso completo de exploración, limpieza, análisis y segmentación de usuarios para identificar patrones de comportamiento y generar recomendaciones de negocio.

---

## 🎯 Objetivo

Comprender cómo utilizan los clientes los servicios de telecomunicaciones para:

* Detectar problemas de calidad de datos.
* Identificar patrones de uso de llamadas y mensajes.
* Encontrar usuarios con comportamientos atípicos.
* Segmentar clientes según edad y nivel de uso.
* Generar recomendaciones para optimizar la oferta comercial y mejorar la experiencia del cliente.

---

## 📂 Datasets Utilizados

### 1. plans.csv

Contiene la información de los planes disponibles.

Variables principales:

* plan
* monthly_price
* included_minutes
* included_gb
* extra_minute_cost

---

### 2. users_latam.csv

Información de los clientes registrados.

Variables principales:

* user_id
* age
* city
* reg_date
* plan

---

### 3. usage.csv

Registro histórico de uso de servicios.

Variables principales:

* user_id
* type (call o text)
* duration
* length
* date

---

## 🧹 Etapas del Análisis

### 1. Carga y Exploración de Datos

* Importación de librerías.
* Carga de datasets.
* Revisión de estructura mediante:

  * `.head()`
  * `.shape`
  * `.info()`

---

### 2. Identificación de Problemas de Calidad

Se analizaron:

* Valores nulos.
* Valores inválidos (sentinels).
* Fechas fuera de rango.
* Tipos de datos incorrectos.

Problemas detectados:

* Edad con valor sentinel: `-999`
* Ciudad desconocida representada como `?`
* Fechas posteriores al año 2024
* Valores nulos dependientes del tipo de evento (MAR)

---

### 3. Limpieza de Datos

Acciones realizadas:

* Reemplazo de `-999` por la mediana de edad.
* Conversión de `?` a valores nulos.
* Marcado de fechas futuras como nulas.
* Conversión de columnas a tipos adecuados.

---

### 4. Construcción de Métricas por Usuario

A partir del dataset de uso se generaron indicadores agregados:

* Cantidad de mensajes.
* Cantidad de llamadas.
* Total de minutos consumidos.

Posteriormente se integraron al perfil de cada usuario.

---

### 5. Análisis Exploratorio

Se realizaron:

#### Estadística descriptiva

* Media
* Mediana
* Cuartiles
* Valores máximos y mínimos

#### Visualizaciones

* Histogramas
* Boxplots
* Distribuciones por plan

Variables analizadas:

* age
* cant_mensajes
* cant_llamadas
* cant_minutos_llamada

---

### 6. Detección de Outliers

Se utilizaron:

* Boxplots
* Método IQR

Los valores extremos identificados fueron conservados debido a que representan comportamientos reales de usuarios intensivos.

---

### 7. Segmentación de Clientes

#### Segmentación por Uso

* Bajo uso
* Uso medio
* Alto uso

Basada en:

* Cantidad de llamadas
* Cantidad de mensajes

#### Segmentación por Edad

* Joven (< 30 años)
* Adulto (30–59 años)
* Adulto Mayor (60+ años)

---

### 8. Insights y Recomendaciones

Principales hallazgos:

* La mayoría de los clientes presenta un uso moderado.
* Los usuarios Premium tienden a acumular más minutos de llamada.
* Existen usuarios intensivos con alto potencial comercial.
* Los patrones de mensajes y llamadas son similares entre planes.

Recomendaciones:

* Diseñar planes específicos para usuarios intensivos.
* Crear ofertas diferenciadas por edad.
* Implementar estrategias de fidelización para clientes de alto consumo.

---

## ▶️ Cómo Ejecutar el Proyecto

### Opción 1: Google Colab

1. Abrir Google Colab.
2. Crear un nuevo notebook.
3. Subir:

   * plans.csv
   * users_latam.csv
   * usage.csv
4. Copiar y ejecutar las celdas del notebook en orden.

---

### Opción 2: Jupyter Notebook

Instalar dependencias:

```bash
pip install pandas numpy matplotlib seaborn
```

Abrir Jupyter:

```bash
jupyter notebook
```

Ejecutar el notebook desde la primera celda hasta la última.

---

## 🔁 Guía de Reproducción

1. Cargar los tres datasets.
2. Realizar exploración inicial.
3. Detectar valores nulos y sentinels.
4. Limpiar edades, ciudades y fechas.
5. Agregar métricas de uso por usuario.
6. Unir información de usuarios y uso.
7. Generar estadísticas descriptivas.
8. Crear histogramas y boxplots.
9. Detectar outliers mediante IQR.
10. Segmentar clientes por edad y nivel de uso.
11. Elaborar conclusiones y recomendaciones.

---

## 🛠️ Tecnologías Utilizadas

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook / Google Colab

---

## 👤 Autor

Priscila Garcia

Proyecto académico de análisis exploratorio de datos (EDA) y segmentación de clientes para ConnectaTel.
