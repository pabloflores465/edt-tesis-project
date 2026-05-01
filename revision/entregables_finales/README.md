# Plan de Dirección del Proyecto — LoRA-HDL-QA

## Entregables Finales

Carpeta: `/Users/pabloflores/Documents/estructura/revision/entregables_finales/`

### Presentación Principal
- **LoRA_Plan_Direccion_Proyecto_Completo.pptx** — 55 diapositivas con todos los documentos requeridos.

### Archivos de Soporte
- **LoRA-HDL-QA_Proyecto_2026.xml** — Cronograma en ProjectLibre (150 tareas, 110 actividades nivel 4, 132 únicas)
- **LoRA_Cost_Estimates_Funding.xlsx** — Estimaciones de costos detalladas por tarea + financiamiento por mes
- **LoRA_Risk_Register_Analysis.xlsx** — Registro de 25 riesgos con análisis EMV + matriz Prob-Impacto
- **build_presentation.py** — Script Python que genera la presentación base (55 slides)
- **fix_presentation.py** — Script de ajustes: EDT tree, calendario completo, RBS simplificado, 110 tareas

### Notas de la Versión Final (v2)
- **EDT/WBS (slide 15):** Diagrama de árbol visual con 5 fases, 16 paquetes de trabajo, conectores jerárquicos
- **Calendario (slide 28):** Calendario guatemalteco completo 2026 con los 12 feriados oficiales
- **Lista de Actividades (slides 29-30):** Las 110 actividades nivel 4 del XML, sin omitir ninguna
- **RBS (slide 41):** Simplificado a MacBook Air M1 2020 (Q 6,000) + Pablo Flores (Q 80/hr) + materiales
- **Recursos (slides 36, 39, 42):** Actualizados con enfoque en el recurso único del proyecto

---

## Estructura de la Presentación (55 slides)

| # | Documento | Dominio PMBOK 8va |
|---|-----------|-------------------|
| 1 | Portada | — |
| 2 | Dominio: Gobernanza | Gobernanza |
| 3 | Acta de Constitución del Proyecto | Gobernanza |
| 4 | Registro de Supuestos | Gobernanza |
| 5 | Dominio: Interesados | Interesados |
| 6 | Registro de Interesados | Interesados |
| 7 | Plan del Involucramiento de los Interesados | Interesados |
| 8 | Plan de Gestión de las Comunicaciones | Interesados |
| 9 | Matriz de Comunicaciones | Interesados |
| 10 | Dominio: Alcance | Alcance |
| 11 | Plan de Gestión del Alcance | Alcance |
| 12 | Plan de Gestión de Requisitos | Alcance |
| 13 | Documentación de Requisitos | Alcance |
| 14 | Enunciado del Alcance del Proyecto | Alcance |
| 15 | EDT / WBS | Alcance |
| 16 | Diccionario de la EDT | Alcance |
| 17 | Matriz de Trazabilidad de Requerimientos | Alcance |
| 18 | Plan de Gestión de Cambios | Alcance |
| 19 | Solicitud de Cambio — Formato | Alcance |
| 20 | Plan de Estrategia de Adquisiciones | Alcance |
| 21 | Adquisiciones — Decisiones Make-or-Buy | Alcance |
| 22 | Adquisiciones — Criterios de Selección | Alcance |
| 23 | Dominio: Cronograma | Cronograma |
| 24 | Plan de Gestión del Cronograma | Cronograma |
| 25 | Línea Base del Cronograma | Cronograma |
| 26 | Cronograma del Proyecto | Cronograma |
| 27 | Datos del Cronograma | Cronograma |
| 28 | Calendarios del Proyecto (completo Guatemala 2026) | Cronograma |
| 29 | Lista de Actividades (1/2 — 110 tareas nivel 4) | Cronograma |
| 30 | Lista de Actividades (2/2 — continuación) | Cronograma |
| 31 | Atributos de la Actividad | Cronograma |
| 32 | Base de Estimaciones + Estimaciones de Duración | Cronograma |
| 33 | Lista de Hitos | Cronograma |
| 34 | Diagramas de Red del Cronograma | Cronograma |
| 35 | Dominio: Recursos | Recursos |
| 36 | Plan de Gestión de Recursos | Recursos |
| 37 | Carta del Equipo | Recursos |
| 38 | Matriz RACI | Recursos |
| 39 | Requisitos de Recursos | Recursos |
| 40 | Base de las Estimaciones — Recursos | Recursos |
| 41 | Estructura de Desglose de Recursos — solo MacBook M1 + Q80/hr | Recursos |
| 42 | Calendarios de Recursos | Recursos |
| 43 | Dominio: Costos / Finanzas | Costos |
| 44 | Plan de Gestión Financiera | Costos |
| 45 | Estimaciones de Costos | Costos |
| 46 | Base de las Estimaciones — Costos | Costos |
| 47 | Línea Base de Costos | Costos |
| 48 | Requisitos de Financiamiento del Proyecto | Costos |
| 49 | Estrategia de Financiamiento | Costos |
| 50 | Dominio: Riesgos | Riesgos |
| 51 | Plan de Gestión de Riesgos | Riesgos |
| 52 | Registro de Riesgos | Riesgos |
| 53 | Reporte de Riesgos | Riesgos |
| 54 | Registro de Lecciones Aprendidas | Riesgos |
| 55 | Cierre | — |

---

## Datos Clave del Proyecto

| Indicador | Valor |
|-----------|-------|
| Duración total | 225 días calendario (Feb 02 → Sep 14, 2026) |
| Horas planificadas | 1,287h (nivel 4 EDT) |
| BAC (Budget at Completion) | Q 116,640.00 |
| Reserva de Contingencia | Q 20,846.00 (25 riesgos, EMV) |
| Presupuesto Total | Q 138,186.00 |
| Tareas en cronograma | 150 (110 nivel 4 + 40 resumen/hitos) |
| Riesgos identificados | 25 |

---

## Paleta de Colores

- Navy oscuro: `#1A2744` — fondos de header y dominio
- Azul acento: `#4285F4` — barras decorativas, detalles
- Azul medio: `#4285C8` — encabezados de tabla
- Azul claro: `#C8DCF0` — elementos secundarios
- Gris claro: `#F8F9FA` — tarjetas de contenido
- Blanco: `#FFFFFF` — texto sobre fondos oscuros
- Texto oscuro: `#1A2744` — sobre fondos claros

---

*Generado: 30 de abril de 2026*
*Script: build_presentation.py (reproducible)*
