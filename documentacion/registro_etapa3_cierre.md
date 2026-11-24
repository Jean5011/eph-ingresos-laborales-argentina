# Etapa 3 – Registro de cierre

**Proyecto:** Ingresos laborales en Argentina (EPH, INDEC)
**Fecha de cierre:** 23/11/2026
**Estado:** cerrada. Las siete tareas del checklist están marcadas y la tarjeta está en "Hecho".
**Notebook:** `01_preparacion.ipynb`, secciones 7 a 11 (versión revisada del 23/11/2026). Corre limpio de principio a fin.

## 1. Entradas y salidas

**Entrada:** `datos_procesados/eph_t2_2017_2026_18mas.parquet`, 369.946 adultos, salida de la Etapa 2.

**Salidas:**

| Archivo | Contenido |
|---|---|
| `datos_procesados/eph_t2_2017_2026_18mas_ingresos.parquet` | 369.946 filas, 20 columnas: las 17 de la Etapa 2 más `factor_ipc`, `p21_real` e `ing_lab_real` |
| `datos_procesados/deflactor_ipc_t2.csv` | Factor de deflación de cada año |
| `documentacion/registro_descarga_ipc.csv` | Registro de la descarga del IPC |
| `documentacion/registro_etapa3_ingresos.md` | Registro técnico del procedimiento |

La celda de guardado termina con un control `.exists()` sobre los dos archivos de salida, de modo que el guardado se verifica en cada ejecución.

## 2. Decisiones tomadas

**Indicador central: solo P21 > 0, con PONDIIO.** La proporción de ocupados con ingreso cero se informa aparte, año por año. El ingreso cero es estable entre el 1,8 % y el 2,8 %, salvo en 2020, que llega al 5,5 %. Ese salto son ocupados que no cobraron, un efecto de la pandemia: incluirlos en el promedio lo bajaría y ocultaría el efecto; informados aparte, se ven.

> **Nota agregada en la Etapa 6 (24/11/2026):** las proporciones de ingreso cero de este documento son **sin ponderar**. Ponderadas con PONDERA sobre todos los ocupados, que es la cifra que se informa en los resultados, van del 2,2 % al 3,0 % por año y llegan al 4,5 % en 2020 (Etapa 4). Además, el salto de 2020 coincide con la cuarentena y con el relevamiento telefónico, y no se atribuye a una causa: ver `hallazgos_y_limitaciones.md`, sección 3.

**Ingreso ampliado (P21 + TOT_P12): PONDIIO, excluyendo TOT_P12 = −9.** Se calcula solo para los casos con P21 > 0 y TOT_P12 ≥ 0. Se descartó PONDII porque corrige la no respuesta del ingreso individual total (P47T), que incluye ingresos no laborales como las jubilaciones, y usarlo podía excluir casos con ingreso laboral válido. El costo de la decisión es que el peso de los casos excluidos no se reparte entre los demás, como sí hace PONDIIO con el −9 de P21; el sesgo es menor y se informa junto con el indicador.

**El −9 nunca se multiplica por el factor.** Queda como faltante (NaN), no como un ingreso negativo.

## 3. IPC y deflactor

**Fuente:** `datos_originales/ipc/serie_ipc_divisiones.csv`, 1.252.806 bytes, descargado el 23/11/2026 a las 12:08 (la primera descarga fue a las 11:05; se repitió durante la revisión del notebook y el contenido no cambió) desde `https://www.indec.gob.ar/ftp/cuadros/economia/serie_ipc_divisiones.csv`.

**Serie:** IPC nacional, base diciembre de 2016 = 100. Cubre todo el período sin cambio de base, de modo que no hubo que empalmar series. El INDEC mantuvo la metodología vigente porque el nuevo IPC, anunciado para enero de 2026, se postergó.

**Lectura:** `sep=";"`, `encoding="latin-1"` (el archivo no está en UTF-8) y `decimal=","`.

**Filtro:** `Region == "Nacional"` y `Descripcion == "NIVEL GENERAL"`. La descripción "NIVEL GENERAL" se repite para cada una de las seis regiones, así que filtrar solo por ella mezclaría siete series.

**Controles:** 119 meses, de diciembre de 2016 a octubre de 2026, sin repetidos. El índice vale 100 en diciembre de 2016 y 12.785,9321 en octubre de 2026.

**Mes base:** octubre de 2026, el último publicado al cierre de la etapa. Queda fijo hasta el final del proyecto.

**Período de referencia del ingreso:** marzo a mayo. La EPH pregunta por el ingreso percibido el mes anterior a la entrevista, y las entrevistas del segundo trimestre se hacen de abril a junio. Es una aproximación, porque la base no informa el mes de cada entrevista.

**Fórmula:** factor del año = IPC de octubre de 2026 dividido por el promedio del IPC de marzo a mayo de ese año.

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

| Variable | Definición | Faltante cuando |
|---|---|---|
| `factor_ipc` | Factor del año, asignado según ANO4 | Nunca |
| `p21_real` | P21 × factor, en pesos de octubre de 2026 | P21 ≤ 0: no respuesta (−9), ingreso cero y no ocupados |
| `ing_lab_real` | (P21 + TOT_P12) × factor, en pesos de octubre de 2026 | P21 ≤ 0 o TOT_P12 = −9 |

## 5. Controles verificados

- Ningún año quedó sin factor.
- El mínimo de `p21_real` es $3.415,68. No hay ingresos reales negativos ni iguales a cero.
- La cantidad de casos con `p21_real` coincide en cada año con los ocupados con P21 > 0. Esto confirma que ningún no ocupado tiene P21 > 0.
- `ing_lab_real` nunca tiene más casos que `p21_real`.
- En todos los años, P21 = −9, P21 = 0 y P21 > 0 suman el total de ocupados. El único código negativo es −9.

## 6. Hallazgos

**La no respuesta de P21 tiene forma de U.** Entre los adultos ocupados es del 16,1 % en 2017, baja a un mínimo del 10,8 % en 2019 y desde entonces sube hasta el 18,5 % en 2026. Conviene no leer 2019 como el nivel habitual anterior a la pandemia: es el punto más bajo de la serie.

**El ingreso cero se duplica en 2020:** 5,5 % frente a alrededor del 2,6 % en 2017–2019, aunque la muestra de ese año es la mitad.

**El ingreso de otras ocupaciones es poco frecuente.** Entre el 6,5 % y el 9,3 % de los ocupados tiene TOT_P12 > 0, de modo que el indicador ampliado solo se diferencia del central para ese grupo.

**Hay ingresos muy bajos.** El mínimo de `p21_real` equivale a unos $3.400 mensuales de octubre de 2026. No se recortaron en esta etapa.

**La pérdida del indicador ampliado respecto del central** va del 0,3 % al 0,9 % de los ocupados por año. El máximo es 2026, con 175 casos.

## 7. Limitaciones declaradas en esta etapa

1. **Pagos retroactivos en TOT_P12.** Los ingresos de otras ocupaciones pueden incluir pagos de trabajos anteriores o retroactivos. Con las variables disponibles no se pueden separar. Es una limitación del indicador ampliado.
2. **Período de referencia aproximado.** El deflactor usa el promedio de marzo a mayo porque la base no informa el mes de cada entrevista.
3. **Casos excluidos sin redistribución de peso** en el indicador ampliado, por el uso de PONDIIO.

## 8. Decisión que sigue abierta

Si se incluye la base preliminar del segundo trimestre de 2026. Por ahora está incluida.

## 9. Traspaso a la Etapa 4 – Analizar

**Notebook:** `02_analisis.ipynb`. **Entrada:** `datos_procesados/eph_t2_2017_2026_18mas_ingresos.parquet`.

Puntos a tener presentes al analizar:

1. **La media sola no alcanza.** Hay ingresos muy bajos y la distribución de ingresos es asimétrica. La mediana debe acompañar a la media en todos los cortes.
2. **Los valores extremos se evalúan en esta etapa**, al ver la distribución. No se recortó nada antes.
3. **Toda estimación de ingreso va ponderada con PONDIIO.** Las de población, con PONDERA.
4. **La no respuesta creciente de P21 es en sí un resultado**, no solo un problema técnico: pasa del 10,8 % en 2019 al 18,5 % en 2026 y conviene informarla junto con los niveles de ingreso.
5. **2020 y 2021 van marcados** en todos los cuadros y gráficos, por el cambio de modalidad de relevamiento.
6. **GBA en 2020 y 2021 tiene poca muestra:** unos 3.900 casos, un 63 % menos que en los años presenciales. Cualquier lectura regional de esos dos años debe decirlo.
