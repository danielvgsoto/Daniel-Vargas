# Arquitectura de IA y costos de Trucky

Alcance actual: todos los tipos de carga y perfiles por carrier.

## Principio

Trucky opera con reglas y datos propios. El LLM es la interfaz de lenguaje y se usa por excepción.

Cada petición pasa por este embudo:
1. Reglas
2. Base de datos
3. Caché
4. Modelo barato
5. Modelo potente, solo como fallback

Metas:
- Chat de mercado: más del 85 % de las consultas sin modelo potente.
- Dashboard, notificaciones y registro de cargas: ~100 % sin LLM.
- Verificador: el modelo potente solo entra en una minoría clara de documentos.

**El prompt no es el guardián del negocio.** Toda regla de producto se aplica en dos puntos:
- una regla previa, que evita que se genere esa salida;
- un filtro posterior, que bloquea la salida si aun así aparece.

Ejemplo: la prohibición de sugerir backhaul al broker.

## Por módulo

| Módulo | Reglas / BD / caché | LLM |
|---|---|---|
| Chat de mercado | Normalizar ruta (alias), millas, costo por milla del camión del perfil activo, break-even, tarifa mínima y objetivo, veredicto, filtro de frases prohibidas, respuesta con plantilla fija | Entender input ambiguo; redactar la respuesta final |
| Calculadora | `CostConfig` por carrier y por camión, obligatoria. Estados: `missing` / `incomplete` / `valid` | No usa |
| Verificador | 1) Extracción a JSON. 2) Motor de reglas: TONU, detention, per diem, demurrage, fechas imposibles, bloqueo de void checks y documentos bancarios. 3) Semáforo por categoría. Caché por hash del documento | Solo si la confianza de la extracción < umbral o hay una cláusula ambigua |
| Dashboard / notificaciones | Consultas y reglas: vencimientos, cargas estancadas, integridad camión–conductor–carga, KPIs | No usa |
| Registro de cargas | Margen, estados, relaciones por ID (no texto libre) | Opcional: extraer una carga desde texto pegado |

Regla de personalización: si el `CostConfig` del camión no está en `valid`, el chat responde en modo genérico, con aviso visible, y ofrece un botón para configurar costos. Nunca presenta un estimado genérico como si fuera personalizado.

## Datos (entidades)

Todas las entidades llevan `carrier_id` (perfil) para aislar los datos entre compañías.

**Configuración y catálogos**
- `CostConfig`
- `RouteAlias`
- `DocumentRuleCatalog`
- `AlertRuleConfig`

**Mercado y rutas**
- `LaneCache`
- `LaneMarketStats`
- `BrokerStats`

**Documentos y cargas**
- `VerifiedDocument`
- `LoadStatusAudit`

**Uso de IA**
- `ChatSessionSummary`
- `AIUsageLog`, con estos campos:
  - módulo
  - nivel del modelo
  - motivo de la llamada
  - acierto de caché
  - tokens
  - costo estimado

## Router de modelos

- **Nivel 0 — sin LLM.** Hay datos estructurados suficientes.
- **Nivel 1 — modelo barato.** Interpretar la pregunta, extraer pocos campos, redactar.
- **Nivel 2 — modelo potente.** Documento ambiguo, conflicto de datos o consulta analítica compleja.

Base44 permite conectar varios proveedores por API key.

Modelo en producción hoy y costo por consulta: PENDIENTE confirmar con desarrollo. La referencia en las instrucciones de abril es `claude-sonnet-4-20250514`.

## Ahorro de contexto

- Una sola sesión activa por usuario y perfil, con `upsert`.
- Al modelo se le envían los últimos 4 a 6 mensajes más un resumen corto de la sesión.
- Nunca se envían tablas completas; solo los 3 a 5 datos relevantes.
- Prompt estable, para aprovechar el caché del proveedor.

## KPIs

**Costo**
- % de consultas resueltas sin LLM
- Costo por consulta, por módulo y por usuario activo
- Tasa de acierto de caché

**Calidad**
- % de veredictos correctos
- Precisión de la normalización de rutas
- % de documentos resueltos sin modelo potente
- Salidas bloqueadas por reglas
