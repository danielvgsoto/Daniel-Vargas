# Mercado objetivo Trucky

Actualizado: 29-sep-2026. Fuentes: HubSpot y FMCSA Company Census.

## Segmento 1 (prioridad): dispatcher

Dispatcher independiente o agencia pequeña que maneja la operación de varias flotas de 2 a 10 camiones, principalmente de dueños hispanohablantes.
- Una venta a un dispatcher equivale a varias flotas.
- Referencia de precio: ~USD 30/mes por usuario con las funciones actuales (un dispatcher entrevistado). PENDIENTE validar con el piloto.
- Requisito de producto: perfiles por carrier / compañía.
- Canal: comunidades y academias de dispatchers, por referidos. No llamadas en frío.
- Tamaño: número de dispatchers independientes en EE. UU. — PENDIENTE (no figuran en el registro de carriers).

### Target persona del segmento 1 (n=1, Jose — entrevista del 29-sep-2026)

Base: `mercado/evidencia-entrevistas.md`, entrada 1. Única entrevista a fondo del segmento; todo lo que sigue es lo evidenciado ahí, no una plantilla genérica de industria.

Rasgos evidenciados:
- Opera agencia propia, no trabaja solo: tiene dispatcher + asistente, con flujo de doble revisión (el dispatcher confirma la rate con, el asistente la vuelve a revisar).
- Es formador/referente: enseña a otros dispatchers en su comunidad (academia).
- Ya construye su propio TMS para esa comunidad — no llega a Trucky sin herramienta previa.
- No sería usuario final él mismo ("prefiere controlar su sistema"), pero ve valor en Trucky para dispatchers de su comunidad que no quieren armar el suyo. Esto lo vuelve canal (academia) y competidor potencial (TMS propio) al mismo tiempo — no solo cliente.
- Abierto a colaborar: probar la siguiente versión y conversar una colaboración con su academia.
- Ancla de precio: paga hoy ~USD 24/mes por su herramienta TMS sin integraciones; ~USD 30/mes es su punto de partida para Trucky con las funciones actuales.
- Requisito no negociable para que el segmento sea viable: perfiles multi-carrier / multi-camión (jerarquía carrier → camiones → conductores). Sin esto, "la app piensa como carrier", no como dispatcher.
- Valida el verificador de rate con como el módulo de mayor interés dentro de su flujo.

Matiz de segmentación por antigüedad (fuente: reunión interna "Reunión Avances Trucky", 23-sep-2026, Read.ai id `01M383YX3K46H1FZWF031PW9VC` / Tactiq id `fRhbGgE2K8Z1uowdZKzy`; discusión del equipo, no un dato confirmado directamente con Numeo):
- El equipo comparó su segmentación con la composición de usuarios de Numeo: la mayoría son dispatchers, menos del 5 % son drivers (~5.000 usuarios totales reportados por el equipo, cifra de Numeo no auditada de forma independiente).
- El equipo relató que operadores experimentados (2–4 camiones, 6–7 años en el negocio) muestran más resistencia a cambiar de herramienta, mientras que dispatchers/conductores con menos antigüedad (0–2 años) muestran más apertura.
- Lectura tentativa (no confirmada): dentro del segmento 1 podría haber un sub-perfil más receptivo — el dispatcher "junior", sin un sistema propio ya armado — distinto del perfil de Jose (dispatcher establecido, con TMS propio y agencia). Esto es un matiz de segmentación interna, no un cambio de segmento ni de prioridad.
- PENDIENTE: la cifra de composición de usuarios de Numeo (mayoría dispatchers, <5 % drivers) es una estimación discutida internamente, no verificada con datos propios de Numeo ni con fuente externa.

PENDIENTE (no evidenciado, no completar con relleno genérico):
- Edad, ubicación geográfica, género e ingresos personales de Jose.
- Si el patrón "junior más abierto / senior más resistente" se replica fuera de la composición de usuarios de Numeo — hoy es un solo relato de una reunión interna, no una medición propia.
- Tamaño de cada sub-perfil (dispatcher con agencia/TMS propio vs. dispatcher independiente sin equipo ni herramienta) dentro del segmento 1: no hay campo en HubSpot (`tamano_de_flota`, `idioma`, `tipo_de_equipo`, `estado_lead`) que distinga esto; no se puede cuantificar con los datos actuales.
- Tamaño total del segmento 1 (dispatchers independientes en EE. UU.): sigue PENDIENTE.

## Segmento 2 (después): dueño de flota

Dueño hispanohablante con autoridad activa (USDOT activo, MC, MCS-150 actualizado) y 2 a 10 camiones registrados en FMCSA.
- Es también la flota que atiende el dispatcher del segmento 1.
- Fuera: 11+ camiones, autoridad inactiva y no carriers. Las flotas de 1 camión solo reciben contenido.
- "Camiones registrados" (FMCSA) no es igual a "camiones operando": se confirma en la llamada y se registra en HubSpot.

## Tamaño de las flotas (FMCSA, USDOT activo con MC)

| Flota | Carriers | % |
|---|---|---|
| 1 camión | 353.732 | 59,3 % |
| 2–10 camiones | 200.600 | 33,6 % |
| Más de 10 | 41.873 | 7,0 % |

- 2–10 camiones por estado: Texas 21.356 · Florida 9.660 · Georgia 8.073.
- Hispanohablantes dentro del registro: PENDIENTE.

## Base HubSpot (4.893 contactos)

| Flota | ES | EN | Total | Trabajados |
|---|---|---|---|---|
| 1 | 1.293 | 1.536 | 2.829 | 310 |
| 2–5 | 599 | 755 | 1.354 | 139 |
| 6–10 | 104 | 170 | 274 | 32 |
| 11+ | 47 | 138 | 185 | 18 |
| No carriers | – | – | 251 | 4 |

- 2–10 camiones en español: 703 contactos (617 sin trabajar).
- 2–10 camiones en inglés: 925 contactos (840 sin trabajar).
- Origen de los contactos:
  - 4.547 del archivo `trucky_import_hubspot_otr_nacional.xlsx`;
  - ~150 de Apollo (shippers/importadores);
  - 80 de Dapta;
  - 41 del directorio intermodal de Florida;
  - 66 manuales.
- 83 % de los carriers usa correo gratuito.

## Respuesta

Base: 76 contactos con respuesta útil, de 139 con conversación, sobre 682 llamadas.

Respuesta positiva por tamaño de flota:

| Flota | Positiva |
|---|---|
| 1 camión | 38 % |
| 2–5 | 54 % |
| 6–10 | 43 % |
| 11+ | 25 % |

- Fuera de perfil: 1 camión 26 % vs 2–5 camiones 13 %.
- Respuesta positiva por idioma: español 59 % vs inglés 28 %.
- Conexión por llamada: español 17,9 % vs inglés 7,5 %.
- Las demos hechas fueron con flotas de menos de 5 camiones.

## Calidad del dato (FMCSA)

- 118 contactos trabajados: el rango de flota coincide en el 84 %; 9 % están inactivos, sin camiones o sin registro.
- 30 contactos sin trabajar: coincide el 90 %; 28 están activos con 1–5 camiones y ninguno tiene más de 10.
- Antigüedad (109 activos): menos de 2 años 9 % · 2–5 años 38 % · más de 5 años 53 %. No se usa como filtro.
