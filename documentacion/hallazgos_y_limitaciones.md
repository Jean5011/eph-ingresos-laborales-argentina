# Ingresos laborales en Argentina, 2017–2026: hallazgos y limitaciones

**Proyecto:** Evolución de los ingresos laborales según edad, educación y región en Argentina: antes, durante y después de la cuarentena
**Fuente:** Encuesta Permanente de Hogares (EPH) e Índice de Precios al Consumidor (IPC) nacional, INDEC
**Período:** segundo trimestre (abril a junio) de cada año, de 2017 a 2026
**Versión:** 23/11/2026 (Etapa 6)
**Notebook asociado:** `notebooks/04_interpretacion.ipynb`, que recalcula cada cifra citada a partir de las tablas de `resultados/`

---

## Índice

1. [En pocas palabras](#1-en-pocas-palabras)
2. [A quién representan los resultados](#2-a-quién-representan-los-resultados)
3. [Cómo leer 2020 y 2021](#3-cómo-leer-2020-y-2021)
4. [Hallazgos por pregunta](#4-hallazgos-por-pregunta)
5. [Limitaciones](#5-limitaciones)
6. [Glosario](#6-glosario)
7. [Fuentes y archivos](#7-fuentes-y-archivos)

---

## 1. En pocas palabras

**Pregunta principal:** ¿cómo evolucionaron los ingresos laborales según la edad, el nivel educativo y la región entre 2017 y 2026?

- **El ingreso real de la ocupación principal es menor en 2026 que en 2017.** El promedio (media) bajó un 16,1 %, de 1,52 a 1,28 millones de pesos de octubre de 2026. El valor del medio (mediana) bajó un 13,9 %.
- **La caída no empezó en 2020.** Entre 2018 y 2019 la media y la mediana ya habían bajado alrededor de un 13 %. El punto más bajo de la serie es 2024, alrededor de un 30 % por debajo de 2017. En 2025 hubo un repunte y 2026 (dato preliminar) vuelve a quedar por debajo.
- **La caída alcanzó a todos los grupos**, pero el orden entre ellos se mantuvo:
  - las personas de 18 a 29 años siguen siendo las de menor ingreso;
  - a mayor nivel educativo, mayor ingreso;
  - Patagonia sigue siendo la región de ingresos más altos y el Noreste, una de las más bajas.
- **La magnitud de la caída varió.** Entre los grupos con resultados sólidos, el Noreste fue el que más cayó (−27,6 %). Varios grupos quedaron cerca del promedio general (−16,1 %), con caídas de entre el 16 % y el 17 %: entre ellos, las personas de 30 a 39 años, la región Pampeana y el nivel superior completo, que es el nivel educativo que menos cayó.
- **El mercado de trabajo y el ingreso se movieron en direcciones distintas.** Después de la cuarentena (2022–2026), en comparación con antes (2017–2019):
  - hay más personas ocupadas (61,3 % frente a 57,2 %);
  - hay menos desempleo (7,2 % frente a 9,6 %);
  - el ingreso real medio de quienes trabajan es alrededor de un 16 % menor.

Estos resultados **describen** lo que se observó. No permiten afirmar que la cuarentena, ni ningún otro factor, haya causado estos cambios.

---

## 2. A quién representan los resultados

- **Personas de 18 años o más que viven en los 31 aglomerados urbanos que releva la EPH.** No representan a la población rural ni al total del país.
- **Ingresos:** corresponden a las personas **ocupadas** que declararon un ingreso mayor a cero en su ocupación principal.
  - Las personas ocupadas que declararon ingreso cero, entre el 2,2 % y el 3,0 % por año (4,5 % en 2020), se informan aparte.
  - Quienes no declararon su ingreso se compensan con el ponderador que publica el INDEC para ese fin (PONDIIO). Ver la limitación 4.
- **Empleo y desempleo:** se calculan sobre toda la población de 18 años o más de esos aglomerados (empleo) o sobre quienes trabajan o buscan trabajo (desempleo).
- **Pesos constantes:** todos los ingresos están expresados en **pesos de octubre de 2026**, ajustados con el IPC nacional. Así, un valor de 2017 y uno de 2026 pueden compararse en poder de compra.
- **Período:** solo el segundo trimestre de cada año. No describe lo que pasó en el resto de cada año.
- **Tamaño de la muestra:** entre 10.625 (2020) y 20.985 (2019) personas ocupadas con ingreso informado por año.

---

## 3. Cómo leer 2020 y 2021

**Qué cambió en la encuesta**

La Encuesta Permanente de Hogares (EPH) suele hacerse en persona: un encuestador del INDEC visita las viviendas seleccionadas y entrevista a sus integrantes. Con las restricciones de la cuarentena, desde el segundo trimestre de 2020 hasta el primero de 2022 se hizo por teléfono. En este proyecto quedan afectados dos de los diez años analizados: 2020 y 2021.

**Qué consecuencias tuvo sobre los datos**

El cambio afectó tres aspectos.

- **Respondió menos gente.** En el segundo trimestre de 2020, de 26.940 viviendas seleccionadas respondieron 11.841, el 44 %. Cuando la respuesta baja tanto, crece el riesgo de que quienes contestan no se parezcan a quienes no lo hacen. Por ejemplo, puede que sea más fácil contactar a algunos hogares que a otros. El INDEC ajustó los ponderadores para compensarlo, pero el ajuste no elimina el problema por completo.
- **La calidad no fue pareja entre regiones.** Quince aglomerados no alcanzaron el estándar de calidad del INDEC en 2020. Entre ellos están la Ciudad de Buenos Aires y los partidos del Gran Buenos Aires, los dos aglomerados que forman la región GBA, la más poblada. En este proyecto, GBA pasa de unos 3.200 ocupados con ingreso informado por año en 2017–2019 a 994 en 2020 y 1.169 en 2021. Sus cifras de esos años son las menos precisas de toda la serie.
- **Los ingresos se declararon con menos exactitud.** Hay evidencia de que, durante el período telefónico, la distancia entre los ingresos declarados en la encuesta y los ingresos reales se amplió. Como el indicador central de este proyecto es justamente un ingreso, los valores de 2020 y 2021 podrían estar más subestimados que los de otros años.

**Qué significa para la interpretación**

Las cifras de 2020 y 2021 combinan dos cosas que no se pueden separar: lo que efectivamente ocurrió en el mercado de trabajo durante la cuarentena y el efecto de haber cambiado la forma de relevar los datos. Por ejemplo, la tasa de empleo baja del 57,4 % en 2019 al 46,9 % en 2020, y la de desempleo sube del 10,6 % al 13,1 %. La dirección de esos cambios es clara, pero su tamaño exacto debe leerse con cautela.

**Cómo se usan en este proyecto**

- **Se muestran.** Forman parte de la serie y dan contexto. En los gráficos aparecen señalados con una franja gris, y en el resumen por etapas, con una barra rayada.
- **No sostienen las conclusiones.** Los hallazgos principales comparan los años en que la encuesta se hizo en persona: antes (2017–2019) y después (2022–2026). Esa comparación es más confiable porque ambos períodos se relevaron de la misma manera.
- **No miden el impacto de la cuarentena.** Este proyecto describe lo que se observó durante esos años; no afirma que la cuarentena haya causado esos cambios ni estima cuánto los causó.

---

## 4. Hallazgos por pregunta

Cada hallazgo indica **qué se observa**, **con qué grado de certeza** y **qué figura lo muestra**. Las variaciones comparan 2017 con 2026, salvo que se indique otra cosa. Una variación es **sólida** (robusta) cuando la media y la mediana van en la misma dirección y difieren en menos de 4 puntos.

### 4.1 ¿Cómo cambió el ingreso de la ocupación principal año por año?

**Qué se observa**

| Año | Media (millones) | Mediana (millones) |
|---|---|---|
| 2017 | 1,52 | 1,18 |
| 2018 | 1,52 | 1,31 |
| 2019 | 1,32 | 1,14 |
| 2020 ▒ | 1,32 | 1,11 |
| 2021 ▒ | 1,27 | 1,00 |
| 2022 | 1,19 | 0,98 |
| 2023 | 1,21 | 1,02 |
| 2024 | 1,06 | 0,82 |
| 2025 | 1,38 | 1,05 |
| 2026 (prel.) | 1,28 | 1,01 |

▒ Relevamiento telefónico. Pesos de octubre de 2026.

- Entre 2018 y 2019, antes de la cuarentena, la media y la mediana bajan alrededor de un 13 %.
- En 2020 y 2021 (relevamiento telefónico) la serie sigue bajando, de forma moderada.
- **2024 es el punto más bajo:** la media queda un 30,5 % por debajo de 2017 y la mediana, un 30,2 %.
- En 2025 hay un repunte: alrededor de un +30 % respecto de 2024.
- En 2026 (dato preliminar), la media baja un 7,3 % respecto de 2025.
- **Saldo 2017–2026:** −16,1 % con la media y −13,9 % con la mediana.

**Con qué grado de certeza**

- La caída entre 2017 y 2026 es sólida: se repite con la media y la mediana, y con cuatro formas distintas de ajustar por inflación (entre −15,9 % y −16,5 %).
- 2024 es el mínimo con cualquiera de esas cuatro formas.
- **El tamaño del repunte de 2025 es incierto:** según el mes de precios que se tome como referencia, va de +24 % a +35 %. Se debe a la inflación mensual muy alta de comienzos de 2024 (limitación 7).
- 2026 es una base preliminar.

**Figura:** `fig01_ingreso_anual` (media, mediana y banda de sensibilidad al ajuste por inflación).

---

### 4.2 ¿Qué diferencias se observan entre los grupos de edad?

**Qué se observa**

- **Los tres grupos de 18 a 64 años caen en magnitudes parecidas:** 18 a 29 años, −18,4 %; 30 a 39 años, −16,6 %; 40 a 64 años, −17,8 % (con la media).
- **Las personas de 18 a 29 años tienen siempre el ingreso más bajo.** En 2026, su media (0,93 millones) equivale a dos tercios de la del grupo de 40 a 64 años (1,40 millones). Esa proporción es la misma que en 2017.
- El grupo de 40 a 64 años tiene la media más alta entre los grupos de 18 a 64, entre un 4,1 % y un 14,9 % por encima del de 30 a 39, según el año. Con la mediana, los dos grupos empatan en casi todos los años (ver limitación 6).
- En los cuatro grupos, 2024 es el año más bajo.

**Con qué grado de certeza**

- Las variaciones de los tres grupos de 18 a 64 años son sólidas.
- **El grupo de 65 años o más no es concluyente.** Con la media cae un 6,2 % y con la mediana, un 28,3 %. Es el grupo más chico (entre 308 y 776 casos por año) y sus valores oscilan mucho de un año a otro.
- El grupo de 65 años o más se define solo por la edad. No se asume que sus integrantes estén jubilados: son personas de esa edad que trabajan.

**Figura:** `fig03_ingreso_edad` (un panel por grupo; 65 o más en gris).

---

### 4.3 ¿Cómo varían los ingresos según el nivel educativo?

**Qué se observa**

- **A mayor nivel educativo, mayor ingreso, en todos los años.** La única excepción es menor: en 2023, el secundario incompleto queda apenas por debajo del primario completo.
- **El nivel superior completo es el que menos cae:** −17,0 % con la media y −17,1 % con la mediana.
- El secundario incompleto (−26,5 %) y el secundario completo (−20,2 %) caen más.
- **La distancia entre los extremos se amplía.** En 2017, una persona con nivel superior completo ganaba en promedio 2,56 veces lo que una con primario incompleto; en 2026, 2,83 veces.
- **Asociación entre educación e ingreso:** la correlación de Spearman es positiva y moderada todos los años. Va de 0,34 (2017) a 0,40 (2021) y vuelve a 0,33 (2026). El máximo cae en los años de relevamiento telefónico, así que ese aumento debe leerse con cautela. La correlación mide qué tan ordenada es la relación (más educación, más ingreso); no mide cuánto más se gana ni implica que la educación cause el ingreso.

**Con qué grado de certeza**

- Son sólidas las variaciones de secundario incompleto, secundario completo y superior completo.
- **No son sólidas** las de primario incompleto (−24,9 % con la media; −36,2 % con la mediana), primario completo y superior incompleto: la media y la mediana difieren en más de 8 puntos.
- El primario incompleto es el grupo más chico, con entre 310 y 839 casos por año. Incluye a las personas sin instrucción.
- El nivel superior agrupa terciario, universitario y posgrado (limitación 11).

**Figura:** `fig04_ingreso_educacion` (un panel por nivel).

---

### 4.4 ¿Qué diferencias aparecen entre las regiones?

**Qué se observa**

- **En 2026, las seis regiones están por debajo de 2017**, y en todas 2024 es el año más bajo.
- **El Noreste es la región que más cae:** −27,6 % con la media y −25,6 % con la mediana. En 2026 su ingreso equivale al 72 % del de 2017.
- Le sigue Cuyo (−22,2 %). Noroeste (−16,8 %) y Pampeana (−16,5 %) caen en una magnitud similar al promedio.
- **Patagonia tiene el ingreso más alto en todos los años.** Su media es alrededor de 1,8 veces la del Noroeste, tanto en 2017 como en 2026.

**Con qué grado de certeza**

- Son sólidas las variaciones de Noreste, Cuyo, Noroeste y Pampeana.
- **No son sólidas las de Gran Buenos Aires y Patagonia.** Con la media caen un 14,1 % y un 18,1 %; con la mediana, un 20,3 % y un 28,3 %. No se puede afirmar que GBA sea la región que menos cae.
- Las cifras de GBA en 2020 y 2021 son las menos precisas de la serie (sección 3).
- **Los niveles entre regiones no son comparables en poder de compra.** Se usó el mismo índice de precios para todas, y el costo de vida no es igual (por ejemplo, en Patagonia). Por eso la figura compara la evolución de cada región (índice 2017 = 100) y no sus niveles. Las tendencias sí son comparables: con los índices de precios regionales cambian como máximo 0,8 puntos (limitación 10).

**Figura:** `fig05_ingreso_region` (índice 2017 = 100, un panel por región).

---

### 4.5 ¿Qué cambia al considerar también los ingresos de otras ocupaciones?

**Qué se observa**

- Sumar los ingresos de otras ocupaciones eleva el ingreso medio entre un 3,8 % (2020) y un 5,9 % (2025).
- **Las dos series se mueven juntas:** mismos años de caída, mismo mínimo en 2024 y mismo repunte en 2025. Entre antes y después de la cuarentena, el ingreso ampliado baja un 15,3 %, frente a un 15,9 % del ingreso de la ocupación principal.
- Conclusión: tener más de un trabajo no cambia la tendencia general.

**Con qué grado de certeza**

- El ingreso de otras ocupaciones puede incluir pagos atrasados o retroactivos que no se pueden separar (limitación 9). Por eso esta medida es un complemento y no reemplaza al indicador central.

**Figura:** `fig02_ingreso_ampliado`.

---

### 4.6 ¿Cómo evolucionaron el empleo y el desempleo?

**Qué se observa**

- **Antes de la cuarentena (2017–2019):** la tasa de empleo está entre el 56,9 % y el 57,4 %, y el desempleo sube del 8,7 % al 10,6 %.
- **2020 (relevamiento telefónico):** el empleo baja al 46,9 % y el desempleo sube al 13,1 %. La proporción de ocupados con ingreso cero sube al 4,5 %, frente a alrededor del 2,5 % en el resto de los años.
- **2021 (relevamiento telefónico):** el empleo vuelve al 57,7 % y el desempleo, al 9,6 %.
- **Desde 2022:** el empleo se mantiene alrededor del 61 %, por encima de los niveles anteriores a la cuarentena. El desempleo está entre el 6,2 % y el 7,9 %, por debajo.

**Con qué grado de certeza**

- Las tasas de desempleo calculadas coinciden con las oficiales del INDEC para la población de 18 años o más, con una diferencia máxima de 0,1 puntos.
- La magnitud de los cambios de 2020 y 2021 debe leerse con cautela (sección 3).
- Las tasas miden cuántas personas trabajan o buscan trabajo, no la calidad del empleo. Este proyecto no analiza la informalidad, las horas trabajadas ni el tipo de ocupación.

**Figura:** `fig06_empleo_desempleo` (dos paneles, porque las tasas tienen bases distintas).

---

### 4.7 ¿Qué se observa al resumir antes, durante y después de la cuarentena?

**Qué se observa**

| Indicador | Antes (2017–2019) | Durante (2020–2021) ▒ | Después (2022–2026) |
|---|---|---|---|
| Ingreso real medio | 1,45 millones | 1,30 millones | 1,22 millones |
| Ingreso real mediano | 1,21 millones | 1,06 millones | 0,98 millones |
| Tasa de empleo | 57,2 % | 52,3 % | 61,3 % |
| Tasa de desempleo | 9,6 % | 11,4 % | 7,2 % |
| Ocupados con ingreso cero | 2,9 % | 3,4 % | 2,4 % |

▒ Relevamiento telefónico. Cada etapa es el promedio simple de sus años.

- **Hallazgo central:** después de la cuarentena hay **más empleo y menos desempleo** que antes, pero el **ingreso real de quienes trabajan es menor**: un 15,9 % con la media y un 19,2 % con la mediana.
- En otras palabras, en 2022–2026 más personas tienen trabajo, pero ese trabajo, en promedio, compra menos que en 2017–2019.
- El ingreso no se recuperó en "después": siguió por debajo de "durante".

**Con qué grado de certeza**

- La comparación entre antes y después es la más confiable, porque ambas etapas se relevaron en persona.
- **"Después" promedia años muy distintos:** incluye el mínimo de 2024, el repunte de 2025 y el dato preliminar de 2026. El promedio no describe a ningún año en particular.
- La muestra es más chica en "después" que en "antes" (limitación 5).

**Figura:** `fig07_resumen_etapas` (barras por etapa; "durante" rayado).

---

## 5. Limitaciones

Estas limitaciones no invalidan los resultados, pero indican hasta dónde se puede llegar con ellos. El detalle técnico está en la tarjeta "Comprobaciones y limitaciones" del tablero del proyecto.

**1. Cobertura.** La EPH releva 31 aglomerados urbanos. Los resultados no describen a la población rural ni al total del país.

**2. Relevamiento telefónico en 2020 y 2021.** Ver la sección 3. Esos años sirven como contexto y no sostienen las conclusiones.

**3. Base preliminar de 2026.** El INDEC publicó el segundo trimestre de 2026 como base preliminar, que puede ser reemplazada por una definitiva. Se incluyó en el análisis y se señala en cada figura.

**4. Personas que no declaran su ingreso.** Entre el 18 % y el 25 % de los ocupados (según el año, con datos ponderados) no declara su ingreso, y la proporción crece desde 2019. Se concentra en GBA y entre quienes tienen ingresos altos. El INDEC lo compensa con un ponderador especial (PONDIIO), que supone que quienes no responden se parecen a quienes sí lo hacen dentro de cada grupo. Cuanto mayor es la no respuesta, más pesa ese supuesto.

**5. Muestra más chica después de la pandemia.** La encuesta pasa de unos 59.000 casos por año en 2017–2019 a 44.467 en 2026. Los grupos chicos, como los jóvenes, GBA o el primario incompleto, son menos precisos en la etapa "después".

**6. Ingresos declarados en números redondos.** Las personas suelen declarar valores redondos: en 2017, por ejemplo, muchos ingresos son exactamente 6.000, 10.000 o 16.000 pesos. Por eso la mediana avanza "a saltos" y a veces dos grupos tienen exactamente la misma mediana. Por esa razón se usan juntas la media y la mediana, y una variación solo se considera sólida si ambas coinciden.

**7. Ajuste por inflación.** La EPH pregunta por el ingreso del mes anterior a la entrevista, pero no informa en qué mes se hizo cada entrevista. Se usó el promedio del IPC de marzo a mayo de cada año. En años de inflación mensual alta, como 2023 y 2024, la elección del mes cambia los resultados; por eso el repunte de 2025 se informa como rango (entre +24 % y +35 %). La caída entre 2017 y 2026 casi no cambia (entre −15,9 % y −16,5 %).

**8. Sin pruebas de significación estadística.** Las bases públicas no incluyen la información necesaria para calcular márgenes de error exactos. La precisión se controló exigiendo al menos 100 casos por grupo y año; todas las combinaciones analizadas superan ese mínimo (la más chica tiene 308). Aun así, las diferencias son descriptivas: no está probado que superen el error de muestreo.

**9. Pagos retroactivos en el ingreso ampliado.** El ingreso de otras ocupaciones puede incluir pagos atrasados que no se pueden identificar. Afecta solo a la medida complementaria (sección 4.5).

**10. Mismo índice de precios para todas las regiones.** Se usó el IPC nacional. Las tendencias regionales casi no cambian con los índices regionales, pero los niveles de ingreso entre regiones no son comparables en poder de compra.

**11. Detalle del nivel educativo.** El nivel superior no se separó en terciario, universitario y posgrado. Sería posible con otras variables de la encuesta, pero requería reprocesar los datos y el posgrado tendría pocos casos. Los estudios técnicos no se pueden identificar.

**12. Grupo de 65 años o más.** Es el grupo con menos casos y con resultados no concluyentes. Describe a las personas de esa edad que trabajan, no a las personas jubiladas.

**13. Descripción, no causas.** Este proyecto describe cambios y relaciones. Ninguno de los resultados permite atribuir los cambios a la cuarentena, a la inflación o a otro factor en particular.

---

## 6. Glosario

- **Ingreso de la ocupación principal:** lo que una persona declara haber cobrado en el mes anterior por su trabajo principal. Es el indicador central del proyecto.
- **Ingreso real:** ingreso ajustado por inflación, expresado en pesos de un mismo momento (octubre de 2026), para que distintos años sean comparables.
- **Media:** el promedio. Es sensible a los valores muy altos.
- **Mediana:** el valor del medio. La mitad de las personas gana menos y la otra mitad, más.
- **Ponderador:** número que indica a cuántas personas de la población representa cada persona encuestada.
- **Tasa de empleo:** porcentaje de personas de 18 años o más que trabajan.
- **Tasa de desempleo:** porcentaje de personas que buscan trabajo y no lo consiguen, sobre el total de quienes trabajan o buscan trabajo.
- **Variación sólida (robusta):** cuando la media y la mediana coinciden en dirección y difieren en menos de 4 puntos.
- **Correlación de Spearman:** mide, de −1 a 1, qué tan ordenada es la relación entre dos variables. Un valor de 0,35 indica una relación positiva moderada.

---

## 7. Fuentes y archivos

**Fuentes**
- INDEC, Encuesta Permanente de Hogares: bases de microdatos individuales del 2.º trimestre, 2017–2026 (2026: base preliminar).
- INDEC, Índice de Precios al Consumidor nacional, base diciembre de 2016 = 100. Mes de referencia: octubre de 2026.

**Notebooks**
1. `01_preparacion.ipynb`: carga, limpieza y ajuste por inflación.
2. `02_analisis.ipynb`: indicadores, cruces, tasas y resúmenes; genera las 13 tablas de `resultados/`.
3. `03_visualizaciones.ipynb`: las 7 figuras de `resultados/`.
4. `04_interpretacion.ipynb`: este texto junto a las figuras, con el recálculo de cada cifra citada.

**Figuras** (en `resultados/`)

| Figura | Contenido | Sección |
|---|---|---|
| `fig01_ingreso_anual` | Evolución anual del ingreso real | 4.1 |
| `fig02_ingreso_ampliado` | Ingreso ampliado frente al central | 4.5 |
| `fig03_ingreso_edad` | Ingreso por grupo de edad | 4.2 |
| `fig04_ingreso_educacion` | Ingreso por nivel educativo | 4.3 |
| `fig05_ingreso_region` | Ingreso por región (índice 2017 = 100) | 4.4 |
| `fig06_empleo_desempleo` | Tasas de empleo y desempleo | 4.6 |
| `fig07_resumen_etapas` | Antes, durante y después | 4.7 |
