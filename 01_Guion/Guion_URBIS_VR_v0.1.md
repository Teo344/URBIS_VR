# Guion del escenario – URBIS VR

**Versión:** 0.1 (borrador interno – NO validado)
**Estado:** pendiente de revisión con personal de seguridad del campus
**Base:** Tabla 1 del Entregable 1P (8 decisiones evaluables)

> ⚠️ Todas las acciones "correctas" de este borrador son propuestas del equipo a partir de recomendaciones generales (NFPA 10, Reglamento de Prevención, Mitigación y Protección contra Incendios – Ecuador). Deben confirmarse o corregirse con seguridad del campus antes de implementarlas o probarlas con estudiantes. Los puntos marcados con **[VALIDAR]** son dudas concretas para esa reunión.

---

## 1. Datos generales

| Campo | Valor |
|---|---|
| Evento | Incendio de origen eléctrico (regleta sobrecargada) |
| Espacio | Laboratorio de cómputo **[nombre/bloque real: ______]**, pasillo, escaleras, salida, punto de encuentro |
| Duración objetivo | 10–15 min por sesión |
| Usuario | 1 estudiante de pregrado (18–25 años) |
| Plataformas | Meta Quest 3/3S (VR) y PC Windows (teclado y ratón) |
| Modos | **Aprendizaje:** pistas, sin límite de tiempo · **Evaluación:** sin pistas, con tiempo |
| Idioma | Español claro, frases cortas, sin jerga |

## 2. Objetivos de aprendizaje

Al terminar, el estudiante será capaz de:
1. Ubicar extintores, pulsador de alarma, salida y punto de encuentro de su laboratorio.
2. Dar la alarma de inmediato ante humo o fuego.
3. Reconocer que no se usa agua sobre equipos energizados y elegir el extintor adecuado.
4. Decidir cuándo combatir un conato y cuándo abandonar el intento y evacuar.
5. Evacuar correctamente (puerta, humo, ruta, punto de encuentro) apoyando a los compañeros.

## 3. Personajes (NPC)

| ID | Rol en la escena | Notas de inclusión |
|---|---|---|
| NPC-1 | Compañero/a junto a la regleta, se sorprende con el humo | Rasgos y género diversos |
| NPC-2 | Compañero/a que quiere volver por su mochila (tentación en D6) | No ridiculizar |
| NPC-3 | Compañero/a con movilidad reducida (silla de ruedas o muletas) | Parte natural del grupo; apoyo mutuo, no lástima |
| NPC-4 | Docente / técnico de laboratorio (opcional) | Cualquier género; no es quien "salva" a todos |
| NPC-5 | Brigadista o responsable en el punto de encuentro | Recibe el reporte de D8 |

## 4. Estructura general (fases)

| Fase | Zona | Descripción | Duración aprox. |
|---|---|---|---|
| F0 Orientación | Sala neutra / lab sin evento | Tutorial de controles, accesibilidad (subtítulos, alto contraste, tamaño de texto) y confort (teletransporte, giro por pasos, modo sentado) | 2–3 min |
| F1 Reconocimiento | Laboratorio | Encontrar y "marcar" extintor(es), pulsador, salida y señalética | 2 min |
| F2 Evento | Laboratorio | La regleta empieza a humear → chispa → llama pequeña | — |
| F3 Decisiones | Laboratorio | D1 a D6 | 3–4 min |
| F4 Evacuación | Pasillo, escaleras, salida | D7, humo en el pasillo | 2–3 min |
| F5 Cierre | Punto de encuentro | D8 y retroalimentación con resumen | 2 min |

Ver el diagrama en `Diagrama_Flujo.md`.

---

## 5. Fichas de decisión

> Plantilla por ficha: disparador → opciones → consecuencia → retroalimentación → canales → objetos → registro.

### D1 – Aparece humo en la regleta
| Campo | Contenido |
|---|---|
| Zona / momento | Laboratorio, al terminar F1 |
| Disparador | Sale humo de la regleta de la mesa **[n.º]**, olor a quemado y chisporroteo |
| Acción correcta | Avisar en voz alta (botón "¡Fuego!") **y** activar el pulsador de alarma |
| Opciones incorrectas | a) Ignorar y seguir · b) Acercarse a desconectar la regleta con la mano · c) Tomar la mochila |
| Consecuencia | Correcta: suena la alarma y los NPC reaccionan. Incorrecta o sin acción en **[20] s**: el humo aumenta y aparece la llama (sigue el flujo con menos tiempo para D3) |
| Retroalimentación | "Avisar de inmediato da tiempo a todos para reaccionar. El pulsador activa la alarma del edificio." |
| Pista (modo aprendizaje) | Brillo/contorno sobre el pulsador + flecha |
| Canales accesibles | Subtítulo "[chisporroteo] [olor a quemado]" · ícono de humo · vibración corta |
| Objetos | `INT_Regleta`, `INT_PulsadorAlarma` |
| Registro CSV | `D1, acierto, tiempo_s, opcion_elegida` |
| [VALIDAR] | ¿El laboratorio real tiene pulsador dentro o en el pasillo? ¿Hay un número interno o una brigada a la que llamar? |

### D2 – Equipos energizados cerca del fuego
| Campo | Contenido |
|---|---|
| Zona / momento | Laboratorio, después de D1 |
| Disparador | Las PCs y la regleta siguen encendidas; el fuego es pequeño |
| Acción correcta | Cortar la energía en el tablero/breaker del laboratorio **solo si se puede llegar de forma segura** |
| Opciones incorrectas | a) Lanzar agua (botella) · b) Desconectar la regleta en llamas con la mano · c) Ir al tablero cruzando por el fuego |
| Consecuencia | Correcta: las pantallas se apagan y la luz baja a emergencia. Agua: chispazo y el fuego crece → D5. Tablero inaccesible: debe saltar a evacuar sin penalización |
| Retroalimentación | "Nunca uses agua sobre equipos eléctricos: conduce la electricidad. Si el tablero está lejos del fuego, corta la energía; si no, no te arriesgues." |
| Canales accesibles | Subtítulo "[equipos encendidos]" · ícono de rayo sobre el tablero |
| Objetos | `INT_TableroElectrico`, `INT_BotellaAgua` (distractor) |
| Registro CSV | `D2, acierto, tiempo_s, opcion_elegida` |
| [VALIDAR] | ¿Dónde está el tablero real? ¿Un estudiante está autorizado a manipularlo o eso le corresponde al docente o técnico? |

### D3 – El fuego aún es pequeño (conato)
| Campo | Contenido |
|---|---|
| Zona / momento | Laboratorio |
| Disparador | Llama del tamaño de **[una papelera]**, con salida libre a la espalda |
| Acción correcta | Tomar el extintor adecuado (**CO₂** preferente para equipos electrónicos; PQS válido) **o** decidir evacuar. Ambas son válidas si son coherentes con las condiciones |
| Opciones incorrectas | a) Extintor de agua (si existe en escena) · b) Sofocar con una chaqueta · c) Quedarse mirando |
| Consecuencia | Elige extintor → D4. Elige evacuar → D6 (acierto). Elige mal → el fuego crece → D5 |
| Retroalimentación | "El fuego eléctrico es de clase C. El CO₂ no conduce la electricidad ni deja residuos en los equipos. Evacuar también es correcto si no te sientes seguro." |
| Canales accesibles | Etiquetas en el extintor con texto + ícono + color (no solo color) |
| Objetos | `INT_Extintor_CO2`, `INT_Extintor_PQS` |
| Registro CSV | `D3, acierto, tiempo_s, extintor_elegido` |
| [VALIDAR] | ¿Qué extintores hay realmente en el laboratorio? ¿La ESPE espera que un estudiante intervenga o solo que evacúe? |

### D4 – Uso del extintor (técnica PASS)
| Campo | Contenido |
|---|---|
| Zona / momento | Laboratorio, solo si eligió extintor en D3 |
| Disparador | Extintor en la mano |
| Acción correcta | Ubicarse a **[2–3] m** con la salida a la espalda y aplicar PASS: **Tirar** del pasador → **Apuntar** a la base → **Apretar** la palanca → **Barrer** de lado a lado |
| Errores | Apuntar a las llamas y no a la base · quedar de espaldas a la pared (sin salida) · demasiado cerca o lejos · olvidar el pasador |
| Consecuencia | Correcta en **[≤10] s** de descarga: el fuego se apaga → D6. Incorrecta: el fuego no baja → D5 |
| Retroalimentación | "Apunta siempre a la base del fuego y mantén la salida detrás de ti para poder escapar." |
| Pista | Pasos PASS numerados en un panel; marca en el piso con la distancia segura |
| Canales accesibles | Cada paso con texto + ícono + vibración al completarlo · versión PC: teclas/clic |
| Objetos | `INT_Extintor_*` (pasador separado, manguera, palanca) |
| Registro CSV | `D4, acierto, pasos_correctos/4, distancia_m, salida_a_espalda` |
| [VALIDAR] | Distancia recomendada y tiempo de descarga típico del extintor real |

### D5 – El fuego no se controla
| Campo | Contenido |
|---|---|
| Zona / momento | Laboratorio, si falla D2/D3/D4 o pasa demasiado tiempo |
| Disparador | El fuego se extiende a otra mesa, el humo baja del techo y el extintor se vacía |
| Acción correcta | Abandonar el intento y evacuar de inmediato |
| Opciones incorrectas | Buscar otro extintor lejos · seguir descargando el extintor vacío |
| Consecuencia | Correcta → D6. Si se demora **[15] s**: aviso de peligro y la visibilidad baja |
| Retroalimentación | "Si el fuego no baja en pocos segundos o el humo te rodea, deja de combatirlo: tu vida es la prioridad." |
| Canales accesibles | Subtítulo "[el fuego se extiende]" · viñeta roja suave (no parpadeante) |
| Registro CSV | `D5, acierto, tiempo_s` |
| [VALIDAR] | Criterio concreto para abandonar (tiempo, tamaño del fuego, humo) |

### D6 – Salida del laboratorio
| Campo | Contenido |
|---|---|
| Zona / momento | Puerta del laboratorio |
| Disparador | NPC-2 dice "¡Espera, mi mochila!" |
| Acción correcta | No regresar por objetos · salir y **cerrar la puerta sin llave** |
| Opciones incorrectas | Volver por la mochila o el celular · dejar la puerta abierta · cerrar con llave |
| Consecuencia | Correcta: el humo queda contenido y el pasillo está más limpio en D7. Volver: pierde tiempo y el humo en el pasillo aumenta |
| Retroalimentación | "Cerrar la puerta frena el humo y el fuego. Los objetos se reemplazan; las personas no." |
| Canales accesibles | Ícono de puerta + texto "Cerrar" · sonido de puerta subtitulado |
| Objetos | `INT_Puerta`, `INT_Mochila` (distractor) |
| Registro CSV | `D6, acierto, regreso_objeto, puerta_cerrada` |
| [VALIDAR] | ¿Revisar que no quede nadie dentro antes de cerrar? |

### D7 – Pasillo con humo
| Campo | Contenido |
|---|---|
| Zona / momento | Pasillo y escaleras |
| Disparador | Humo en la parte alta del pasillo |
| Acción correcta | Desplazarse **agachado** siguiendo la señalética de salida (ISO 7010) por las **escaleras**, sin usar el ascensor (si existe) |
| Opciones incorrectas | Caminar erguido dentro del humo · ruta no señalizada · ascensor · correr |
| Consecuencia | Correcta: llega a la salida. Erguido: la visibilidad baja y aparece un aviso. Ruta equivocada: callejón y regreso |
| Retroalimentación | "El humo sube: cerca del piso hay más aire y visibilidad. Sigue siempre las señales de salida." |
| Mecánica | VR: agacharse físicamente **o** botón "agacharse" (accesible y en modo sentado). PC: tecla C/Ctrl |
| Canales accesibles | Flechas de salida con forma + texto (no solo verde) · alto contraste resalta la ruta |
| Registro CSV | `D7, acierto, tiempo_agachado_%, ruta_correcta, tiempo_s` |
| [VALIDAR] | Ruta oficial de evacuación del bloque y existencia de ascensor |

### D8 – Llegada al exterior
| Campo | Contenido |
|---|---|
| Zona / momento | Escaleras → punto de encuentro |
| Disparador | NPC-3 (movilidad reducida) necesita apoyo; en el exterior está el brigadista (NPC-5) |
| Acción correcta | Apoyar a NPC-3 (acompañarlo o avisar de su ubicación a la brigada), ir al **punto de encuentro** y **reportarse** |
| Opciones incorrectas | Ignorar a NPC-3 · quedarse en la puerta del edificio · irse del campus sin reportarse · regresar al edificio |
| Consecuencia | Correcta: conteo completo → pantalla de resultados |
| Retroalimentación | "Reportarte permite saber si falta alguien. Apoyarnos entre todos es parte de la evacuación." |
| Canales accesibles | Ícono ISO 7010 de punto de encuentro + texto |
| Registro CSV | `D8, acierto, ayudo_companero, reporto` |
| [VALIDAR] | Protocolo real para personas con movilidad reducida en escaleras (¿zona de refugio? ¿esperar a la brigada?) y ubicación del punto de encuentro |

---

## 6. Ramificación resumida

```
D1 → D2 → D3 ─┬─ extintor → D4 ─┬─ controla → D6
              │                 └─ falla → D5 → D6
              ├─ evacuar → D6
              └─ opción errónea → D5 → D6
D6 → D7 → D8 → Resultados
```
Cualquier rama termina en evacuación y en el punto de encuentro (no hay "game over"); la retroalimentación es formativa.

## 7. Retroalimentación final (pantalla de resultados)

- Lista D1–D8 con ✔/✘, el texto de la acción correcta y el "porqué" (máximo 2 líneas cada una).
- Tiempo total (solo en modo evaluación).
- Botones: **Repetir** · **Repetir en modo aprendizaje** · **Salir**.
- Tono no punitivo: "Esto lo puedes mejorar" en lugar de "Fallaste".

## 8. Registro CSV (una fila por decisión)

`sesion_id, fecha, modo, plataforma, decision, acierto, tiempo_s, detalle`

## 9. Textos de subtítulos / sonidos clave

| Evento | Subtítulo | Canal adicional |
|---|---|---|
| Humo inicial | [chisporroteo] [olor a quemado] | vibración corta |
| Alarma | [alarma de incendio] | luz estroboscópica + ícono de dirección |
| Fuego crece | [el fuego se extiende] | viñeta suave |
| Puerta | [puerta cerrándose] | — |
| Brigadista | "¿Estás bien? ¿Falta alguien de tu laboratorio?" | — |

## 10. Pendientes antes de v1.0

- [ ] Completar los datos del laboratorio real (nombre, bloque, ubicación de los elementos) tras el levantamiento.
- [ ] Resolver todos los **[VALIDAR]** con seguridad del campus.
- [ ] Definir los tiempos entre corchetes `[ ]` y probarlos en el prototipo.
- [ ] Revisar el lenguaje con estudiantes de perfiles diversos.
- [ ] Pasar el flujo final a Figma (diagrama + storyboard).

## 11. Control de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 2026-11-09 | Equipo GR03 | Borrador inicial a partir de la Tabla 1 del Entregable 1P |
