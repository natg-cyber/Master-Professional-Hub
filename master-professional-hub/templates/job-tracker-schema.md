# Job Tracker schema reference

The populated personal workbook is deliberately excluded from this repository. Its structure was inspected to document import/export expectations. Always inspect the actual workbook version before writing; headers and dashboard formulas can change.

## Sheets and observed headers

### `Posiciones`

`ID`, `Fuente`, `Empresa`, `Rol`, `Fecha`, `Link JD`, `Score (1-10)`, `% Match`, `Keywords Faltantes`, `Red Flags (IDs)`, `Red Flags Resueltas`, `ATS Pass (Si/No)`, `Estado CV`, `Estado Cover Letter`, `Estado General`, `Resultado`

### `Prep Entrevistas`

`ID Posicion`, `Pregunta Conductual`, `Situation`, `Task`, `Action`, `Result`, `Takeaway / Tie-back`, `RF que resuelve`, `Fecha`

### `Investigacion Empresa`

`ID Posicion`, `Empresa`, `Reclutador / Hiring Manager`, `Hallazgos clave (empresa)`, `Hallazgos publicos (reclutador)`, `Fecha`

### `Networking`

`Nombre`, `Rol`, `Empresa`, `Como la conoci`, `Fecha contacto`, `Objetivo conversacion`, `Puntos de conexion (Hecho/Posible/Pregunta abierta)`, `Fecha conversacion`, `Reflexion`, `Siguiente paso`, `Estado`

### `Dashboard`

Summary sheet. Inspect formulas, labels, and layout from the current source workbook; do not reconstruct from assumptions.

## Safe import/export expectations

- Do not commit a populated personal tracker.
- Preserve sheet names, column headers, unknown columns, and unrelated data.
- Preview mapping and possible duplicates before import.
- Export to a new file; never overwrite the imported source by default.
- Use UTF-8 for CSV where supported. XLSX remains the preferred round-trip format when the chosen implementation can preserve the workbook adequately.
