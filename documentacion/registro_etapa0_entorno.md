# Etapa 0 – Registro de preparación del entorno

**Fechas:** 10 y 11/11/2026
**Notebook:** `01_preparacion.ipynb`, secciones 1 y 2
**Entrada:** ninguna. Es la etapa inicial del proyecto.
**Salidas:**
- Estructura de carpetas `eph_ingresos/` en Google Drive
- `notebooks/01_preparacion.ipynb`, con el montaje de Drive, las rutas del proyecto y las versiones del entorno
- Tablero de seguimiento del proyecto en Trello

**Estado:** cerrada y aprobada el 11/11/2026.

## 1. Objetivo

Dejar listo un entorno de trabajo reproducible: carpetas ordenadas en Drive, un notebook de Colab conectado a esas carpetas, rutas definidas una sola vez y versiones de las librerías registradas. Así, cualquier persona puede repetir el análisis con la misma estructura y saber con qué versiones se hizo.

## 2. Estructura de carpetas

Creada en Google Drive ("Mi unidad") el 10/11/2026:

```text
eph_ingresos/
├── datos_originales/
│   ├── eph/
│   └── ipc/
├── datos_procesados/
├── notebooks/
│   └── 01_preparacion.ipynb
└── resultados/
```

| Carpeta | Contenido |
|---|---|
| `datos_originales/eph/` | Bases de microdatos de la EPH tal como las publica el INDEC. No se modifican. |
| `datos_originales/ipc/` | Serie del IPC nacional tal como la publica el INDEC. No se modifica. |
| `datos_procesados/` | Bases limpias y transformadas que generan los notebooks. |
| `notebooks/` | Notebooks de Colab del proyecto. |
| `resultados/` | Tablas y gráficos finales. |

La carpeta `documentacion/` se agregó en la Etapa 1.

### Convención de nombres

Minúsculas, guion bajo en lugar de espacios y sin tildes, eñes ni caracteres especiales. Se usa un nombre técnico corto (`eph_ingresos`) en lugar del título del proyecto por dos motivos: simplifica las rutas en Python y evita problemas de compatibilidad entre sistemas, ya que, por ejemplo, Windows no admite los dos puntos en los nombres de archivo.

## 3. Configuración del notebook

### Montaje de Google Drive

El entorno de ejecución de Colab es una máquina temporal que no ve Drive y que borra su disco al reiniciarse. Por eso todo lo que debe conservarse se guarda en Drive, y el notebook empieza montándolo:

```python
from google.colab import drive
drive.mount('/content/drive')
```

Tras el montaje, "Mi unidad" queda disponible en `/content/drive/MyDrive/`.

### Rutas del proyecto

Las rutas se definen una sola vez, al comienzo del notebook, con `pathlib.Path`. El resto del código usa estas constantes, así que un cambio de carpeta se corrige en un solo lugar.

| Constante | Ruta |
|---|---|
| `RAIZ` | `/content/drive/MyDrive/eph_ingresos` |
| `DATOS_ORIGINALES` | `RAIZ / 'datos_originales'` |
| `DATOS_EPH` | `DATOS_ORIGINALES / 'eph'` |
| `DATOS_IPC` | `DATOS_ORIGINALES / 'ipc'` |
| `DATOS_PROCESADOS` | `RAIZ / 'datos_procesados'` |
| `RESULTADOS` | `RAIZ / 'resultados'` |

**Control:** las seis rutas se verificaron con `exists()` y todas dieron `True`. En la Etapa 1 se agregó una séptima constante, `DOCUMENTACION`.

## 4. Versiones del entorno

Registradas el 11/11/2026 con las versiones que Colab ofrece por defecto:

| Componente | Versión |
|---|---|
| Python | 3.13.18 |
| pandas | 2.2.3 |
| matplotlib | 3.10.0 |
| seaborn | 0.13.2 |

Colab actualiza sus versiones sin aviso. Por eso el notebook vuelve a mostrar las versiones en cada ejecución, y esta tabla funciona como referencia: si en el futuro aparecen errores o resultados distintos, el primer paso es comparar las versiones con estas.

## 5. Estructura base de los notebooks

Cada notebook del proyecto empieza con las mismas secciones:

1. Título y objetivo.
2. Configuración del entorno: montaje de Drive y rutas.
3. Versiones del entorno.

Después vienen las secciones propias de cada notebook. Si la sesión de Colab se reinicia, hay que volver a ejecutar las secciones 2 y 3 antes de seguir.

## 6. Seguimiento del proyecto

El avance se registra en un tablero de Trello con las listas **Referencias**, **Pendiente**, **En curso**, **En revisión** y **Hecho**. Cada etapa es una tarjeta con su checklist de tareas.

Reglas de uso:

1. Hay una sola etapa en "En curso" a la vez.
2. Cada tarea terminada se marca en el checklist y se registra con un comentario sobre lo hecho y lo aprendido.
3. Con el checklist completo, la tarjeta pasa a "En revisión". Si la revisión la aprueba, pasa a "Hecho" y la etapa siguiente pasa a "En curso".
4. Las tarjetas de "Referencias" ("Decisiones del proyecto" y "Comprobaciones y limitaciones") no se mueven: se actualizan cuando cambia una decisión o se resuelve una comprobación.

## 7. Decisiones tomadas

1. **Carpeta con nombre técnico:** `eph_ingresos`, con la convención de nombres de la sección 2.
2. **Datos originales separados de los procesados:** los archivos descargados no se modifican nunca.
3. **Notebooks creados desde Drive** (Nuevo → Más → Google Colaboratory), dentro de `notebooks/`, para que queden en la carpeta correcta desde el inicio.
4. **Rutas como constantes con `pathlib`**, definidas una sola vez por notebook.
5. **Versiones de Colab por defecto**, registradas en lugar de fijadas, con control en cada ejecución.
6. **Cada etapa se trabaja en su propio chat** de asistencia, con un documento de cierre y traspaso al terminarla.

## 8. Pendientes

Al cierre de la etapa quedaron dos detalles de formato en el notebook: faltaban los dos puntos en las etiquetas `matplotlib:` y `seaborn:` de la celda de versiones, y había una celda de código vacía al final. Los dos se resolvieron en la Etapa 1.
