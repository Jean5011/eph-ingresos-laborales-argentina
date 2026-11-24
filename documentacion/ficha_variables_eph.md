# Ficha de variables de la EPH

**Fuente:** INDEC, *Diseño de registros y estructura para las bases preliminares Hogar y Personas*, noviembre de 2025.
**Armada el:** 12/11/2026, en la Etapa 1 del proyecto.
**Base de referencia:** Personas (`usu_individual.txt`), salvo donde se indique Hogar (`usu_hogar.txt`).

Tipo de campo: N = numérico, C = carácter. El número entre paréntesis es la longitud.

---

## 1. Identificación y enlace entre bases

| Campo | Tipo | Qué mide | Categorías |
|---|---|---|---|
| CODUSU | C (29) | Identifica la vivienda. Permite seguirla a lo largo de los trimestres en que participa. | — |
| NRO_HOGAR | N (2) | Identifica el hogar dentro de la vivienda. | 51 = servicio doméstico en hogares; 71 = pensionistas en hogares |
| COMPONENTE | N (2) | Número de orden de cada persona dentro del hogar. | 51 y 71, mismos casos especiales |
| ANO4 | N (4) | Año de relevamiento. | — |
| TRIMESTRE | N (1) | Trimestre de relevamiento. | 1, 2, 3, 4 |
| H15 | N (1) | Si se realizó la entrevista individual. | 1 = sí; 2 = no |

**Clave de unión Personas–Hogar:** CODUSU + NRO_HOGAR.
**Clave de una persona:** CODUSU + NRO_HOGAR + COMPONENTE.

---

## 2. Región

| Campo | Tipo | Qué mide | Categorías |
|---|---|---|---|
| REGION | N (2) | Región estadística. | 01 = Gran Buenos Aires; 40 = Noroeste; 41 = Noreste; 42 = Cuyo; 43 = Pampeana; 44 = Patagonia |
| AGLOMERADO | N (2) | Aglomerado urbano. | 32 códigos, de 02 (Gran La Plata) a 93 (Viedma–Carmen de Patagones) |
| MAS_500 | C (1) | Tamaño del aglomerado. | N = menos de 500.000 habitantes; S = 500.000 y más |

Los seis códigos de REGION coinciden exactamente con las seis regiones definidas en la tarjeta "Decisiones del proyecto". No hace falta recodificar, solo etiquetar.

---

## 3. Edad

| Campo | Tipo | Qué mide | Categorías |
|---|---|---|---|
| CH06 | N (2) | Años cumplidos. | — |
| CH05 | date | Fecha de nacimiento (día, mes, año). | — |

CH06 es la variable a usar. Los grupos del proyecto (18–29 / 30–39 / 40–64 / 65 y más) se construyen a partir de ella.

---

## 4. Nivel educativo

| Campo | Tipo | Qué mide | Categorías |
|---|---|---|---|
| NIVEL_ED | N (1) | Nivel educativo alcanzado. Variable construida por el INDEC. | 1 = primario incompleto (incluye educación especial); 2 = primario completo; 3 = secundario incompleto; 4 = secundario completo; 5 = superior y universitario incompleto; 6 = superior y universitario completo; 7 = sin instrucción; 9 = Ns/Nr |
| CH10 | N (1) | Si asiste o asistió a un establecimiento educativo. | 1 = sí, asiste; 2 = no asiste, pero asistió; 3 = nunca asistió |
| CH12 | N (2) | Nivel más alto que cursa o cursó. | 1 = jardín/preescolar; 2 = primario; 3 = EGB; 4 = secundario; 5 = polimodal; 6 = terciario; 7 = universitario; 8 = posgrado universitario; 9 = educación especial |
| CH13 | N (1) | Si finalizó ese nivel. | 1 = sí; 2 = no; 9 = Ns/Nr |
| CH14 | N (2) | Último año aprobado. | 00 = ninguno; 01 a 09 = primero a noveno; 98 = educación especial; 99 = Ns/Nr |

**Diferencia entre las dos familias.** NIVEL_ED es una variable ya construida: resume en seis categorías lo que CH12 y CH13 registran por separado (qué nivel cursó y si lo terminó). Las seis categorías de NIVEL_ED corresponden a las tres etapas con completa e incompleta que define el proyecto. CH12 y CH13 permiten reconstruir el nivel con otro criterio, si hiciera falta justificar una agrupación distinta.

**Nota sobre EGB y polimodal (CH12 = 3 y 5):** son denominaciones de un sistema educativo anterior. Siguen apareciendo en las bases. NIVEL_ED ya las absorbe en las categorías de primario y secundario, lo cual es un motivo más para usarla.

---

## 5. Situación laboral

| Campo | Tipo | Qué mide | Categorías |
|---|---|---|---|
| ESTADO | N (1) | Condición de actividad. | 0 = entrevista individual no realizada; 1 = ocupado; 2 = desocupado; 3 = inactivo; 4 = menor de 10 años |
| CAT_OCUP | N (1) | Categoría ocupacional. Para ocupados y desocupados con ocupación anterior. | 1 = patrón; 2 = cuenta propia; 3 = obrero o empleado; 4 = trabajador familiar sin remuneración; 9 = Ns/Nr |
| CAT_INAC | N (1) | Categoría de inactividad. | 1 = jubilado/pensionado; 2 = rentista; 3 = estudiante; 4 = ama de casa; 5 = menor de 6 años; 6 = discapacitado; 7 = otros |
| INTENSI | N (1) | Intensidad de la ocupación. | 1 = subocupado por insuficiencia horaria; 2 = ocupado pleno; 3 = sobreocupado; 4 = ocupado que no trabajó en la semana; 9 = Ns/Nr |
| PP3E_TOT | N (5) | Horas trabajadas en la semana en la ocupación principal. | — |
| PP3F_TOT | N (5) | Horas trabajadas en la semana en otras ocupaciones. | — |
| EMPLEO | N (1) | Formalidad del empleo. Incorporada desde el 4.º trimestre de 2023. | 1 = formal; 2 = informal; 9 = Ns/Nr |
| SECTOR | N (1) | Formalidad del sector. Incorporada desde el 4.º trimestre de 2023. | 1 = formal; 2 = informal; 3 = hogares; 9 = Ns/Nr |
| IMPUTA | N (1) | Marca los casos cuyos valores fueron imputados. | — |
| CH04 | N (1) | Sexo. | 1 = varón; 2 = mujer |

ESTADO es la variable con la que se construyen las tasas de empleo y desempleo que el proyecto usa como contexto.

**Advertencia:** EMPLEO y SECTOR no existen antes del 4.º trimestre de 2023. No sirven para la serie 2017–2026.

---

## 6. Ingresos

### 6.1 Variables agregadas (las que importan)

| Campo | Tipo | Qué mide |
|---|---|---|
| P21 | N (12) | Ingreso de la ocupación principal. Agrega el total de ingresos habituales de esa ocupación. |
| TOT_P12 | N (12) | Ingreso de otras ocupaciones: ocupación secundaria, ocupación previa a la semana de referencia, retroactivos por ocupaciones anteriores. |
| P47T | N (12) | Ingreso total individual. Suma de ingresos laborales **y no laborales**. |
| T_VI | N (12) | Total de ingresos no laborales. |
| ITF | N (12) | Ingreso total familiar. Suma de los ingresos individuales totales de todos los miembros del hogar. |
| IPCF | N (12,2) | Ingreso per cápita familiar. ITF dividido por la cantidad de miembros del hogar. |

**Correspondencia con el proyecto:**
- Indicador central (ingreso de la ocupación principal) → **P21**
- Complemento (ingresos laborales ampliados) → **P21 + TOT_P12**
- **P47T no es ingreso laboral.** Incluye jubilaciones, pensiones, AUH, alquileres, becas y rentas. Usarlo como si fuera ingreso del trabajo es el error que la tarjeta de la Etapa 3 marca como riesgo.

### 6.2 Componentes (no se usan directamente, pero conviene conocerlos)

Asalariados: PP08D1 (sueldos, salario familiar, horas extras, bonificaciones habituales, tickets), PP08D4 (tickets), PP08F1 (comisiones), PP08F2 (propinas), PP08J1 (aguinaldo), PP08J2 (bonificaciones no habituales), PP08J3 (retroactivo).

Independientes: PP06C (patrones y cuenta propia sin socios), PP06D (con socios).

No laborales: la familia V*_M (jubilaciones, pensiones, indemnización, seguro de desempleo, AUH, planes, alquileres, becas, etc.), que suman T_VI.

### 6.3 Escalas decílicas

Para cada variable de ingreso hay seis deciles, según el universo de comparación: total EPH, aglomerado, región, interior, aglomerados de 500.000 y más, y de menos de 500.000. Ejemplo para P21: DECOCUR, ADECOCUR, RDECOCUR, IDECOCUR, GDECOCUR, PDECOCUR.

Categorías: 00 = sin ingresos; 1 a 10 = decil; 12 = no respuesta de ingresos; 13 = entrevista individual no realizada.

---

## 7. Ponderadores

| Campo | Tipo | Para qué se usa |
|---|---|---|
| PONDERA | N (6) | Población y todas las variables que no son de ingreso. Sin corrección por no respuesta. |
| PONDIIO | C (2) | Ingreso de la ocupación principal: P21, PP06C, PP06D, PP08D1, PP08D4, PP08F1, PP08F2 y los deciles DECOCUR y familia. |
| PONDII | N (6) | Ingreso total individual: P47T y los deciles DECINDR y familia. |
| PONDIH | N (6) | Ingreso total familiar y per cápita familiar: ITF, IPCF y sus deciles. |

**Regla.** PONDERA no corrige la no respuesta de ingresos; los otros tres sí. Para cualquier estimación de ingreso corresponde el ponderador de esa variable. Para el proyecto, el ponderador del indicador central es **PONDIIO**.

**Inconsistencia del documento.** PONDIIO figura como C (2) y PONDIH aparece como C (6) en la base Hogar y N (6) en la base Personas. Un ponderador de dos caracteres no es posible. Es un error de tipeo del PDF, pero conviene verificar los tipos reales al leer los archivos en la Etapa 2 y no confiar en la longitud declarada.

---

## 8. Códigos especiales (leer antes de calcular cualquier promedio)

| Código | Significado | Dónde |
|---|---|---|
| 9, 99, 999, 9999 | No sabe / No responde | Variables categóricas, salvo indicación contraria |
| **-9** | **No respuesta** | **Montos de ingreso** |
| -7 | No tenía esa ocupación en el mes de referencia | PP06C y PP06D |
| -8 | No tuvo ingresos en el mes de referencia | PP06C y PP06D |
| 0 | No corresponde la secuencia analizada | General |

**Este es el punto de mayor riesgo de la Etapa 3.** En los montos de ingreso, la no respuesta se codifica como **-9**, no como vacío ni como 9. Si -9 entra en un promedio, el resultado queda arrastrado hacia abajo por un valor que no es un ingreso sino una marca de ausencia. Un ingreso faltante no es cero, y un -9 tampoco.

---

## 9. Decisiones abiertas para el proyecto

1. **NIVEL_ED = 7 (sin instrucción) y 9 (Ns/Nr).** La tarjeta "Decisiones del proyecto" ya señala que falta definirlo. Opciones: dejar "sin instrucción" como categoría propia, agruparla con primario incompleto, o excluirla. Los Ns/Nr se tratan aparte.
2. **Tratamiento de -9 en P21.** Excluir esos casos del cálculo, que es lo que el ponderador PONDIIO ya asume, o imputar. El INDEC construye PONDIIO precisamente para que la exclusión no sesgue.
3. **Ponderador del ingreso laboral ampliado (P21 + TOT_P12).** El INDEC no publica un ponderador para esa suma. PONDIIO cubre P21; PONDII cubre P47T, que incluye ingresos no laborales. Hay que decidir y documentar cuál se usa y por qué. Es una limitación a registrar en la tarjeta "Comprobaciones y limitaciones".
4. **Cambio metodológico del 4.º trimestre de 2023.** Se incorporaron variables nuevas (informalidad, estrategias del hogar, ingresos no laborales desagregados). Ninguna es necesaria para el análisis central, pero hay que verificar en la Etapa 2 que las variables que sí se usan no hayan cambiado de nombre ni de categorías a lo largo de la serie.
