# Yelp para Restaurantes

## Introducción

Fue analizada una muestra equilibrada de 28.097 personas, de las cuales 14.065 son mujeres y 14.032 hombres. El objetivo fue identificar patrones de consumo, perfiles demográficos y patrones de consumo sobre clientes en restaurantes de Estados Unidos.

## Estructura

```
├── Avance_EDA.ipynb                     # Notebook con todo el análisis
├── base_datos_restaurantes_USA_v2.csv   # Dataset original
├── Avance_2_API_Yelp.ipynb              # Estudio complementario
└── README.md
```

## Metodología y limpieza de datos

El archivo csv fue trabajado con Python en el archivo `Avance_EDA`.

- En primer lugar, se filtraron valores atípicos como edad en valores negativos o superiores a 80 años, dejando como rango edades entre 18 y 80 años.
- En segundo lugar, fueron eliminadas variables que no tenían utilidad para el análisis. En esta ocasión fue el teléfono y el correo electrónico.
- Por otro lado, los valores nulos en relación a edades faltantes o promedio de gasto fueron completados utilizando la media de sus respectivas columnas.
- Fue creada una nueva categoría de nombre "No especificado" para las preferencias alimenticias faltantes (4,7% aprox.).
- En tercer lugar, los gastos con valores menores a $1 fueron eliminados.

Por otro lado, se obtuvieron datos por medio de una API en la página web Yelp.com y se trabajó en el archivo `Avance_2_API_Yelp`. De este se obtuvo información de 5.700 restaurantes, aunque el 37,5% no tenía información de los precios, por lo que fueron eliminados aquellos registros sin información.

## Análisis descriptivo

**Con el archivo `Avance_EDA`:**

- En primer lugar, se segmentaron las edades.
- Agrupé las preferencias alimenticias en categorías más amplias (Vegano, Vegetariano, Consumidor de Carne, etc.) para facilitar la comparación entre ciudades.
- Analicé las ciudades para comprender el comportamiento de consumo según la ubicación geográfica y cuál es la influencia que puede tener una membresía "Premium" en el gasto total de las personas.
- También realicé histogramas y gráficos de densidad para ver cómo se distribuyen los ingresos económicos en el dataset.

**Con el archivo `Avance_2_API_Yelp`:**

- Generé una tabla para cruzar las categorías de comida con los niveles de precio ($, $$, $$$). Esto permitió identificar cuántos restaurantes de mariscos había y en qué rango de precio se encontraban.
- Realicé una consulta para ver los mejores restaurantes de toda la lista basándome en el rating y la cantidad de reseñas.
- Filtré el DataFrame para aislar únicamente los restaurantes cuya `categoria_principal` fuera igual a `'Seafood'`.
- Ordené estos resultados por calificación de forma descendente y seleccioné los 5 primeros registros.
- Finalmente, ordené estos resultados para comparar los nombres de los restaurantes frente a su calificación.
