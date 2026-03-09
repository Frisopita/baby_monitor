# Plantilla UI/UX — Monitor de Bebé (v1)

## 0. Información del documento
- **Proyecto:** Monitor de Bebé
- **Versión:** 0.1
- **Fecha:** 2026-02-26
- **Autora:** Frida Sofía Andrade Sierra
- **Alcance de esta versión:** prototipo
- **Estado:** Borrador

---

## 1. Resumen ejecutivo (1 página)
### 1.1 Objetivo (1 frase)
- **Objetivo:** TBD

### 1.2 Propuesta de valor (2–3 bullets)
- TBD
- TBD
- TBD

### 1.3 Alcance v1 (qué SÍ incluye)
- TBD

### 1.4 Fuera de alcance v1 (qué NO incluye)
- TBD

### 1.5 Supuestos y dependencias
- **Supuestos:** TBD
- **Dependencias:** (ej. BLE estable, app móvil, sensor específico, etc.) TBD

---

## 2. Usuarios y contexto de uso
### 2.1 Perfiles de usuario (personas)
Completa al menos 2 perfiles.
- **Persona 1 (principal):**
  - Edad/rango: TBD
  - Rol: (mamá/papá/cuidador/etc.) TBD
  - Nivel de tecnología: Bajo / Medio / Alto
  - Objetivo principal: TBD
  - Miedos/dolores: TBD
  - Entorno típico: (noche, cansancio, ruido, etc.) TBD

- **Persona 2 (secundaria):**
  - Edad/rango: TBD
  - Rol: TBD
  - Nivel de tecnología: Bajo / Medio / Alto
  - Objetivo principal: TBD
  - Miedos/dolores: TBD
  - Entorno típico: TBD

### 2.2 Contextos de uso (situaciones reales)
Lista 6–10 escenarios.
- [ ] Noche, usuario dormido, alerta crítica.
- [ ] TBD
- [ ] TBD
- [ ] TBD
- [ ] TBD
- [ ] TBD

### 2.3 Restricciones del contexto
- Uso con una mano: Sí / No / TBD
- Iluminación baja: Sí / No / TBD
- Sin internet: Sí / No / TBD
- Ruido ambiental: Bajo / Medio / Alto / TBD
- Otros: TBD

---

## 3. Problema y “Job to be Done”
### 3.1 Problema principal
- **Problema:** TBD

### 3.2 Job to be done (frase)
- **Cuando** ______, **quiero** ______, **para** ______.
- TBD

### 3.3 Resultados esperados (outcomes)
- TBD
- TBD
- TBD

---

## 4. Señales, mediciones y significado
> Define qué mide el sistema y cómo se interpreta en la UI.

### 4.1 Sensores / señales (lista)
Para cada señal, completa esta tabla.

| Señal | Qué detecta | Unidad/Estados | Frecuencia de actualización | Latencia aceptable | Calidad de lectura | Notas |
|---|---|---|---|---|---|---|
| Posición | TBD | supino/prono/lateral/unknown | TBD | TBD | (buena/regular/mala) TBD | TBD |
| Ritmo cardiaco | TBD | bpm | TBD | TBD | TBD | TBD |
| Movimiento | TBD | TBD | TBD | TBD | TBD | TBD |
| (Agrega más) | TBD | TBD | TBD | TBD | TBD | TBD |

### 4.2 Fuentes de error / falsos positivos (por señal)
- **Posición:** causas típicas: TBD — mitigación UX: TBD
- **Ritmo cardiaco:** causas típicas: TBD — mitigación UX: TBD
- **Movimiento:** causas típicas: TBD — mitigación UX: TBD

### 4.3 Contrato Sensor → UX (reglas mínimas)
Ejemplos de reglas:
- “Posición = prono sostenido por **X** segundos → **Alerta**”
- “Calidad de señal < **Y** por **Z** segundos → ‘Sin lectura’”
- Reglas v1:
  - TBD
  - TBD
  - TBD

---

## 5. Estados del sistema (state model)
> Define estados claros; esto guía pantallas, mensajes y pruebas.

### 5.1 Lista de estados
- Estado **OK / Normal**
- Estado **Advertencia**
- Estado **Crítico**
- Estado **Sin lectura**
- Estado **Desconectado / reconectando**
- Estado **Batería baja (sensor)**
- Estado **Batería baja (teléfono / hub, si aplica)**
- Otros: TBD

### 5.2 Transiciones (reglas de cambio de estado)
- OK → Advertencia cuando: TBD
- Advertencia → Crítico cuando: TBD
- Cualquier estado → Sin lectura cuando: TBD
- Sin lectura → OK cuando: TBD

---

## 6. Alertas y notificaciones (lo más importante)
### 6.1 Matriz de severidad
Define niveles (mínimo 3).

| Severidad | Ejemplos de evento | Canal (push/sonido/vibración) | Persistencia | Escalamiento | Acción requerida del usuario |
|---|---|---|---|---|---|
| Info | TBD | TBD | TBD | TBD | TBD |
| Advertencia | TBD | TBD | TBD | TBD | TBD |
| Crítica | TBD | TBD | TBD | TBD | TBD |

### 6.2 Reglas de alertas (detalle)
Para cada alerta importante:

**Alerta #1 — Nombre:** TBD  
- **Disparador (condición):** TBD  
- **Umbral y tiempo:** (ej. >10s) TBD  
- **Qué muestra la UI:** TBD  
- **Texto exacto (microcopy):** TBD  
- **Acción principal (CTA):** TBD  
- **Acción secundaria:** TBD  
- **Qué pasa si el usuario NO responde:** TBD  
- **Cómo se cancela/ack:** TBD  
- **Notas de seguridad:** TBD  

(Repite para todas las alertas v1)

### 6.3 Modo noche / silencioso
- ¿Existe? Sí / No / TBD
- ¿Qué se silencia y qué no? TBD
- ¿Cómo se activa/desactiva? TBD
- ¿Hay horarios? Sí / No / TBD

---

## 7. Arquitectura de experiencia (App vs Dispositivo)
### 7.1 Componentes del sistema
- Sensor (en bebé): TBD
- App móvil: iOS / Android / ambos / TBD
- Hub/base (si aplica): TBD
- Nube (si aplica): Sí / No / TBD

### 7.2 Qué funciona sin internet
- TBD

### 7.3 Qué pasa si...
- **Se desconecta BLE:** TBD
- **El teléfono se apaga:** TBD
- **La app está cerrada:** TBD
- **Sensor sin batería:** TBD

---

## 8. Onboarding y configuración (primer uso)
### 8.1 Objetivo del onboarding
- Tiempo objetivo: ___ min (meta: 3–5 min) TBD
- Resultado final: “usuario listo y confiado” con: TBD

### 8.2 Checklist de primer uso
- [ ] Descargar app
- [ ] Permisos (Bluetooth, notificaciones, etc.)
- [ ] Pairing del sensor
- [ ] Colocación correcta del sensor
- [ ] Prueba rápida / verificación de lectura
- [ ] Configurar alertas
- [ ] Activar modo noche (si aplica)

### 8.3 Puntos donde puede fallar (y cómo lo explicas)
- Falla #1: TBD → Mensaje/solución: TBD
- Falla #2: TBD → Mensaje/solución: TBD
- Falla #3: TBD → Mensaje/solución: TBD

---

## 9. Navegación y pantallas (IA de información)
### 9.1 Mapa de navegación (sitemap)
- Home / Estado
- Alertas / Centro de notificaciones
- Historial (si aplica)
- Configuración
- Ayuda / Colocación
- Otros: TBD

### 9.2 Pantallas mínimas v1 (lista)
- [ ] Home (estado simple + calidad lectura)
- [ ] Detalle de lectura (opcional)
- [ ] Pantalla de alerta crítica (acción clara)
- [ ] Sin lectura (qué hacer)
- [ ] Batería baja
- [ ] Pairing / reconexión
- [ ] Ajustes de alertas
- [ ] Ayuda / FAQ

### 9.3 Wireframes (links / archivos)
- Figma / imágenes: TBD

---

## 10. Contenido y microcopy (textos exactos)
> Escribe los textos tal como aparecerán.

### 10.1 Mensajes estándar
- **OK:** “TBD”
- **Reconectando:** “TBD”
- **Sin lectura:** “TBD”
- **Sensor suelto:** “TBD”
- **Batería baja:** “TBD”
- **Crítico:** “TBD”

### 10.2 Tonalidad
- Tono: calmado / claro / directo / TBD
- Evitar: alarmismo / tecnicismos / culpa
- Ejemplos de frases “sí” y “no”:
  - Sí: TBD
  - No: TBD

---

## 11. Accesibilidad y usabilidad
- Tamaño mínimo de texto: TBD
- Contraste: TBD
- No depender solo de color para severidad: Sí / No / TBD
- Interacciones con una mano: Sí / No / TBD
- Haptics / vibración: TBD
- Idiomas: ES / EN / TBD

---

## 12. Privacidad y datos
- ¿Qué datos se guardan localmente?: TBD
- ¿Qué datos se suben a la nube?: TBD
- Retención: TBD
- Roles/compartir acceso (cuidadores): TBD
- Seguridad mínima (PIN/biometría/cifrado): TBD

---

## 13. Métricas de éxito (UX)
Define objetivos medibles.
- Onboarding completo sin ayuda: ___%
- Tiempo promedio de setup: ___ min
- Tasa de fallas de pairing: ___%
- Falsas alertas por noche: ___
- “Sin lectura” por noche: ___ min
- NPS / satisfacción: TBD

---

## 14. Plan de pruebas UX (rápido)
### 14.1 Tareas a probar (con 5–8 usuarios)
- [ ] Emparejar sensor y empezar monitoreo
- [ ] Activar modo noche
- [ ] Responder a alerta crítica
- [ ] Resolver “sin lectura”
- [ ] Ajustar sensibilidad/alertas (si aplica)

### 14.2 Qué medir
- Tiempo por tarea
- Errores
- Confusión (frases textuales)
- Éxito/fracaso

### 14.3 Hallazgos y cambios
- Hallazgo #1: TBD → Cambio: TBD
- Hallazgo #2: TBD → Cambio: TBD
- Hallazgo #3: TBD → Cambio: TBD

---

## 15. Pendientes (TBD) y decisiones abiertas
- TBD
- TBD
- TBD

---

## Apéndice A — Lista de riesgos y mitigaciones UX (opcional)
| Riesgo/Hazard | Impacto | Detección | Mitigación UX | Prueba |
|---|---|---|---|---|
| Bebé boca abajo no detectado | TBD | TBD | TBD | TBD |
| Falsa alerta frecuente | TBD | TBD | TBD | TBD |
| Sin lectura prolongada | TBD | TBD | TBD | TBD |

---

## Apéndice B — Glosario
- **Sin lectura:** TBD
- **Calidad de señal:** TBD
- **Severidad crítica:** TBD
