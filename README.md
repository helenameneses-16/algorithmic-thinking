# Diagnóstico de marca de Vyko

Proyecto final de Applied Algorithmic Thinking (LINQ03.2), Assignments 2 y 3
Helena Sofía Meneses Martínez

Función nueva para la página de Vyko, una agencia de marketing. El cliente sube una captura de su red social, escribe en 3 palabras la personalidad que quiere proyectar y comparte su branding. La página dice si su red social se parece a su marca.

## Cómo funciona

1. Mide los colores con carácter de la captura de la red social y del branding.
2. Compara cada color de la marca con el color más cercano de la red.
3. Compara la intensidad, el contraste y la variedad de color de la red con lo que se espera de cada palabra de personalidad.
4. Da un resultado de 0 a 100 y un veredicto: va por buen camino, hay que ajustar o no está alineada.
5. Si el cliente no tiene branding, ofrece el servicio de branding de Vyko por WhatsApp.

Las imágenes se analizan en el navegador y no se suben a ningún servidor. No usa llaves ni API.

## Lo que no hace

No evalúa qué producto vendes, a qué mercado le hablas ni lo que dicen tus textos. Mide colores y energía visual. El botón azul de Instagram en una captura cuenta como un color de la red.

## Archivos

- `index.html`: la página y la función.
- `PROMPT_LOG.md`: especificación de 3 campos, decisiones de aceptar, rechazar o revisar, validación y uso de IA.

## Decisiones de diseño vs. sugerencias del IS
Las entradas 1 y 2 pasaron en la versión de trabajo de la página de Vyko, que vive en otro repositorio privado que comparto con mi socio. Las documento aquí porque son decisiones del mismo proyecto.

### 1. Escalabilidad: dónde publicar la página de Vyko
- Qué propuso el IS: publicar la página de Vyko en Vercel, igual que en el curso (proyecto marketing).
- Lo que verifiqué yo (23 nov 2026): con 50 visitas al mes como base y 1,000 veces más (50,000 visitas), la página usaría unos 4.3 GB y 100,000 solicitudes, dentro del límite gratis de Vercel Hobby (100 GB y 1,000,000 de solicitudes, vercel.com/docs/pricing). Pero los términos de Vercel (sección 4) dicen que Hobby es solo para uso personal o no comercial, y Vyko es una agencia.
- Mi decisión: revisar.
- Por qué: el cuello de botella no era el tráfico sino una regla. Pagar Pro costaría $20 al mes sin necesitarlo, así que decidimos publicar la versión de trabajo en Cloudflare, donde los archivos estáticos son gratis. Falta confirmar que el plan gratis de Cloudflare permita uso comercial.

### 2. Cambios que la IA hizo sin pedirlo
- Qué propuso el IS: en el commit ae2a476 cambió "ignorar" por "olvidar" en el lema y quitó la palabra "gratis" de los botones, sin que yo lo pidiera.
- Mi decisión: rechazar.
- Por qué: "imposible de ignorar" es el lema de la marca y no se cambia sin decidirlo. Lo detecté revisando los cambios del commit y revertimos esa versión.
- Lo que cambié en mi forma de trabajar: ahora reviso el diff antes de aceptar cualquier cambio.

  
### 3. Casos límite que encontré al probar la versión final
- Lo que probé: hice dos diagnósticos completos en la app publicada. En el segundo describí mi marca como elegante, juvenil y maximalista.
- Lo que falló: la app no pudo medir "maximalista" y me dio un resultado parcial, justo sin la palabra más importante de la personalidad de mi marca. También noté que solo deja subir imágenes del branding y no PDF, aunque muchas veces el branding viene en PDF.
- Mi decisión: no cambié la palabra para que la app sí me diera un resultado completo, porque eso escondería el problema en vez de resolverlo. Lo dejo documentado.
- Qué haría después: agregar una lista más grande de palabras de personalidad para que la app entienda más descripciones, y aceptar archivos PDF además de imágenes.
