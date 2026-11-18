# Bitácora de prompts · Diagnóstico de marca de Vyko

Assignment 2 · Applied Algorithmic Thinking
Helena Sofía Meneses Martínez

## Contexto real del proyecto

Esto ya pasó antes de empezar la función, en el trabajo de la página de Vyko:

- El diagnóstico aparecía como "Diagnóstico gratis" en un sticker y como primera opción del formulario. Helena decidió quitar el diagnóstico gratis del formulario y poner "Plan de marketing completo" como primera opción.
- Leonardo revisó la página el 6 de noviembre de 2026 y anotó que el "diagnóstico" no estaba definido en ningún otro archivo: faltaba decidir qué se entrega, cómo se mide y cuánto trabajo lleva.
- Helena cambió el sticker a "Diagnóstico de marca", ya sin la palabra gratis.

Por eso esta función existe: la página ya prometía un diagnóstico y todavía no hacía nada.

## Paso 1 · Especificación de 3 campos

Estado: escrita por Helena. Se le hicieron preguntas de auditoría y falta que ella confirme los ajustes.

**Campo 1 · Qué hace**
Es un diagnóstico de marca según la red social que maneje el cliente y lo que quiere proyectar con su personalidad de marca o el público al que busca llegar. Aprobamos o calificamos si está haciendo el contenido correcto para llegar a esos clientes potenciales o no.

**Campo 2 · Qué datos necesita y de dónde vienen**
- Red social: una captura de pantalla que sube el cliente.
- Personalidad de la marca: el cliente la describe en 3 palabras.
- Branding: el cliente lo sube o lo explica. Si no tiene branding, se le ofrece de una vez el servicio de branding de la agencia.

Los datos salen del cliente. En esta versión no se guardan: las imágenes se analizan en el navegador de la persona y no se suben a ningún servidor.

**Campo 3 · Cómo se sabrá que funciona**
Caso de prueba de Helena: se sube como branding la imagen del brand board de Vyko, como red social la captura del Instagram de Monka (una joyería de cuero) y se escriben las palabras "disruptiva, innovadora, creativa". El diagnóstico debe decir que la red social no está alineada con el branding, sobre todo porque los colores no se parecen.

## Paso 2 · Construcción: aceptar, rechazar o revisar

Cada entrada dice qué propuso la IA, qué campo de la especificación estaba en juego y qué decidió Helena. La decisión y su razón las escribe Helena.

### Entrada 1 · Sin llave de API, la IA propuso medir colores en vez de "ver" la captura
- Qué propuso la IA: como Helena no tiene una llave de API, hacer el diagnóstico midiendo los colores, la intensidad y el contraste de las imágenes dentro del navegador, sin ningún modelo de IA.
- Campo en juego: campo 1 (qué hace). La especificación dice "contenido correcto para llegar a esos clientes". Con esta propuesta la función no puede juzgar el producto, el mercado ni lo que dicen los textos. Solo mide colores.
- Decisión de Helena (Aceptar, Rechazar o Revisar): _pendiente_
- Razón: _pendiente_

### Entrada 2 · La primera versión no cumplía el campo 3
- Qué pasó: al correr el caso de prueba de Helena, la primera versión dio colores 14 de 100 pero personalidad 100, y el total fue 48 con el veredicto "Hay que ajustar". El campo 3 pedía "no alineada".
- Qué propuso la IA: que mande el pilar más débil. Si los colores de la marca no se parecen (menos de 40 de 100), el veredicto es "No está alineada" aunque la personalidad encaje.
- Campo en juego: campo 3 (cómo se sabrá que funciona).
- Resultado después del cambio: colores 5 de 100, total 43, veredicto "No está alineada".
- Decisión de Helena: _pendiente_
- Razón: _pendiente_

### Entrada 3 · Sin branding no se debe aprobar
- Qué pasó: sin branding, la primera versión dio 100 y "Va por buen camino". Eso no es honesto, porque no se compararon colores.
- Qué propuso la IA: mostrar "Resultado parcial" y solo el puntaje de personalidad, más el ofrecimiento del servicio de branding que pide el campo 2.
- Campo en juego: campo 2 (branding opcional) y campo 3.
- Decisión de Helena: _pendiente_
- Razón: _pendiente_

### Entrada 4 · Cosas que la IA agregó y que no estaban en la especificación
- La lista de palabras de personalidad (disruptiva, creativa, elegante, etc.) con rangos de intensidad, contraste y variedad de color. Esos rangos los inventó la IA, no salen de ninguna fuente.
- El botón "Hablar con Vyko" que manda el resultado por WhatsApp.
- La regla de que la captura de Instagram se mide completa, así que el botón azul "Seguir" de Instagram cuenta como un color de la red. Es una limitación conocida.
- Decisión de Helena sobre cada una: _pendiente_

## Paso 3 · Validación

### Prueba previa durante la construcción (hecha en la computadora, antes de publicar)
- Input: branding = imagen del brand board de Vyko, red social = captura de Monka, palabras = "disruptiva, innovadora, creativa".
- Output real:
  - Total: 43 de 100
  - Veredicto: No está alineada
  - Colores de la red: #6B2D3C, #B25635, #4A5CF7, #6877F8, #CB936D
  - Colores de la marca: #D4FE3D, #FF7902, #49561D, #B0D137, #87BCF3
  - Texto: "Tus colores de marca y los de tu captura se parecen 5 de 100." y "Tu color #D4FE3D casi no aparece en tu red social."
- Prueba de control: el brand board de Vyko como red social y como branding dio 98 de 100 y "Va por buen camino".

### Validación en el deploy (la hace Helena)
- Input exacto: _pendiente_
- Output real copiado: _pendiente_
- Veredicto (Aceptar, Rechazar o Revisar) y razón con algo específico del output: _pendiente_

## Uso de IA

- Herramienta: Claude (Claude Code, modelo Sonnet 5.5).
- Para qué se usó: preguntas para auditar la especificación, escribir el código de la página, probar el caso de Helena con sus imágenes y redactar esta bitácora con lo que pasó de verdad.
- Lo que decidió y verificó Helena: _pendiente de escribir por Helena_
