ENTREGA FINAL DEL ASSIGNMENT 2
Helena Sofía Meneses Martínez

Link de deploy: https://algorithmic-thinking.vercel.app

Link del repositorio: https://github.com/helenameneses-16/algorithmic-thinking

Bitácora completa también en el repositorio: https://github.com/helenameneses-16/algorithmic-thinking/blob/main/PROMPT_LOG.md


QUÉ ES LA FUNCIÓN

Es un diagnóstico de marca para la página de Vyko, mi agencia de marketing. El cliente sube una captura de su red social, escribe 3 palabras de la personalidad que quiere proyectar y comparte su branding. La página mide los colores y la intensidad visual de la captura, los compara con los colores del branding y con lo que se espera de cada palabra, y da un resultado de 0 a 100 con un veredicto. Todo ocurre en el navegador. No se guarda nada y no se usa ninguna API.


CONTEXTO REAL DEL PROYECTO

- El diagnóstico aparecía como "Diagnóstico gratis" en un sticker y como primera opción del formulario de mi página. Yo decidí quitar el diagnóstico gratis del formulario y poner "Plan de marketing completo" como primera opción.
- Leonardo, mi socio, revisó la página el 6 de noviembre de 2026 y anotó que el diagnóstico no estaba definido en ningún otro archivo. Faltaba decidir qué se entrega, cómo se mide y cuánto trabajo lleva.
- Yo cambié el sticker a "Diagnóstico de marca", ya sin la palabra gratis.

Por eso elegí esta función: la página ya prometía un diagnóstico y todavía no hacía nada.


PASO 1. ESPECIFICACIÓN DE 3 CAMPOS

Campo 1. Qué hace
Es un diagnóstico de marca según la red social que maneje el cliente y lo que quiere proyectar con su personalidad de marca o el público al que busca llegar. Aprobamos o calificamos si está haciendo el contenido correcto para llegar a esos clientes potenciales o no.

Campo 2. Qué datos necesita y de dónde vienen
- Red social: una captura de pantalla que sube el cliente.
- Personalidad de la marca: el cliente la describe en 3 palabras.
- Branding: el cliente lo sube o lo explica. Si no tiene branding, se le ofrece de una vez el servicio de branding de la agencia.
Los datos salen del cliente. Decidí que no se guardan, para hacerlo sencillo y porque la captura puede mostrar información de otras personas. Las imágenes se analizan en el navegador y no se suben a ningún servidor.

Campo 3. Cómo se sabrá que funciona
Caso de prueba: se sube como branding la imagen del brand board de Vyko, como red social la captura del Instagram de Monka, que es una joyería de cuero, y se escriben las palabras disruptiva, innovadora, creativa. El diagnóstico debe decir que la red social no está alineada con el branding, sobre todo porque los colores no se parecen.

Auditoría
Pedí a la IA que auditara mi especificación como lo haría una pareja. Me hizo estas preguntas:
1. Qué significa aprobar y con qué regla se decide.
2. Contra qué se compara el contenido correcto, porque el público no estaba en el campo 2.
3. Si es una captura o varias, y qué red social.
4. Qué hace la función con el branding.
5. Qué pasa si no hay branding.
6. Quién califica, reglas fijas o una IA.
Mis respuestas y lo que quedó en la función: aprobar es un resultado de 70 o más sobre 100. Es una sola captura. Califican reglas fijas que mido con los colores, sin IA. Si no hay branding, el resultado es parcial y se ofrece el servicio. El público al que busco llegar no quedó como dato de entrada. Eso es una limitación que reconozco.


PASO 2. REGISTRO DE ACEPTAR, RECHAZAR O REVISAR

Entrada 1. Sin llave de API, medir colores en lugar de usar una IA que vea la captura
- Qué propuso la IA: como no tengo llave de API, medir los colores, la intensidad y el contraste de las imágenes dentro del navegador, sin ningún modelo de IA. Para comparar la personalidad, la IA agregó una lista de palabras como disruptiva, creativa o elegante, cada una con un rango de intensidad, contraste y variedad de color.
- Campo de mi especificación en juego: campo 1, qué hace. Mi especificación hablaba de saber si el contenido es correcto para llegar a los clientes. Con esta propuesta la función no puede juzgar el producto, el mercado ni lo que dicen los textos. Solo mide colores.
- Mi decisión: Aceptar.
- Por qué: no tengo llave de API y quería algo sencillo que sí funcionara a tiempo. Dejé escrita la limitación en la página y en esta bitácora para no prometer más de lo que hace. Acepté también la lista de palabras, porque sin ella no hay cómo comparar la personalidad. Reconozco que los rangos de la lista son una suposición de la IA y no salen de ninguna fuente. Por eso el resultado es una guía y no una medición científica.

Entrada 2. La primera versión no cumplía mi campo 3
- Qué pasó: al correr mi caso de prueba, la primera versión dio colores 14 de 100 pero personalidad 100. El total fue 48 y el veredicto fue "Hay que ajustar". Mi campo 3 decía que debía salir no alineada. No acepté ese primer resultado como bueno.
- Qué propuso la IA: que mande el color. Si los colores de la marca no se parecen, con menos de 40 de 100, el veredicto es "No está alineada" aunque la personalidad encaje.
- Campo en juego: campo 3, cómo se sabrá que funciona.
- Mi decisión: Aceptar el cambio.
- Por qué: mi campo 3 dice que con colores que no se parecen debe salir no alineada, y el cambio hace que la función cumpla lo que yo especifiqué. Después del cambio mi caso dio colores 5 de 100, total 43 y "No está alineada". El commit de esta decisión se llama "si los colores no se parecen, el veredicto es No está alineada".

Entrada 3. Sin branding no se debe aprobar
- Qué pasó: sin branding, la primera versión daba 100 y "Va por buen camino". No era honesto, porque no se había comparado ningún color.
- Qué propuso la IA: mostrar "Resultado parcial" con solo el puntaje de personalidad y ofrecer el servicio de branding.
- Campo en juego: campo 2, porque mi especificación dice que si no hay branding se ofrece el servicio, y campo 3.
- Mi decisión: Aceptar.
- Por qué: aprobar sin comparar colores sería engañar al cliente, y el ofrecimiento del servicio de branding es justo lo que pedí en mi campo 2.

Entrada 4. El botón "Hablar con Vyko" que no estaba en mi especificación
- Qué propuso la IA: agregar al final del resultado un botón "Hablar con Vyko" que manda el resultado por WhatsApp.
- Campo en juego: campo 1 y campo 2. Ese botón no estaba escrito en mi especificación. Lo único que mi campo 2 pide ofrecer por contacto es el servicio de branding cuando el cliente no tiene branding.
- Mi decisión: Rechazar.
- Por qué: no estaba en mi especificación y la función cumple mi campo 3 sin él. Quité el botón del código. Dejé solo el botón "Quiero mi branding", porque ese sí lo pide mi campo 2. El commit de esta decisión se llama "Quito el botón Hablar con Vyko: no estaba en mi especificación".


PASO 3. REGISTRO DE VALIDACIÓN

Deploy confirmado: https://algorithmic-thinking.vercel.app responde con código 200 y muestra la función. Comprobado el 17 de noviembre de 2026.

Caso de prueba, hecho con el mismo código que está publicado:

Input exacto:
- Branding: imagen del brand board de Vyko, subida como archivo.
- Red social: captura del Instagram de Monka.
- Palabras: disruptiva, innovadora, creativa

Output real copiado:

43 / 100
NO ESTÁ ALINEADA
Colores de tu red: #6B2D3C, #B25635, #4A5CF7, #6877F8, #CB936D
Colores de tu marca: #D4FE3D, #FF7902, #49561D, #B0D137, #87BCF3
Por qué:
Dijiste «disruptiva»: esperamos colores intensos (intensidad de 55% o más) y tu captura marca 60%. Esta palabra encaja 100 de 100.
Dijiste «innovadora»: esperamos colores intensos (intensidad de 45% o más) y tu captura marca 60%. Esta palabra encaja 100 de 100.
Dijiste «creativa»: esperamos colores intensos (intensidad de 45% o más) y tu captura marca 60%. Esta palabra encaja 100 de 100.
Tus colores de marca y los de tu captura se parecen 5 de 100.
Tu color #D4FE3D casi no aparece en tu red social.
Aunque otras partes encajan, los colores de tu marca y los de tu red no se parecen. Por eso el resultado es «No está alineada».
Qué hacer primero:
Usa en tus publicaciones los colores de tu branding. Elige 2 o 3 y repítelos en fondos, textos y fotos.

Mi veredicto: Aceptar.
Razón: el resultado dice "No está alineada" y que los colores se parecen 5 de 100, que es lo que mi campo 3 pedía. Además señala #D4FE3D, el lima de Vyko, como el color que casi no aparece en la red de Monka. Como prueba de control, el brand board de Vyko usado como red social y como branding dio 98 de 100 y "Va por buen camino".

Lo que no logra: no dice que Monka vende otro producto en otro mercado, porque solo mide colores. Además, el botón azul de Instagram en la captura cuenta como un color de la red, y por eso aparecen dos azules en los colores de la red.


USO DE IA

Herramienta: Claude (Claude Code, modelo Sonnet 5.5).

Para qué la usé:
- Para hacerme preguntas de auditoría sobre mi especificación.
- Para escribir el código de la página y de la función.
- Para correr mi caso de prueba con mis imágenes y corregir lo que no cumplía mi campo 3.
- Para crear el repositorio, publicar el deploy y ordenar esta bitácora con lo que pasó de verdad.

Lo que decidí y verifiqué yo:
- Elegí la función, escribí los campos 1 y 2 de la especificación y el caso de prueba del campo 3, con las imágenes que di.
- Decidí hacerlo sin API y sin guardar datos.
- Decidí aceptar 3 propuestas de la IA y rechazar 1, el botón de WhatsApp, con las razones de arriba.
- Verifiqué que el resultado de mi caso de prueba coincide con mi campo 3.
- Reconozco que la lista de palabras y sus rangos son suposiciones de la IA.
