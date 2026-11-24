# Etapa 3 – Registro de preparación de los ingresos

**Fecha:** 23/11/2026
**Notebook:** `01_preparacion.ipynb`, secciones 7 a 11 (versión revisada del 23/11/2026)
**Entrada:** `datos_procesados/eph_t2_2017_2026_18mas.parquet` (369.946 adultos, salida de la Etapa 2)
**Salidas:**
- `datos_procesados/eph_t2_2017_2026_18mas_ingresos.parquet` (369.946 filas, 20 columnas: las 17 de la Etapa 2 más `factor_ipc`, `p21_real` e `ing_lab_real`)
- `datos_procesados/deflactor_ipc_t2.csv`
- `documentacion/registro_descarga_ipc.csv`

**Estado:** cerrada el 23/11/2026. El notebook corre limpio con "Reiniciar y ejecutar todo".
**Última actualización:** 23/11/2026, después de la revisión del notebook (hora de descarga del IPC, estado y pendientes).

## 1. Situación del ingreso entre los adultos ocupados

Población: adultos con ESTADO = 1. Son 208.828 en los diez años. Las cifras son **casos de la muestra, sin ponderar**.

| Año | Ocupados | P21 = −9 | P21 = 0 | P21 > 0 | TOT_P12 > 0 | TOT_P12 = −9 |
|---|---|---|---|---|---|---|
| 2017 | 24.127 | 16,1 % | 2,6 % | 81,4 % | 7,0 % | 1,4 % |
| 2018 | 23.571 | 14,5 % | 2,7 % | 82,8 % | 7,8 % | 1,4 % |
| 2019 | 24.247 | 10,8 % | 2,6 % | 86,5 % | 9,3 % | 1,3 % |
| 2020 | 12.770 | 11,3 % | 5,5 % | 83,2 % | 6,5 % | 1,0 % |
| 2021 | 19.326 | 14,1 % | 2,8 % | 83,2 % | 7,8 % | 1,4 % |
| 2022 | 22.141 | 16,0 % | 2,4 % | 81,6 % | 8,9 % | 1,5 % |
| 2023 | 21.740 | 17,0 % | 2,1 % | 80,9 % | 9,1 % | 1,7 % |
| 2024 | 20.660 | 17,5 % | 1,9 % | 80,6 % | 9,2 % | 1,8 % |
| 2025 | 20.312 | 18,0 % | 2,2 % | 79,9 % | 9,3 % | 1,8 % |
| 2026 | 19.934 | 18,5 % | 1,8 % | 79,7 % | 8,8 % | 2,1 % |

- **Verificación:** en todos los años, P21 = −9, P21 = 0 y P21 > 0 suman el total de ocupados. El único código negativo es −9.
- **Superposición de la no respuesta:** la mayoría de los casos con TOT_P12 = −9 tampoco respondieron P21. Por ejemplo, en 2017 hay 346 casos con TOT_P12 = −9, y solo 146 de ellos respondieron P21.

## 2. Decisiones sobre los ingresos

### Indicador central: P21 > 0

El ingreso de la ocupación principal se calcula solo con los casos que tienen P21 > 0, con el ponderador PONDIIO. La proporción de ocupados con ingreso cero se informa aparte, año por año.

**Motivo:** el ingreso cero es estable, entre el 1,8 % y el 2,8 %, salvo en 2020, que llega al 5,5 %. Ese salto muestra ocupados que no cobraron, un efecto de la pandemia. Si se incluyeran en el promedio, bajarían la media y el efecto quedaría oculto. Informados aparte, se ven.

> **Nota agregada en la Etapa 6 (24/11/2026):** las proporciones de ingreso cero de este documento son **sin ponderar**. Ponderadas con PONDERA sobre todos los ocupados, que es la cifra que se informa en los resultados, van del 2,2 % al 3,0 % por año y llegan al 4,5 % en 2020 (Etapa 4). Además, el salto de 2020 coincide con la cuarentena y con el relevamiento telefónico, y no se atribuye a una causa: ver `hallazgos_y_limitaciones.md`, sección 3.

### Ingreso laboral ampliado: PONDIIO, sin TOT_P12 = −9

El ingreso ampliado (P21 + TOT_P12) se calcula con PONDIIO, solo para los casos con P21 > 0 y TOT_P12 ≥ 0.

**Motivo:**
- La pérdida adicional respecto del indicador central es chica: entre el 0,3 % y el 0,9 % de los ocupados por año (sección 4).
- Se descartó PONDII porque corrige la no respuesta del ingreso individual total (P47T), que incluye ingresos no laborales como las jubilaciones. Usarlo podía excluir casos con ingreso laboral válido. Además, habría obligado a volver a leer las diez bases.

**Costo:** el peso de los casos excluidos no se reparte entre los demás, como sí hace PONDIIO con el −9 de P21. El sesgo es menor y se informa junto con el indicador.

## 3. IPC y deflactor

### Fuente

- **Archivo:** `datos_originales/ipc/serie_ipc_divisiones.csv` (1.252.806 bytes), descargado el 23/11/2026 a las 12:08 (hora de Argentina) desde `https://www.indec.gob.ar/ftp/cuadros/economia/serie_ipc_divisiones.csv`.
- **Historial de la descarga:** la primera descarga fue a las 11:05. Mientras la celda no comprobaba si el archivo ya existía, se volvió a descargar a las 11:42 y a las 12:08, y la versión vigente es la de las 12:08. El contenido no cambió: mismo tamaño, mismos 119 meses y mismos factores. Desde la revisión del notebook, la celda no descarga el archivo si ya está en Drive, para no sobrescribir el original.
- **Serie:** IPC nacional con base diciembre de 2016 = 100. El INDEC mantuvo la metodología vigente, porque el nuevo IPC, anunciado para enero de 2026, se postergó. La serie cubre todo el período sin cambio de base, así que no hace falta empalmar.
- **Lectura:** `sep=";"`, `encoding="latin-1"` (el archivo no está en UTF-8) y `decimal=","`.
- **Filtro:** `Region == "Nacional"` y `Descripcion == "NIVEL GENERAL"`. "NIVEL GENERAL" se repite para cada una de las seis regiones, así que filtrar solo por la descripción mezclaría siete series.
- **Controles:** 119 meses (de diciembre de 2016 a octubre de 2026), sin repetidos. El índice vale 100 en diciembre de 2016 y 12.785,9321 en octubre de 2026.

### Criterio

- **Mes base:** octubre de 2026, el último publicado (informe técnico del 12/11/2026). Queda fijo hasta el final del proyecto.
- **Período de referencia del ingreso:** marzo a mayo. La EPH pregunta por el ingreso percibido el mes anterior a la entrevista, y las entrevistas del 2.º trimestre se hacen de abril a junio. Es una aproximación, porque la base no informa el mes de cada entrevista.

$$F_t = \frac{IPC_{\text{oct-2026}}}{\overline{IPC}_{t,\ \text{mar–may}}}$$

| Año | Factor |
|---|---|
| 2017 | 117,790 |
| 2018 | 93,682 |
| 2019 | 60,068 |
| 2020 | 41,219 |
| 2021 | 28,241 |
| 2022 | 17,873 |
| 2023 | 8,539 |
| 2024 | 2,222 |
| 2025 | 1,495 |
| 2026 | 1,127 |

El factor baja de un año al siguiente. El salto más grande está entre 2023 y 2024, el tramo de mayor inflación del período.

## 4. Variables creadas

| Variable | Definición | Casos sin valor |
|---|---|---|
| `factor_ipc` | Factor del año, asignado según ANO4 | Ninguno |
| `p21_real` | P21 × factor, en pesos de octubre de 2026 | NaN si P21 ≤ 0: no respuesta (−9), ingreso cero y no ocupados |
| `ing_lab_real` | (P21 + TOT_P12) × factor, en pesos de octubre de 2026 | NaN si P21 ≤ 0 o TOT_P12 = −9 |

El −9 nunca se multiplica por el factor: queda como faltante (NaN), no como un ingreso negativo.

### Casos válidos por indicador

| Año | `p21_real` | `ing_lab_real` | Diferencia | % de los ocupados |
|---|---|---|---|---|
| 2017 | 19.632 | 19.490 | 142 | 0,6 % |
| 2018 | 19.517 | 19.396 | 121 | 0,5 % |
| 2019 | 20.985 | 20.856 | 129 | 0,5 % |
| 2020 | 10.625 | 10.587 | 38 | 0,3 % |
| 2021 | 16.072 | 15.993 | 79 | 0,4 % |
| 2022 | 18.058 | 17.942 | 116 | 0,5 % |
| 2023 | 17.590 | 17.480 | 110 | 0,5 % |
| 2024 | 16.659 | 16.530 | 129 | 0,6 % |
| 2025 | 16.220 | 16.093 | 127 | 0,6 % |
| 2026 | 15.895 | 15.720 | 175 | 0,9 % |

### Controles

- Ningún año quedó sin factor.
- El mínimo de `p21_real` es de $3.415,68: no hay ingresos reales negativos ni iguales a cero.
- La cantidad de casos con `p21_real` coincide en cada año con los ocupados con P21 > 0 de la sección 1. Esto confirma que ningún no ocupado tiene P21 > 0.
- `ing_lab_real` nunca tiene más casos que `p21_real`.

## 5. Hallazgos

- **La no respuesta de P21 tiene forma de U.** Entre los adultos ocupados es del 16,1 % en 2017, llega a un mínimo del 10,8 % en 2019 y desde entonces sube hasta el 18,5 % en 2026. 2019 es el punto más bajo, no el nivel habitual anterior a la pandemia.
- **El ingreso cero se duplica en 2020** (5,5 % frente a alrededor del 2,6 % en 2017–2019), aunque la muestra de ese año es la mitad.
- **El ingreso de otras ocupaciones es poco frecuente:** entre el 6,5 % y el 9,3 % de los ocupados tiene TOT_P12 > 0. El indicador ampliado solo se diferencia del central para ese grupo.
- **Hay ingresos muy bajos:** el mínimo de `p21_real` equivale a unos $3.400 mensuales de octubre de 2026. No se recortan en esta etapa.

## 6. Pendientes

1. ~~Ejecutar "Reiniciar y ejecutar todo" en `01_preparacion.ipynb` y confirmar que corre limpio.~~ **Resuelto:** corre limpio, con los contadores del 1 al 33 y los mismos resultados.
2. ~~**Pagos retroactivos en TOT_P12.**~~ **Resuelto:** quedó registrado como limitación 10 en la tarjeta "Comprobaciones y limitaciones". Los ingresos de otras ocupaciones pueden incluir pagos de trabajos anteriores o retroactivos, que con las variables disponibles no se pueden separar.
3. **Valores extremos:** evaluar en la Etapa 4, al analizar la distribución, los ingresos muy bajos y muy altos. Por eso la mediana debe acompañar a la media.
4. Si se incluye la base preliminar del 2.º trimestre de 2026. Por ahora está incluida.

## 7. Actualizaciones aplicadas en Trello

Las tres actualizaciones se aplicaron el 23/11/2026 en la tarjeta "Comprobaciones y limitaciones":

- **Limitación 4:** la pérdida del indicador ampliado va del 0,3 % al 0,9 % de los ocupados. El máximo es 2026.
- **Ítem "Inflación" de la lista Verificaciones:** marcado. La serie es adecuada y el mes base está documentado.
- **Ítem "Ingresos complementarios":** marcado. Las decisiones sobre las otras ocupaciones y los faltantes están tomadas, y los retroactivos quedaron como limitación 10. También se marcó "Ponderaciones".
