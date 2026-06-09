# ERROR_CONTRACT.md
## Contrato de Errores de LUNA v1.7.3

Este documento define el comportamiento esperado ante fallos de almacenamiento.
**Refleja la implementación actual.** Todo código nuevo debe respetarlo.

### 1. Taxonomía - Qué errores existen

```
StorageError
├── DatabaseCorruptError

│   ├── DB_CORRUPTA_JSON

│   └── DB_CORRUPTA_ESQUEMA

└── DatabaseMissingError

    └── DB_INEXISTENTE
```
**Nota:** `BaseLunaError` es una abstracción planificada para V2.0. No existe en v1.7.3.

