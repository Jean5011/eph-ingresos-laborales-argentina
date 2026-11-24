# Inventario de fuentes

**Proyecto:** Ingresos laborales en Argentina (EPH, INDEC).
**Armado el:** 12/11/2026, como resultado de la Etapa 1. **Actualizado el:** 22/11/2026, con los datos verificados en la Etapa 2.
**Serie:** segundo trimestre de cada año, de 2017 a 2026. Diez observaciones.
**Fuente:** INDEC, bases de microdatos de la EPH. https://www.indec.gob.ar/Institucional/Indec/BasesDeDatos
**Formato elegido:** txt. El INDEC también publica las bases en xls.
**Base usada:** solo la individual. La de hogar no se usa (ver `registro_etapa2_inclusiones_exclusiones.md`).
**Citación obligatoria:** "Fuente: Instituto Nacional de Estadística y Censos (INDEC)."

---

## Tabla de inventario

| Año | Archivo comprimido | Tamaño | Archivo individual (dentro del zip) | Registros | Columnas | Diseño de registro | Observaciones |
|---|---|---|---|---|---|---|---|
| 2017 | EPH_usu_2_Trim_2017_txt.zip | 3,2 MB | usu_individual_t217.txt | 59.755 | 177 | No consultado | Relevamiento presencial. Comparable. |
| 2018 | EPH_usu_2_Trim_2018_txt.zip | 2,9 MB | usu_individual_t218.txt | 57.835 | 177 | No consultado | Relevamiento presencial. Comparable. |
| 2019 | EPH_usu_2_Trim_2019_txt.zip | 3,1 MB | USU_individual_t219.txt | 59.258 | 177 | No consultado | Relevamiento presencial. Comparable. |
| 2020 | EPH_usu_2_Trim_2020_txt.zip | 1,9 MB | usu_Individual_T220.txt | 37.132 | 177 | No consultado | **Relevamiento telefónico estricto.** Tasa de respuesta del 44 %: de 26.940 viviendas seleccionadas, respondieron 11.841. Quince aglomerados no alcanzaron el estándar de calidad del INDEC, entre ellos CABA y los partidos del GBA. GBA tiene 3.935 casos, contra unos 10.600 en 2017–2019. Las cifras combinan el efecto de la pandemia con el de la modalidad, y no se pueden separar. |
| 2021 | EPH_usu_2_Trim_2021_txt.zip | 2,6 MB | usu_individual_T221.txt | 47.085 | 177 | No consultado | **Relevamiento no presencial o mixto.** La modalidad alterada va del 2.º trimestre de 2020 al 1.º de 2022. **GBA tiene 3.914 casos, tan pocos como en 2020.** |
| 2022 | EPH_usu_2_Trim_2022_txt.zip | 3,1 MB | EPH_usu_2do_Trim_2022_txt/usu_individual_T222.txt.txt | 50.614 | 177 | No consultado | Vuelta al relevamiento presencial. Comparable. Los txt están dentro de una subcarpeta y el nombre termina en `.txt.txt`. |
| 2023 | EPH_usu_2_Trim_2023_txt.zip | 3,0 MB | EPH_usu_2do_Trim_2023_txt/usu_individual_T223.txt | 49.072 | 177 | No consultado | Comparable. Los txt están dentro de una subcarpeta. Las variables nuevas del 4.º trimestre de 2023 (EMPLEO, SECTOR y otras) todavía no están. |
| 2024 | EPH_usu_2_Trim_2024_txt.zip | 3,6 MB | EPH_usu_2_Trim_2024_txt/usu_individual_T224.txt | 47.151 | 235 | No consultado | Comparable en las variables del proyecto. Los txt están dentro de una subcarpeta. Pasa de 177 a 235 columnas por las variables nuevas. |
| 2025 | EPH_usu_2_Trim_2025_txt.zip | 3,5 MB | usu_individual_T225.txt | 46.086 | 235 | **Consultado**, versión de noviembre de 2025, guardado en documentacion/ | Comparable. Es el diseño de registro de referencia del proyecto. |
| 2026 | EPH_usu_2_Trim_2026_txt.zip | 2,9 MB | usu_individual_T226.txt | 44.467 | 234 | No consultado | **Base preliminar.** Puede ser reemplazada por una versión definitiva. Está incluida por ahora; la decisión sigue pendiente. Se eliminó CAT_INAC, que no afecta al proyecto. |

**Descarga:** los diez archivos se descargaron el 22/11/2026 entre las 13:03 y las 13:04 (hora de Argentina), desde `https://www.indec.gob.ar/ftp/cuadros/menusuperior/eph/` + el nombre del archivo comprimido. El detalle está en `registro_descarga_eph.csv`.

**Registros:** son personas de todas las edades en la base individual, sin filtrar. Después del filtro de 18 años o más quedan 369.946 en total.

---

## Estado de verificación

Esta sección distingue lo comprobado de lo supuesto. La distinción importa: un inventario que presenta como verificado algo que no lo está es peor que uno incompleto.

### Verificado sobre los datos (Etapa 2)

- **El nombre del archivo comprimido de cada año.** Todos siguen el patrón `EPH_usu_2_Trim_AAAA_txt.zip`. El de 2016, que no forma parte de la serie, usa otro: `EPH_usu_2doTrim_2016_txt.zip`.
- **Los nombres internos no son uniformes.** Esto corrige lo que se suponía en la Etapa 1, cuando se tomaba como nombre `usu_individual.txt`. En la práctica cambian las mayúsculas, el sufijo del trimestre y, en 2022–2024, hay una subcarpeta. Por eso la lectura busca el archivo por su contenido ("individual" + ".txt") y no por un nombre fijo.
- **Cantidad de registros, columnas y tamaño de cada archivo:** están en la tabla.
- **Las nueve variables del proyecto están en los diez años:** CODUSU, CH06, NIVEL_ED, REGION, ESTADO, P21, TOT_P12, PONDIIO y PONDERA. El detalle está en `verificacion_bases_eph.csv`.
- **PONDIIO es numérico (entero) en los diez años.** El `C(2)` del diseño de registro de 2025 es un error del PDF.
- **Las categorías son estables:** NIVEL_ED (1 a 7, sin el código 9), REGION (seis códigos), ESTADO (0 a 4) y CH06 (de −1 a 104).

### Verificado en documentación (Etapa 1)

- **Las diez bases existen** en el sitio del INDEC, sin faltantes, incluido 2020.
- **El INDEC publica las bases** individual y de hogar en txt y en xls para todos los trimestres de la serie.
- **El segundo trimestre de 2026 figura como base preliminar.**
- **Las observaciones metodológicas** de 2020 y 2021, documentadas en `notas_metodologicas_2020.md` con sus fuentes.

### No verificado

- **Los diseños de registro de 2017 a 2024.** No se consultaron. La verificación sobre los datos los vuelve menos necesarios para las variables del proyecto, pero no cubre el significado de cada código en los años intermedios.
- **El diseño de registro del segundo trimestre de 2017**, que es el inicio real de la serie, no se consiguió. Se usó el de 2016 en su lugar.
