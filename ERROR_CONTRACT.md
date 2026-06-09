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

| Nivel | Descripción | Acción Inmediata | Principio E.A.O. que protege |
| --- | --- | --- | --- |
| *CRÍTICO* | Fuga de Prompt, Inyección de Contexto, Violación de contrato explícito | 1. Bloquear salida. 2. Activar Freno de Mano. 3. Log + Alerta a Bernardo. 4. No reintentar sin revisión humana. | 5. La autonomía requiere responsabilidad y límites explícitos. 3. Toda decisión importante debe poder auditarse. |
| *ALTO* | Alucinación de Datos, Ruptura de Secuencia en tarea crítica | 1. Marcar respuesta como "No Verificada". 2. No ejecutar acciones. 3. Pedir confirmación al usuario. 4. Registrar en trazabilidad. | 1. La tecnología es un medio, no un fin. 7. La utilidad para las personas tiene prioridad sobre la complejidad. |
| *MEDIO* | Timeout de API, Error de Sistema recuperable, Respuesta incompleta | 1. Reintentar 1 vez con backoff. 2. Si falla, usar modo degradado/memoria cache. 3. Informar al usuario sin tecnicismos. | 2. La complejidad debe justificarse por utilidad real. 4. La memoria es un activo estratégico. |
| *BAJO* | Respuesta Malformada, Error de formato, Typo en output no crítico | 1. Auto-corregir si es posible. 2. Si no, pedir al usuario reformular. 3. Log para mejora continua. | 8. La evolución debe preservar principios. 6. La sostenibilidad permite la continuidad. |

### Reglas de Escalamiento:
1. *2 errores MEDIOS seguidos* = escalar a ALTO.
2. *1 error ALTO* = activar Freno de Mano preventivo en esa sesión.
3. *1 error CRÍTICO* = suspensión de capacidades autónomas hasta revisión de Bernardo.
4. *Todo error queda en el log de trazabilidad.* Sin excepciones. Principio 3.
