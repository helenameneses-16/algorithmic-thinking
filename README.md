# Diagnóstico de marca de Vyko

Assignment 2 de Applied Algorithmic Thinking (LINQ03.2).
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


### 3. Casos límite que encontré al probar la versión final
- Lo que probé: hice dos diagnósticos completos en la app publicada. En el segundo describí mi marca como elegante, juvenil y maximalista.
- Lo que falló: la app no pudo medir "maximalista" y me dio un resultado parcial, justo sin la palabra más importante de la personalidad de mi marca. También noté que solo deja subir imágenes del branding y no PDF, aunque muchas veces el branding viene en PDF.
- Mi decisión: no cambié la palabra para que la app sí me diera un resultado completo, porque eso escondería el problema en vez de resolverlo. Lo dejo documentado.
- Qué haría después: agregar una lista más grande de palabras de personalidad para que la app entienda más descripciones, y aceptar archivos PDF además de imágenes.
