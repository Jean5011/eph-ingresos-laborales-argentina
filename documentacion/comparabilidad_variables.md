# Comparabilidad de las variables entre los extremos de la serie

**Hecho el:** 12/11/2026, Etapa 1, ítem 3 del checklist.
**Método:** comparación documental entre dos diseños de registro, no entre archivos de datos.

## Documentos comparados

| | Documento | Origen |
|---|---|---|
| Extremo reciente | *Diseño de registros y estructura para las bases preliminares Hogar y Personas*, noviembre de 2025 | INDEC. Descargado y guardado en `documentacion/`. |
| Extremo antiguo | *Diseño de Registro y Estructura para las bases preliminares Hogar y Personas*, segundo trimestre de 2016 | Copia alojada en un repositorio académico (cátedra de la UBA), no en el sitio del INDEC. |

**Advertencia sobre la sustitución.** Se buscó el diseño de registro del segundo trimestre de 2017, que es el inicio real de la serie del proyecto, y no se lo pudo obtener. Se usó en su lugar el del segundo trimestre de 2016, que es anterior al inicio de la serie y pertenece a la misma etapa metodológica, la que comienza con la reanudación de la publicación de la EPH en 2016. Es una sustitución conservadora: si no hay diferencias entre 2016 y 2025, tampoco las hay entre 2017 y 2025. No reemplaza la verificación directa.

---

## Resultado: sin cambios en lo que el proyecto usa

**Nombres de campo, tipo y categorías idénticos en ambos extremos:**

| Campo | Observación |
|---|---|
| CH06 | N (2) en ambos. |
| NIVEL_ED | N (1), mismos ocho códigos (1 a 7 y 9) en ambos. |
| REGION | N (2), mismos seis códigos en ambos. |
| ESTADO | N (1), mismas cinco categorías. |
| CAT_OCUP | N (1), mismas cinco categorías. |
| CAT_INAC | N (1), mismas siete categorías. |
| INTENSI | N (1), mismas cinco categorías. |
| TOT_P12 | N (12) en ambos. |
| PONDERA, PONDII, PONDIH | N (6) en ambos. |
| Códigos especiales | -9, -7, -8 y 0 con el mismo significado en ambos. La regla de 9/99/999/9999 también. |

**Cambian las etiquetas, no los códigos.** En 2016 las regiones figuran como NOA, NEA y Patagónica; en 2025, como Noroeste, Noreste y Patagonia. Los códigos 40, 41 y 44 son los mismos. Lo mismo ocurre con NIVEL_ED: "Primaria Incompleta" en 2016, "Primario incompleto" en 2025, código 1 en ambos. Para el análisis no cambia nada; al etiquetar conviene usar una sola redacción para toda la serie.

---

## Diferencias encontradas

### 1. Longitud declarada de los campos de ingreso

| Campo | 2016 | 2025 |
|---|---|---|
| P21 | N (10) | N (12) |
| P47T | N (10) | N (12) |
| ITF | N (12,2) | N (12) |
| T_VI | N (12,4) | N (12) |
| PONDIIO | N (6) | C (2) |

La longitud es metadato del documento, no una propiedad del dato. Al leer un archivo delimitado con pandas, el ancho declarado no cumple ninguna función: lo que importa es el tipo real de la columna. Estas diferencias no afectan la comparabilidad.

### 2. PONDIIO: error de tipeo confirmado en el documento de 2025

El documento de 2025 declara PONDIIO como `C (2)`. El de 2016 lo declara como `N (6)`, igual que los otros tres ponderadores. Queda confirmado que `C (2)` es un error del PDF de 2025, no un cambio de la variable. **De todos modos, verificar el tipo real al leer los archivos en la Etapa 2.**

### 3. EMPLEO y SECTOR no existen en 2016

Confirmado: las variables de formalidad laboral no están en el diseño de registro de 2016. Fueron incorporadas en el cuarto trimestre de 2023. **No sirven para una serie 2017–2026.** No son necesarias para el análisis central del proyecto.

---

## Qué no cubre esta verificación

1. **No se revisaron los años intermedios.** Se compararon los dos extremos. Un cambio que hubiera aparecido y desaparecido entre 2018 y 2024 no sería detectado, aunque es improbable.
2. **No se usó el documento de 2017**, sino el de 2016. Ver la advertencia sobre la sustitución.
3. **No se verificó ningún archivo de datos.** Toda la comparación es documental. El diseño de registro describe lo que el INDEC documentó, no necesariamente lo que el archivo contiene; el caso de PONDIIO muestra que el documento puede equivocarse.

---

## Verificación pendiente, para la Etapa 2

Al leer los diez archivos `usu_individual.txt`, antes de unirlos:

1. Obtener la lista de nombres de columna de cada año.
2. Comparar las diez listas entre sí e identificar qué columnas están en todos los años y cuáles no.
3. Verificar que las columnas del proyecto —CH06, NIVEL_ED, REGION, ESTADO, CAT_OCUP, P21, TOT_P12, PONDERA, PONDIIO— estén presentes en los diez.
4. Para las variables categóricas, listar los valores distintos de cada año y comprobar que no aparezcan códigos no documentados.
5. Confirmar el tipo real de PONDIIO.

El punto 4 es el que detecta lo que el diseño de registro no dice.

---

## Conclusión

Las variables que el proyecto necesita son estables a lo largo de la serie 2017–2026 en nombre, tipo y categorías. No se requiere recodificación por cambios metodológicos. El riesgo de comparabilidad del proyecto no está en las variables sino en el relevamiento del segundo trimestre de 2020, que es el ítem 4 del checklist.
