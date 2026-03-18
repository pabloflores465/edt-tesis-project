# Contexto para agentes

## Archivo activo

El archivo de proyecto a usar siempre es `LoRA-HDL-QA_Proyecto_2026.xml`. Los otros XML son versiones anteriores.

## Bug conocido: ProjectLibre 1.9.8 no abre el XML si tiene `<Exceptions>` en el calendario

### Qué pasa

ProjectLibre abre pero muestra la ventana en blanco. No hay mensaje de error visible al usuario.

### Por qué

La librería mpxj usada por ProjectLibre lanza `NullPointerException` al leer excepciones de calendario (feriados) que no tienen `<RecurrenceType>`. El crash ocurre antes de cargar cualquier tarea.

```
java.lang.NullPointerException: Cannot invoke "net.sf.mpxj.RecurrenceType.ordinal()"
because "net.sf.mpxj.RecurringData.getRecurrenceType()" is null
    at MSPDIReader.readException -> readCalendar -> readCalendars
```

### Fix aplicado

Se eliminó el bloque `<Exceptions>` del calendario `Guatemala 2026` en `LoRA-HDL-QA_Proyecto_2026.xml`. Los feriados ya no están marcados como no laborables, pero el proyecto carga correctamente.

### Si regeneras o modificas el XML

No agregues un bloque `<Exceptions>` al calendario sin incluir `<RecurrenceType>` en cada `<Exception>`. Incluso con `<RecurrenceType>0</RecurrenceType>` el crash puede persistir en ProjectLibre 1.9.8 — lo más seguro es omitir `<Exceptions>` por completo.
