# Trucky: estado actual (fuente única)

Vigente desde: 29-sep-2026.
Este documento reemplaza cualquier dato anterior que lo contradiga.
Regla: un dato sin fuente se marca PENDIENTE. No se estima ni se inventa.
Cuándo se actualiza: con cada decisión. Se cambia la fecha de arriba y la línea afectada; no se crean notas nuevas por reunión.

---

## 1. Qué es Trucky

- TMS con IA para dispatchers que manejan varias flotas pequeñas en EE. UU.
- Núcleo:
  - verificador de rate confirmations;
  - chat de mercado, con tarifa y veredicto;
  - calculadora de costo por milla por camión.
- Soporte: registro de cargas, dashboard y notificaciones.
- Construido en Base44. App ID: `69e8214a181314e517a283d5`.
- Mensaje central: Trucky potencia al dispatcher, no lo reemplaza.

Ya no vigente:
- producto solo de drayage en Florida;
- "reemplaza al dispatcher humano por una fracción del costo";
- "no somos un bot" como diferenciador (Numeo usa el mismo lenguaje);
- Larcofer como piloto.

## 2. Cliente

| | Definición | Estado |
|---|---|---|
| Segmento 1 | Dispatcher independiente o agencia pequeña que maneja flotas de 2 a 10 camiones, dueños mayormente hispanohablantes | Prioridad actual |
| Segmento 2 | Dueño hispanohablante con autoridad activa y 2 a 10 camiones | Después de validar el 1 |
| Fuera | 11+ camiones, autoridad inactiva, no carriers. Flotas de 1 camión solo reciben contenido | — |

**Por qué el dispatcher va primero (decisión del 29-sep-2026):**
- Es el único perfil que expresó disposición de pago (~USD 30/mes). Ningún carrier contactado dijo que pagaría.
- Da acceso a pilotos por referidos dentro de su comunidad, sin llamadas en frío.
- Los módulos actuales resuelven problemas del dispatcher. Los problemas del carrier son otros:
  - gestión de cargas para impuestos;
  - respuesta automática de correos;
  - saber cuánto paga el shipper.
- El error anterior fue construir para dos públicos a la vez sin priorizar ninguno.

Datos del mercado:
- Mercado geográfico prioritario: Texas, con 21.356 carriers activos con MC y 2 a 10 camiones.
- Evidencia del segmento 1: una entrevista a fondo (n=1). Todo lo demás sobre el dispatcher es hipótesis.
- Tamaño del segmento 1: PENDIENTE.
- Target persona del segmento 1 (Jose, agencia + academia + TMS propio) y matiz de antigüedad dentro del segmento (dispatcher junior vs. establecido): `mercado/mercado-objetivo.md`. No cambia la prioridad ni el razonamiento de arriba.

Detalle: `mercado/mercado-objetivo.md` y `mercado/evidencia-entrevistas.md`.

## 3. Producto: prioridades

1. **Perfiles / compañías.** Selector para cambiar entre carriers, como el de idioma. Al cambiar se actualizan calculadora, chat, flota, conductores y brokers. Jerarquía: carrier → camiones → conductores. En Jira el ticket existía solo para la calculadora y en fase final; sube a prioridad 1.
2. **Chat y módulos interconectados.** El chat usa el costo por milla del camión del perfil activo.
3. **Verificador de rate con.** Posible módulo estrella: es lo que cambia la conversación en las demos. Se podría ampliar a invoices, BOL e impuestos sin volver Trucky solo un gestor documental. Lo decide el uso en el piloto; el chat no se quita.

Otras reglas de producto:
- Bajan de prioridad: integraciones con DAT, Truckstop y Motive. Deberán poder activarse y desactivarse.
- Excluido hasta resolver el aislamiento de datos entre cuentas y tener pruebas automáticas: OAuth con Gmail.
- Riesgos técnicos del informe de julio (fuga de datos entre cuentas, cero pruebas automáticas, fórmulas de rentabilidad contradictorias, reglas de precio en el prompt): estado PENDIENTE de confirmar con desarrollo.
- Fecha de beta: 10-oct-2026 (plan del 23-sep). PENDIENTE confirmar con perfiles como prioridad 1.

Arquitectura y costos de IA: `producto/arquitectura-ia.md`.

## 4. Precio (hipótesis, sin validar)

| Opción | Estructura | Origen |
|---|---|---|
| A | USD 30 / 25 / 20 por camión al mes, escalonado, primer mes gratis | Definición interna previa |
| B | ~USD 30 al mes plano por usuario | Ancla de un dispatcher, que hoy paga USD 24/mes por su herramienta |

- Descartado: porcentaje del gross.
- Con 5 camiones por dispatcher, A deja ~USD 125 al mes y B deja USD 30.
- Se decide con el piloto; no se presentan ambas como si fueran equivalentes.

## 5. Validación

**Piloto:**
- 3 dispatchers de la comunidad del dispatcher referente, 1 mes gratis.
- Arranca cuando existan los perfiles.
- Mide días de uso por semana, módulo más usado (chat o verificador) y disposición de pago al cierre.
- Si funciona, se empieza a vender. Si no, quedan cambios concretos para desarrollo.
- Criterio de éxito: PENDIENTE.

**Método:**
- Llamadas de descubrimiento con referentes y conocidos del nicho.
- Llamadas en frío pausadas como método de validación.

**HubSpot:** registrar "camiones operando" separado de "camiones registrados".

Cifras de referencia (1-ago → 27-sep-2026):

| Indicador | Valor |
|---|---|
| Llamadas | 682 |
| Contactos con conversación > 30 s | 139 |
| Contactos con interés real | 9 |
| Reuniones | 7 (entre 19-ago y 2-sep) |
| Deals | 0 |
| Clientes que pagan | 0 |
| Base HubSpot | 4.893 contactos (5.280 y 5.297 ya no se usan) |
| Conexión por llamada | español 17,9 % · inglés 7,5 % |

### Hipótesis evaluadas con los datos de llamadas

| Hipótesis | Veredicto |
|---|---|
| "Llamamos a conductores empleados" | No se sostiene: eran dueños de 1 camión, muchos saliendo del mercado |
| "1–10 camiones, <2 años" | Se ajusta a 2–10 camiones; la antigüedad no se usa como filtro |
| "El dispatcher decide" | Se sostiene, con muestra pequeña |
| "El problema es la lista" | Se ajusta: fallaron la lista y el seguimiento después del sí |
| "El español es la ventaja" | Se sostiene con reserva: está mezclado con el idioma de quien llama |
| "El mercado sube por quiebras" | PENDIENTE (DAT Freight Analytics) |
| "Piloto en Georgia" | Sin base: 176 contactos en Georgia |

### Referencia HubSpot (para análisis)

Resultados de llamada:

| ID | Resultado |
|---|---|
| f240bbac | Connected |
| 2e7360c1 | Meeting booked |
| 73a0d17f | No answer |
| 9d9162e7 | Busy |
| b2cf5968 | Left voicemail |
| 17b47fee | Wrong number |
| a4c4c377 | Left live message |

- Owners: 166295956 = Juan Grau · 80598234 = Daniel Vargas.
- Propiedades de contacto: `tamano_de_flota`, `idioma`, `tipo_de_equipo`, `estado_lead`.

### Compromisos de abril no cumplidos

| Compromiso | Estado hoy |
|---|---|
| Primer cliente de Trucky pagando entre julio y octubre de 2026 | 0 clientes |
| Validar precio con 5 dispatchers antes del 30-abr | 1 entrevista a fondo |
| Retorno del 70–130 % de la inversión en 36 meses, apoyado en Larcofer | Larcofer detenida |

## 6. Canal y competencia

**Canal:**
- Comunidades y academias de dispatchers, por referidos.
- Propuesta sin aprobar: cuenta de TikTok con un curso de "cómo ser dispatcher en Latinoamérica" que enseña a usar Trucky y a conseguir carriers. Se produciría con los créditos de video existentes.
- Decisión del 23-sep-2026 (reunión interna): priorizar contenido orgánico sobre pago y construir una landing page para convertir el tráfico. Base: Instagram +110 % en vistas y Facebook +31 % en alcance (ventana de 28 días); 2 leads orgánicos, ambos dispatchers, preguntaron "qué es Trucky" y no preguntaron precio (n=2, no es evidencia de disposición de pago).

**Competencia:**
- **Numeo:** su IA busca y agenda cargas, y la comunidad lo percibe como un reemplazo del dispatcher. La IA solo está en planes de 10+ camiones y no cubre drayage. El dato "91,5 % de carriers ≤10 camiones" está PENDIENTE de verificar.
- **LoadHunter:** promete verificador sin mostrarlo funcionando. Contactó al dispatcher referente, quien ve a Trucky más completo.
- **Plataforma de Tyler:** drayage y drivers, profit por carga, asistente de mercado y agente "Ruby" que organiza documentos.
- **TMS propios de academias:** el dispatcher referente construye el suyo. Es canal y competidor a la vez.
- Mencionado en reunión interna del 23-sep-2026, sin verificar: "Anumeo" (posible error de transcripción de "otro Numeo"; no confirmar como competidor real hasta verificar el nombre) y una plataforma con ~5.000 dispatches, promovida por un influencer llamado Bobby ("Load Hunters"). No está claro si esta última es LoadHunter (mismo competidor, dato nuevo de que la promueve un influencer) o un competidor adicional. PENDIENTE resolver con el equipo comercial.

## 7. Equipo

| Rol | Persona |
|---|---|
| Product Owner: estrategia, dirige por objetivos con fecha | Daniel Vargas |
| Comercial y estrategia; valida tickets | Juan Grau |
| Desarrollo (Jira) | Luis Bermúdez |
| Marketing y redes | Gonzalo Kaihara |
| Fechas, permisos, infraestructura | Olenka Sandoval |
| Contenido | Cristian Vargas (Comunicaciones) |
| Socios | Alexander Vargas, Manuel Vargas |

- Cadencia: el equipo entrega el viernes y el PO reporta a gerencia el lunes.
- Programa externo: Launch Lab, The Idea Center (MDC), con Trucky como venture.

## 8. Larcofer

- Es otro negocio, detenido y en estudio de mercado. Informe previsto ~7-oct-2026.
- No es piloto ni fuente de datos de Trucky. No se mezcla en este proyecto.

## 9. Próximas fechas

| Fecha | Hito | Responsable |
|---|---|---|
| 30-sep, mañana | Repriorizar Jira: perfiles arriba, APIs DAT abajo | Comercial |
| 30-sep, 3:00 pm Miami | Reunión con referente carrier y su esposa | PO |
| 30-sep | Registrar esa reunión en `mercado/evidencia-entrevistas.md` | PO |
| 30-sep | Presentación a socios: dispatcher primero | PO + Comercial |
| ~7-oct | Informe Larcofer (fuera de este proyecto) | — |
| 10-oct | Beta (PENDIENTE confirmar) | Desarrollo |

## 10. PENDIENTES abiertos

- Número de dispatchers independientes en EE. UU. y proporción hispanohablante.
- Criterio de éxito y de cierre del piloto.
- Precio: A o B.
- Estado de los riesgos técnicos del informe de julio.
- Fecha real de perfiles y de beta.
- Modelo de IA en producción y costo por consulta.
- Posicionamiento del producto para el pitch (23-sep-2026): en la reunión interna quedó abierto si Trucky se presenta como "solución documental" o como "plataforma integral de optimización logística"; Alexander pidió definir el MVP exacto. La sección 3 ya orienta la respuesta (el verificador puede ampliarse sin que Trucky se vuelva solo un gestor documental, y lo decide el uso en el piloto), pero no hay un cierre formal de qué mensaje de posicionamiento usar en el pitch a socios/inversión.
- Verificar competencia mencionada el 23-sep-2026: si "Anumeo" es un competidor real o un error de transcripción, y si la plataforma de ~5.000 dispatches con el influencer Bobby ("Load Hunters") es LoadHunter o un competidor distinto.
- Roadmap técnico comercial (23-sep-2026): DAT con acceso a API privada confirmado, Truckstop con API pública disponible, migración de ClickUp a Jira con 47 tickets pendientes (4 en desarrollo, 13 en revisión/pruebas). No hay un archivo del proyecto donde este seguimiento de roadmap tenga lugar (no es arquitectura de IA ni decisión de mercado); PENDIENTE decidir dónde documentarlo o si vive solo en Jira.

## 11. Mapa del proyecto

| Archivo | Contenido |
|---|---|
| `CLAUDE.md` | Instrucciones para Claude Code |
| `00-LEER-PRIMERO/estado-actual.md` | Fuente única: qué es, cliente, prioridades, precio, validación, fechas, pendientes |
| `mercado/mercado-objetivo.md` | Cifras de FMCSA y HubSpot por segmento |
| `mercado/evidencia-entrevistas.md` | Hallazgos por entrevista (se amplía con el piloto) |
| `mercado/vocabulario.md` | Términos del mercado para el chat |
| `producto/arquitectura-ia.md` | Reglas, datos y caché antes que el LLM |
| `brand/trucky-logo-white.png`, `brand/trucky-logo-purple.png` | Logo oficial |

Dónde va cada cosa nueva:
- una decisión → este documento;
- una entrevista → `evidencia-entrevistas.md`;
- un cambio técnico → `producto/`;
- datos de mercado → `mercado/`.
