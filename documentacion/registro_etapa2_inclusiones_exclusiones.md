# Etapa 2 – Registro de inclusiones y exclusiones

**Fecha:** 22/11/2026
**Notebook:** `01_preparacion.ipynb`
**Salida:** `datos_procesados/eph_t2_2017_2026_18mas.parquet` (369.946 filas, 17 columnas)
**Estado:** borrador para revisar.

## 1. Fuentes

- **Bases:** las diez bases del 2.º trimestre, de 2017 a 2026, en formato txt. Se descargaron el 22/11/2026 entre las 13:03 y las 13:04 (hora de Argentina), desde `https://www.indec.gob.ar/ftp/cuadros/menusuperior/eph/EPH_usu_2_Trim_AAAA_txt.zip`. El detalle está en `documentacion/registro_descarga_eph.csv`: URL, nombre del archivo, tamaño, fecha y archivos internos de cada zip.
- **Solo se usa la base individual.** Las 13 columnas que necesita el proyecto están en ella. La base de hogar no aporta variables a la pregunta, y unirla por CODUSU y NRO_HOGAR agregaría un riesgo de error sin ganar información.
- **Los nombres internos de los zip no son uniformes.** Cambian las mayúsculas (`usu_individual_t217`, `USU_individual_t219`, `usu_Individual_T220`) y el orden de los archivos. En 2022, 2023 y 2024 los txt están dentro de una subcarpeta, y en 2022 el nombre termina en `.txt.txt`. Por eso la función de lectura no usa nombres fijos: busca el archivo cuyo nombre, en minúsculas, contiene "individual" y termina en ".txt", y se detiene con un error si no encuentra exactamente uno.
- **Parámetros de lectura:** `sep=";"` y `low_memory=False`. No hizo falta indicar `decimal` ni `encoding`.

## 2. Verificación de estructura

El detalle está en `documentacion/verificacion_bases_eph.csv`.

- **Las nueve variables del proyecto están en los diez años:** CODUSU, CH06, NIVEL_ED, REGION, ESTADO, P21, TOT_P12, PONDIIO y PONDERA.
- **P21, TOT_P12 y PONDIIO se leen como enteros (`int64`) en los diez años.** No hay decimales con coma. Esto confirma sobre los datos que el `C(2)` que el diseño de registro de 2025 asigna a PONDIIO es un error del PDF.
- **Cantidad de columnas:** 177 de 2017 a 2023, 235 en 2024 y 2025, y 234 en 2026. En 2026 se eliminó CAT_INAC (categoría de inactividad) sin que la reemplace otra columna. No afecta al proyecto.
- **Categorías:**
  - NIVEL_ED: códigos del 1 al 7 en los diez años. El código 9 (Ns/Nr) no aparece en ningún año.
  - REGION: los seis códigos (1, 40, 41, 42, 43 y 44) en los diez años. No hace falta recodificar.
  - ESTADO: códigos del 0 al 4 en los diez años.
  - CH06: va de −1 (menos de un año) a un máximo de entre 100 y 104 según el año. No hay códigos especiales mezclados con la edad.
- **Únicos valores negativos en los ingresos:** −9, tanto en P21 como en TOT_P12.

## 3. Columnas de la base procesada

| Tipo | Columnas |
|---|---|
| Identificación | ANO4, CODUSU, NRO_HOGAR, COMPONENTE, AGLOMERADO |
| Variables del proyecto | REGION, CH06, NIVEL_ED, ESTADO, P21, TOT_P12 |
| Ponderadores | PONDIIO (para P21), PONDERA (para las tasas) |
| Creadas | `grupo_edad` (18-29 / 30-39 / 40-64 / 65 o más), `nivel_educativo` (seis categorías), `etapa` (antes / durante / después), `no_presencial` (True en 2020 y 2021) |

AGLOMERADO se conserva para poder marcar los aglomerados que en 2020 no alcanzaron el estándar de calidad del INDEC.

## 4. Inclusiones y exclusiones

### Filas

| Paso | Filas | Diferencia | Criterio |
|---|---|---|---|
| Unión de las diez bases individuales | 498.455 | — | Sin duplicados según ANO4 + CODUSU + NRO_HOGAR + COMPONENTE |
| Filtro de 18 años o más (CH06 ≥ 18) | 369.946 | −128.509 | Población definida para el proyecto |

### Recodificaciones

- **NIVEL_ED = 7 (sin instrucción) se suma a "Primario incompleto".** Después del filtro de edad quedan entre 191 y 365 adultos con este código por año, menos del 1 %. Un grupo tan chico daría promedios poco confiables, y excluirlo sesgaría la parte baja de la distribución.

### Casos que se conservan en la base y se excluyen al calcular

La base procesada conserva a todos los adultos. Las exclusiones se aplican en cada cálculo, para que se pueda informar cuántos casos quedaron afuera y por qué.

| Caso | Magnitud | Tratamiento |
|---|---|---|
| P21 = −9 (no respondió el ingreso) | 32.358 ocupados* en los diez años; entre el 10,8 % y el 18,5 % de los ocupados según el año | Todos tienen PONDIIO = 0: el INDEC los excluye y le pasa su peso a quienes respondieron. Además se filtran de forma explícita al calcular |
| ESTADO = 0 (entrevista individual no realizada) | Entre 53 y 91 casos* por año | Se excluyen del cálculo de las tasas de empleo y de desempleo |
| P21 = 0 (ocupado con ingreso cero) | 5.485 ocupados* en los diez años; tienen PONDIIO > 0 | Pendiente: decisión de la Etapa 3 |
| TOT_P12 = −9 | Sin cuantificar todavía | Pendiente: decisión de la Etapa 3, junto con el ponderador del ingreso ampliado |

\* Estas cifras se calcularon sobre la base de todas las edades. Las cifras para los adultos se calculan en la Etapa 3.

## 5. Hallazgos sobre la muestra

Estas cifras son **casos en la muestra, sin ponderar**. Sirven para juzgar la solidez de cada dato, no para describir a la población.

- **2020 es el año con menos casos:** 37.132, contra unos 59.000 en 2017–2019. Entre 2022 y 2026, la cantidad baja de 50.614 a 44.467 y no vuelve al nivel anterior a la pandemia.
- **GBA en 2020 y 2021:** unos 3.900 casos por año, un 63 % menos que el promedio de 2017–2019 (10.625). **2021 está igual de débil que 2020.** Entre 2022 y 2026, GBA se mantiene alrededor de 7.300 casos, un 32 % por debajo de antes de la pandemia.
- **La no respuesta del ingreso crece:** entre los ocupados, el −9 pasa del 10,8 % en 2019 al 18,5 % en 2026.
- **Ingreso cero en 2020:** el 5,6 % de los ocupados declaró un ingreso de cero, contra un 2,7 % en 2017–2019.
- **La muestra de 18 a 29 años cae un 30 %** entre 2017 y 2026 (de 11.760 a 8.182 casos). La de 65 o más cae un 12 %.

## 6. Decisiones

### Tomadas en esta etapa

1. Se usa solo la base individual.
2. Se trabaja con 13 columnas: las nueve del proyecto más ANO4, NRO_HOGAR, COMPONENTE y AGLOMERADO.
3. NIVEL_ED = 7 se suma a "Primario incompleto". No hay casos con código 9.
4. El −9 en P21 se trata con PONDIIO, que ya lo excluye por diseño, y además se filtra de forma explícita al calcular.
5. ESTADO = 0 se excluye del cálculo de las tasas.
6. La base procesada se guarda en formato parquet, que conserva los tipos de las columnas.

### Pendientes

1. Si el indicador central incluye a los ocupados con ingreso cero (Etapa 3).
2. El tratamiento de TOT_P12 = −9 y el ponderador del ingreso ampliado (Etapa 3).
3. Si se incluye la base preliminar del 2.º trimestre de 2026. Por ahora está incluida.

## 7. Actualizaciones sugeridas para la tarjeta "Comprobaciones y limitaciones"

- **Limitación 2:** ampliarla a 2021. GBA tiene en 2021 la misma cantidad de casos que en 2020.
- **Limitación 6:** la verificación sobre los datos ya está hecha. Las variables del proyecto son comparables en los diez años.
- **Nueva limitación:** la no respuesta del ingreso crece desde 2019 y llega al 18,5 % de los ocupados en 2026.
