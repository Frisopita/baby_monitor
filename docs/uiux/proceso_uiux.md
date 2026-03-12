# Guía de preguntas y proceso UI/UX — Monitor de Bebé

## A. Usuario y contexto (quién, dónde, en qué momento)
- ¿Quién lo va a usar? Padres, cuidador.
- ¿En qué condiciones lo usará? de noche, con sueño, en una mano, en un tobillo o en el pañal.
- ¿Qué tan técnico es el usuario? Nada técnico
- ¿Cuáles son sus miedos principales? asfixia por estar boca abajo y mejorar patrones de sueño del bebé
- ¿Qué decisiones tomarán con la información? ir a ver al bebé, girarlo, llamar a alguien, ir a urgencias

## B. Problema y propuesta de valor (qué promesa haces)
- ¿Cuál es el “job to be done” en una frase?  
  - “Quiero saber que mi bebé está seguro mientras duerme”.
  - “Quiero conocer la calidad de sueño de mi bebé, sugerencias para mejorar su calidad de sueño y por ende la mía”.
- ¿Qué 3 cosas son las más importantes que el sistema debe informar?
  - Posición del bebé en estado real
  - Su calidad de sueño
  - Patrones de sueño
- ¿Qué NO vas a hacer en v1 para mantenerlo simple?
  - Medir temperatura
  - Conexión Wifi

## C. Señales y eventos (qué detectas y qué significa)
- ¿Qué detectas exactamente? 
  - posición, ritmo cardiaco, movimiento y SPO2
- ¿Qué tan confiable es cada medición? 
  - TBD
- ¿Cuáles son los estados del bebé que quieres representar?  
  - Diferentes Posiciones.
- ¿Cuáles son los falsos positivos más probables? ¿Cómo los manejarás?
  - Que no mida bien cuando se empieza a dormir el bebé
  - TBD no se como manejarlo

## D. Alertas (la parte más delicada)
- ¿Qué eventos ameritan alerta? 
  - Que el bebé este boca abajo, no es alerta critica pero si es necesario 
- ¿Qué severidades tendrás? Crítica 
- ¿Cuál es el “tiempo de reacción” esperado del usuario en cada nivel?
- ¿Cómo confirmas que el usuario entendió? (acknowledge, repetir, escalamiento)
- ¿Qué pasa si el usuario no responde? (escalamiento: sonido, llamada, contacto de respaldo)

## E. Confianza y explicabilidad (por qué debo creerte)
- ¿Cómo mostrarás “calidad de lectura”? (señal buena / mala / sensor suelto)
- ¿Cómo evitarás que el usuario se confíe de datos dudosos?
- ¿Qué le dirás al usuario cuando NO haya lectura? (sin pánico, pero claro)
- ¿Qué métricas mostrarás y cuáles ocultarás para no abrumar?

## F. Onboarding y configuración (primer uso)
- ¿Cuánto debe tardar el setup ideal? (objetivo: < 3–5 minutos)
- ¿Qué permisos necesita la app? (Bluetooth, notificaciones, Wi-Fi)
- ¿Cómo emparejas? ¿Qué haces si falla?
- ¿Cómo enseñas a colocar el sensor correctamente? (tutorial visual + checklist)

## G. Arquitectura de experiencia (app vs dispositivo)
- ¿Qué se ve en el dispositivo y qué en la app?
- ¿Qué funciona sin internet?
- ¿Qué pasa si el teléfono está lejos o sin batería?
- ¿Habrá 1 bebé / múltiples bebés? ¿múltiples cuidadores?

## H. Privacidad y datos (importantísimo con bebés)
- ¿Qué datos guardas y por cuánto tiempo?
- ¿Se sube algo a la nube? ¿para qué?
- ¿Quién puede ver la info? (roles: mamá/papá/abuela)
- ¿Qué ocurre si alguien roba el teléfono o comparte la cuenta?

## I. Métricas de éxito (cómo sabrás que UI/UX funciona)
- ¿Qué significa “éxito” en v1?
  - Setup sin ayuda
  - Alertas entendidas en < 3 segundos
  - Bajo número de falsas alarmas
  - El usuario confía y no abandona
- ¿Qué vas a medir? (tiempo de onboarding, tasa de fallas de pairing, tasa de “sin lectura”, etc.)

---

# 2) Proceso recomendado paso a paso (para hacerlo bien desde cero)

## Paso 1: Define alcance y límites (1 hoja)
- Objetivo principal (1 frase)
- 3 funciones core
- 3 cosas fuera de alcance (v1)
- Supuestos (ej. “si no hay lectura, se alerta”)

**Salida:** “Product brief” de 1 página.

## Paso 2: Identifica escenarios críticos (safety-first)
Escribe 8–12 escenarios reales. Por ejemplo:
- Noche, usuario dormido, alerta crítica.
- Sensor se despega → “sin lectura”.
- Bebé boca abajo.
- Teléfono sin batería.
- Bluetooth se desconecta.

**Salida:** lista de escenarios + prioridad (crítico/alto/medio).

## Paso 3: Mapa de estados y alertas
Diseña un diagrama sencillo de estados:
- Normal (OK)
- Advertencia
- Crítico
- Sin lectura / Error
- Modo nocturno / silencio
- Desconectado / reconectando

Y define por estado:
- Qué muestra la app
- Qué suena/vibra
- Qué acción pide al usuario

**Salida:** “Alerting spec” (tabla de severidades + comportamiento).

## Paso 4: Define la IA/algoritmo como “contrato UX”
No necesitas el algoritmo completo, pero sí el contrato:
- Qué evento produce (posición = supino/prono/lateral/unknown)
- Cada cuánto se actualiza
- Umbrales y tiempos (ej. “prono sostenido 10s”)
- Calidad de señal (0–100 o bueno/regular/malo)

**Salida:** “Sensor-to-UX contract”.

## Paso 5: User flows (rutas principales)
Dibuja los flujos mínimos:
- Primer uso (onboarding + pairing + colocación)
- Uso diario (ver estado + modo noche)
- Alerta crítica (recibir → entender → actuar → confirmar)
- Problemas (sin lectura, desconexión, batería baja)

**Salida:** diagramas de flujo.

## Paso 6: Wireframes (baja fidelidad)
Empieza por pantallas clave:
- Home / Estado del bebé
- Detalle de lectura (confiabilidad)
- Configuración de alertas
- Historial (si aplica)
- Ayuda / colocar sensor
- Pantalla de “sin lectura”

**Regla de oro:** en alertas, **texto corto + acción clara** (no dashboards).

## Paso 7: Sistema de diseño mínimo (consistencia)
Define:
- Tipografías y tamaños (accesibilidad)
- Colores por severidad (no depender solo del color)
- Componentes: tarjetas, banner de alerta, botones primarios, chips de estado
- Microcopy: frases estándar (OK / sin lectura / reconectando)

**Salida:** mini design system (10–15 componentes).

## Paso 8: Prototipo clickable + pruebas rápidas
- Prototipo en Figma (o similar)
- Prueba con 5–8 personas (aunque sean conocidos) con tareas:
  - “Configura el sensor”
  - “Activa modo noche”
  - “Recibes alerta crítica, ¿qué haces?”
- Mide: tiempo, errores, confusión, frases que dicen.

**Salida:** lista de hallazgos + cambios.

## Paso 9: Especificación lista para ingeniería
Convierte UI en requerimientos:
- Reglas de alertas
- Frecuencias de actualización
- Offline behavior
- Estados de error
- Logs mínimos para depurar

**Salida:** “UX requirements” (ideal para tu SRS).

---

# 3) Checklist de pantallas mínimas (v1)
- [ ] Onboarding (permisos + pairing)
- [ ] Tutorial de colocación (visual + checklist)
- [ ] Home (estado simple + calidad de lectura)
- [ ] Alerta crítica (acción clara)
- [ ] Sin lectura (qué hacer)
- [ ] Batería baja (del sensor y del teléfono si lo monitoreas)
- [ ] Ajustes de alertas (niveles, silencios, horarios)
- [ ] Ayuda/FAQ (muy breve)

---

# 4) Para hacerlo más sólido (tipo “dispositivo médico”)
Añade dos documentos rápidos:
- **Hazard → UX Mitigation Map:** riesgo (“boca abajo no detectado”) → mitigación UX (alerta, confirmación, escalamiento, señal de calidad).
- **Traceability UX:** pantalla/alerta → requisito → prueba.
