# EDT Tesis Project — LoRA-HDL-QA

Estructura de desglose de trabajo (EDT) para el proyecto de graduación **LoRA-HDL-QA** de la Universidad del Istmo (UNIS).

## Archivos

| Archivo | Descripción |
|---|---|
| `LoRA-HDL-QA_Proyecto_2026.xml` | Versión activa del proyecto (compatible con ProjectLibre) |
| `LoRA-HDL-QA_Proyecto_v2.xml` | Versión anterior |
| `LoRA-HDL-QA_Proyecto.xml` | Versión inicial |

## Cómo abrir en ProjectLibre

1. Abrir ProjectLibre
2. **File → Open**
3. Seleccionar `LoRA-HDL-QA_Proyecto_2026.xml`

---

## Bug documentado: NullPointerException al abrir XML de MS Project en ProjectLibre 1.9.8

### Síntoma

Al intentar abrir el archivo XML (formato Microsoft Project) en ProjectLibre 1.9.8, la aplicación se abre pero muestra una ventana completamente en blanco. No se carga ninguna tarea ni estructura.

### Causa raíz

ProjectLibre usa la librería **mpxj** para parsear archivos XML de MS Project. El método `MSPDIReader.readException()` lanza un `NullPointerException` cuando una excepción de calendario (día festivo/feriado) no incluye el campo `<RecurrenceType>`.

```
java.lang.NullPointerException: Cannot invoke "net.sf.mpxj.RecurrenceType.ordinal()"
because the return value of "net.sf.mpxj.RecurringData.getRecurrenceType()" is null
    at net.sf.mpxj.mspdi.MSPDIReader.readRecurringData(Unknown Source)
    at net.sf.mpxj.mspdi.MSPDIReader.readException(Unknown Source)
    at net.sf.mpxj.mspdi.MSPDIReader.readExceptions(Unknown Source)
    at net.sf.mpxj.mspdi.MSPDIReader.readCalendar(Unknown Source)
    at net.sf.mpxj.mspdi.MSPDIReader.readCalendars(Unknown Source)
    at net.sf.mpxj.mspdi.MSPDIReader.read(Unknown Source)
    at com.projectlibre.core.pm.exchange.MspImporter.parseProject(Unknown Source)
```

Este error ocurre **antes** de que se cargue cualquier tarea, por lo que ProjectLibre muestra la ventana vacía sin ningún mensaje de error al usuario.

### Estructura que causa el problema

Las excepciones de calendario (feriados) en el XML no incluían `<RecurrenceType>`:

```xml
<Exception>
  <ExceptionUID>1</ExceptionUID>
  <Name>Año Nuevo</Name>
  <Occurring>1</Occurring>
  <DayWorking>0</DayWorking>
  <TimePeriod>
    <FromDate>2026-01-01T00:00:00</FromDate>
    <ToDate>2026-01-01T23:59:00</ToDate>
  </TimePeriod>
  <!-- ⚠️ Falta <RecurrenceType> — esto causa el NullPointerException -->
</Exception>
```

Los feriados afectados eran:

- Año Nuevo
- Lunes Santo
- Martes Santo
- Miércoles Santo
- Jueves Santo
- Viernes Santo
- Día del Trabajo
- Día del Ejército
- Día de la Independencia
- Día de la Revolución

### Solución aplicada

Se eliminó el bloque `<Exceptions>` completo del calendario `Guatemala 2026`. Los días festivos dejan de marcarse como no laborables, pero el proyecto carga correctamente con todas sus tareas y dependencias intactas.

### Solución alternativa (sin perder los feriados)

Agregar `<RecurrenceType>0</RecurrenceType>` a cada excepción del calendario antes de la etiqueta `</Exception>`:

```xml
<Exception>
  <ExceptionUID>1</ExceptionUID>
  <Name>Año Nuevo</Name>
  <Occurring>1</Occurring>
  <DayWorking>0</DayWorking>
  <TimePeriod>
    <FromDate>2026-01-01T00:00:00</FromDate>
    <ToDate>2026-01-01T23:59:00</ToDate>
  </TimePeriod>
  <RecurrenceType>0</RecurrenceType>  <!-- ✅ Fix -->
</Exception>
```

> **Nota:** En la prueba realizada, agregar `<RecurrenceType>0</RecurrenceType>` no fue suficiente para resolver el crash en ProjectLibre 1.9.8. El crash persistió porque mpxj aún intentaba leer un objeto `RecurringData` inexistente. La eliminación completa del bloque `<Exceptions>` fue la única solución efectiva.

### Entorno

| Componente | Versión |
|---|---|
| ProjectLibre | 1.9.8 |
| Java | 21.0.6 |
| macOS | Darwin 25.3.0 |
| Formato XML | Microsoft Project Schema (`http://schemas.microsoft.com/project`) |

### Referencias

- [mpxj en GitHub](https://github.com/joniles/mpxj)
- [ProjectLibre en SourceForge](https://sourceforge.net/projects/projectlibre/)
