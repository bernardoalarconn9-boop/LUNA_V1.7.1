# Contrato de Errores de LUNA V1.7.1

Este documento define la taxonomía oficial de errores para LUNA. Todo código nuevo debe usar estas categorías.

## 1. Taxonomía - Qué errores existen
```

Errores por Naturaleza (LUNA_V1.7.1)
├── Errores Lógicos
│   ├── Alucinación de Datos
│   └── Ruptura de Secuencia
├── Errores de Seguridad
│   ├── Fuga de Prompt
│   └── Inyección de Contexto
└── Errores de Sistema
    ├── Timeout de API
    └── Respuesta Malformada
```
## 2. Severidad - Qué tan grave es

| Nivel | Descripción | Acción |
| --- | --- | --- |
| *CRÍTICO* | Riesgo de seguridad o pérdida de datos | Detener y alertar |
| *ALTO* | Rompe funcionalidad core | Reintentar con fallback |
| *MEDIO* | Degrada experiencia | Loggear y continuar |
| *BAJO* | Cosmético | Solo loggear |

*Nota:* Esta taxonomía reemplaza cualquier versión anterior.


