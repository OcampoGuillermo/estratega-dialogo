# EL ESTRATEGA — Humano digital estilo JARVIS

Busto 3D procedural + ElevenLabs Conversational AI + lip-sync por fonema + HUD Stark.
Un solo archivo `index.html`. Sin build.

## 1. Qué incluye

* Escena Three.js 0.160: busto con armadura rojo/negro, reactor, circuitos, gafas HUD, tablero de ajedrez, sala roja/cian, partículas, paneles holo.
* Boca con 4 visemas ES: `A / E-I / O-U / M-B-P` + coarticulación + energía Web Audio + anclaje automático.
* Giros 360° con `OrbitControls`, mirada que sigue, parpadeo, gestos por frase, botón Volver al frente 0.9s.
* Panel JARVIS: boot, onda de voz, transcript, monitor de visemas, FPS, estado de conexión.
* Demo sin conexión con `speechSynthesis` (no gasta créditos).
* Config de `Agent ID` con `?agente=ID`, `localStorage`, offset de sincronía calibrable.

## 2. Crear el agente para ESTE personaje (recomendado, con tu clave)

No pegues tu `XI-API-KEY` en el frontend. La clave se queda en tu cuenta de ElevenLabs. El navegador usa un **agente público**.

1. Entra a `elevenlabs.io` → Agents → Create agent.
2. Nombre: `El Estratega — Diálogo con el Mentor`.
3. Idioma: Spanish (es). Modelo: `eleven_flash_v2_5` (baja latencia).
4. Voz: hombre 35-45 latino, templado y táctico. Prueba `Facundo Grok` o `Elder`. Agrega la voz a tu workspace antes de asignarla.
5. Prompt del sistema (pégalo tal cual):

```
Hablas como EL ESTRATEGA: mitad humano, mitad máquina. Tienes 38 años, vives en una mansión de mármol y acero, juegas ajedrez para pensar. Tratas de "usted". Tono sereno, preciso, nunca teatral.
Reglas: respuestas de 2 a 5 oraciones, sin listas (se escuchan, no se leen). Cada respuesta termina con una pregunta que obligue a pensar una jugada. Distingue lo documentado de lo opinado. Si te preguntan si eres IA, admítelo: "Soy una recreación con IA del Estratega". No opinas de política partidaria actual. Si te piden hechos fuera de tu mundo (ajedrez, estrategia, IA, decisiones), responde desde tu experiencia en el tablero.
Saludo inicial: "Tome asiento. Soy el Estratega. ¿Empezamos por una apertura, una decisión difícil que tenga entre manos, o por cómo pienso cuando muevo la reina?"
```

6. Base de conocimiento: crea un documento de texto con 12 bloques: quién soy, la mansión, el ajedrez como método, aperturas que enseño, medio juego, finales, gestión del tiempo, lectura del rival, IA y humanos, derrotas famosas, máximas del Estratega, glosario. Márcalo como `Estratega — Base (vida, método, partidas, ideas)`.
7. Security → hazlo **público** (authentication OFF). Si usas Allowed domains, agrega tu dominio: `TU_USUARIO.github.io` y `localhost`.
8. Copia el `agent_id` (empieza con `agent_...`). Pégalo en la app: botón Configurar → pegar → Guardar. O abre `index.html?agente=agent_TU_ID`.

Enlace de prueba directa: `https://elevenlabs.io/app/talk-to?agent_id=TU_ID`.

## 3. Probar en local

```powershell
cd estratega-jarvis
python -m http.server 8000
# abre http://localhost:8000/
```

Necesitas micrófono + internet. Sin Agent ID, usa `Demo sin conexión`.

## 4. Publicar en GitHub Pages

1. En github.com → New repository → `estratega-dialogo` → Public.
2. Add file → Upload files → sube `index.html` y este README → Commit.
3. Settings → Pages → Source: Deploy from a branch → Branch: main, /(root) → Save.
4. Espera 1-2 min: `https://TU_USUARIO.github.io/estratega-dialogo/`.
5. En ElevenLabs → Allowed domains → agrega `TU_USUARIO.github.io`.

## 5. Calibrar boca/voz

Si la boca va adelantada o atrasada, abre Configurar → Offset y mueve de a 40ms. Negativo si la boca abre antes que el sonido, positivo si abre después. Queda guardado.

## 6. Costos y privacidad

Cada minuto con el agente consume créditos de ElevenLabs. Un agente público lo puede usar cualquiera con el enlace. Limita dominios y revisa consumo. La voz viaja a ElevenLabs. Avisalo en clase y ofrece escribir en vez de hablar. Es recreación artística, no persona real.
