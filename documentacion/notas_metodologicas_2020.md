# Notas metodológicas del relevamiento 2020–2021

**Hecho el:** 12/11/2026, Etapa 1, ítem 4 del checklist.

## Fuentes

- INDEC (noviembre de 2020), *EPH — Consideraciones metodológicas sobre el tratamiento de la información del segundo trimestre de 2020*. https://www.indec.gob.ar/ftp/cuadros/menusuperior/eph/EPH_consideraciones_metodologicas_2t20.pdf
- INDEC, *Mercado de trabajo. Tasas e indicadores socioeconómicos (EPH). Segundo trimestre de 2020*. https://www.indec.gob.ar/uploads/informesdeprensa/mercado_trabajo_eph_2trim20929E519161.pdf
- Dirección General de Estadística y Censos de Entre Ríos (2020), *Cambios metodológicos en el contexto de la pandemia por COVID-19*.
- Observatorio, Universidad Nacional de Rosario, *Manual metodológico EPH* (2026).
- Observatorio de la Deuda Social Argentina, UCA, ponencia ASET (2025) sobre subcaptación del ingreso en la EPH.

---

## 1. Qué pasó

El relevamiento del segundo trimestre de 2020 se hizo bajo el decreto 297/2020, de aislamiento social preventivo y obligatorio. El operativo pasó de entrevistas presenciales a telefónicas. Se mantuvo el esquema muestral original y la misma rotación de la muestra. No se realizaron entrevistas presenciales.

Procedimiento: a las viviendas con teléfono conocido se las contactó por esa vía; a las que no tenían teléfono registrado, los encuestadores buscaron el número a partir de la dirección. Solo donde se flexibilizó el aislamiento, y con autorización explícita, se salió a campo, únicamente para conseguir teléfonos.

## 2. Cuánta muestra se perdió

| | Viviendas |
|---|---|
| Seleccionadas | 26.940 |
| Con información de contacto | 21.950 |
| Que respondieron | 11.841 |

La tasa de respuesta cayó a alrededor del 44%, frente a los niveles habituales de la encuesta.

## 3. Aglomerados que no alcanzaron el estándar de calidad

El INDEC exige dos condiciones para difundir los datos de un aglomerado: una tasa de respuesta superior al 40% de sus viviendas, y al menos el 70% de las áreas relevadas en cada estrato.

**Quince aglomerados no cumplieron una o ambas condiciones.** Entre ellos: Ciudad Autónoma de Buenos Aires, partidos del Gran Buenos Aires, Gran La Plata y Posadas.

**Consecuencia directa para este proyecto.** La región GBA (código 01) está compuesta por CABA y los partidos del Gran Buenos Aires. Los dos aglomerados que la forman están entre los que no alcanzaron el estándar. El dato regional de GBA para el segundo trimestre de 2020 es el más débil de toda la serie. Gran La Plata pertenece a la región Pampeana y Posadas al Noreste, de modo que esas dos regiones también quedan afectadas, aunque en menor medida porque tienen más aglomerados.

## 4. Qué se hizo con los ponderadores

Se aplicaron tres ajustes además del procedimiento habitual:

1. **Panel de primer ingreso.** En los aglomerados con pocos casos en el grupo de rotación nuevo, se trabajó solo con el 75% de la muestra, el que ya tenía participación previa.
2. **Probabilidad de respuesta (propensity score).** Se estimó un modelo logit por aglomerado, con variables como nivel educativo del jefe de hogar, tamaño del hogar, régimen de tenencia, si se conocía el teléfono y cantidad de ocupados o desocupados. Los coeficientes se promediaron por quintiles.
3. **Calibración final.** Ajuste a las proyecciones de población por sexo y tramos de edad de cada aglomerado.

Los ponderadores de la base ya incorporan estas correcciones. No hay que hacer nada adicional al usarlos: el ajuste está hecho. Lo que no se corrige con ponderadores es el sesgo de modalidad, que es otra cosa.

## 5. El período afectado no es solo 2020

**Este es el hallazgo que modifica el alcance del problema.** La modalidad de relevamiento no presencial no duró un trimestre: se extendió desde el segundo trimestre de 2020 hasta el primer trimestre de 2022, alternando modalidades telefónica y mixta.

Para la serie de este proyecto, que toma el segundo trimestre de cada año:

| Año | Modalidad | Estado |
|---|---|---|
| 2017, 2018, 2019 | Presencial | Comparable |
| **2020** | **Telefónica estricta** | **Afectado, caso extremo** |
| **2021** | **No presencial o mixta** | **Afectado** |
| 2022 en adelante | Presencial | Comparable |

Son **dos de las diez observaciones**, no una. Coincide exactamente con la agrupación "Durante: 2020–2021" que ya está definida en la tarjeta "Decisiones del proyecto", lo cual respalda esa agrupación: no es arbitraria, se corresponde con un cambio operativo documentado.

## 6. Efecto sobre los ingresos

Hay evidencia externa de que el relevamiento telefónico aumentó sistemáticamente la subcaptación del ingreso en 2020. Un estudio del Observatorio de la Deuda Social de la UCA, que compara la EPH con otra encuesta de CABA, muestra que la brecha entre ambas fuentes se amplió durante el período telefónico, y que la cantidad de casos de trabajadores con ingresos en CABA cayó de 647 a 281, una caída que se mantiene hasta aproximadamente 2022.

Como el indicador central de este proyecto es un ingreso, esto importa más que para un análisis de tasas de empleo.

## 7. Advertencia sobre la interpretación

El INDEC señala que los datos del segundo trimestre de 2020 "no contaban con la calidad con la que habitualmente la EPH presenta sus resultados", y las direcciones provinciales de estadística pidieron que se publicaran con esa advertencia. Por la caída de la tasa de respuesta y la pérdida de precisión, el INDEC publicó solo una parte de los cuadros habituales.

**El punto conceptual, que es el que importa al interpretar:** las cifras del segundo trimestre de 2020 combinan un efecto real —la pandemia y el aislamiento afectaron de verdad el empleo y los ingresos— con un efecto de modalidad, producido por el cambio del operativo. **Los dos efectos no se pueden separar.** Cualquier afirmación del tipo "en 2020 los ingresos cayeron X%" atribuye al fenómeno algo que en parte es del instrumento de medición.

---

## 8. Decisión pendiente

Qué hacer con 2020 y 2021 en el análisis. Tres opciones:

1. **Incluirlos y marcarlos.** Se mantienen las diez observaciones, los dos años quedan señalados en los gráficos y en el texto, y se explica por qué. Conserva la serie completa y la agrupación por etapas ya definida.
2. **Excluirlos.** La serie queda en ocho observaciones y pierde justamente el período que el proyecto se propuso observar.
3. **Incluirlos con una advertencia reforzada en GBA**, que es la región donde la pérdida de muestra fue mayor.

**Recomendación:** la opción 1, por coherencia con el diseño del proyecto, que explícitamente quiere comparar antes, durante y después. Excluir el período "durante" vaciaría la pregunta. Pero la limitación debe quedar escrita en la tarjeta "Comprobaciones y limitaciones" y repetida en la interpretación final, no solo en la documentación técnica.

**Verificación sugerida para la Etapa 2:** contar los casos válidos de P21 por año y por región. Si 2020 y 2021 muestran una caída fuerte de casos, sobre todo en GBA, queda confirmado en los datos lo que estas notas anticipan, y eso mismo sirve como evidencia para justificar el tratamiento elegido.
