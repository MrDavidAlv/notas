
<div align="center">

# RESUMEN GENERAL SOBRE IA GENERATIVA 

<img src="./imagenes/portada.png" width="20%">

</div>

> 📖 Basado en el libro *IA Generativa en AWS* de Marbombo, autores: Chris, Antje y Shelbee.

## 1. CASOS DE USO DE LA IA GENERATIVA Y CICLO DE VIDA DEL PROYECTO

### Servicios AWS para IA 
- Bedrock
- SageMarker
- CodeWhispperer
- Trainium
- Inferentia

### Casos de uso
- Resumen texto
- Reescritura
- Extracción de información
- Respuesta a preguntas
- Detección de contenido tóxico o dañino
- Clasificación y moderación de contenido
- Interfaz conversacional
- Traducción 
- Generación de código fuente
- Razonamiento sobre un bosquejo dibujado a mano
- Enmascarar información personal identificable(PII)
- Marketing personalizado y anuncios

### Modelos básicos y centros de modelos
- Modelos de redes neuronales grandes y complejos (con cantidades enormes de parámetros).
    > 📌 **NOTA:**  Los parámetros aprenden en una etapa de aprendizaje llamada *preformación*, donde se utilizan grandes cantidades de datos distribuidos en CPU y GPU con lo cual al final estos pueden representar entidades complejas como el lenguaje humano, imágenes, vídeos y fragmentos de audio. 

### Fuentes de modelos de IA
- Hugging Face Model Hub
- Pythorch Hub
- Amazoz SageMaker JumpStart

### Ciclo de vida del proyecto de IA generativa
No existe un ciclo de vida definitivo para un proyecto de IA generativa, pero esto podría concentrar las etapas más importantes de un ciclo de proyecto IA.

<div align="center">
    <img src="./imagenes/ciclo-vida-proyecto-IA.png" width="70%">
</div>




- **Identifique caso de uso**
    Aquí se define el caso de uso, alcance y tarea específica con el fin de tener claro los objetivos, comprender el potencial y las limitaciones. 
- **Experimente y seleccione** 
    Se utilizan técnicas de *ingeniería de indicaciones* y *aprendizaje de contexto*. Inicie con un modelo básico existente y ajuste según la necesidad de la aplicación. Evalúe tamaño y recursos, probando distintas opciones en entornos como Amazon SageMaker, Hugging Face u otros para iterar rápido antes de escalar.
- **Adapte alinee y mejore** 
    Personalice el modelo al dominio específico y caso de uso, afinando datos y parámetros. Use técnicas como RLHF para alinearlo con valores y preferencias humanas, y compleméntelo con fuentes externas o APIs.
- **Evalúe** 
    Defina métricas claras para medir mejoras y alineación con metas empresariales. La evaluación continua durante la adaptación asegura que el modelo evolucione en la dirección correcta.
- **Instale e integre** 
    Implemente el modelo optimizando la inferencia y reduciendo latencia para mejorar la experiencia del usuario. Utilice instancias de AWS optimizadas para cargas generativas y puntos de conexión flexibles.
- **Monitoree**  
    Configure métricas y alertas con servicios como Amazon CloudWatch y CloudTrail para supervisar rendimiento y seguridad. Mantenga un control constante para ajustar y optimizar en producción.

![Ciclo de vida](/imagenes/ciclo-vida.png)

### ¿Por qué IA generativa en la nube?

- **Mayor flexibilidad y elección**
    La nube ofrece la posibilidad de acceder a una amplia gama de servicios, modelos y herramientas para ajustarse a diferentes necesidades y casos de uso. Permite elegir el modelo adecuado para un proyecto y cambiarlo cuando sea necesario, aprovechando de forma continua las mejoras y nuevos modelos que aparecen.
- **Funciones de seguridad y gestión de nivel empresarial**
    Los proveedores de nube suelen integrar medidas avanzadas de seguridad y gestión para proteger datos, redes y accesos. Esto incluye cifrado, aislamiento de entornos, autenticación, autorización y detección de amenazas, lo que resulta esencial en sectores con altos requerimientos regulatorios. 

- **Capacidades generativas de última generación**
    Las plataformas en la nube facilitan el uso de modelos generativos de código abierto y propietario, así como herramientas para entrenamiento, ajuste fino e implementación a gran escala. Además, los proveedores invierten en infraestructura optimizada para IA, reduciendo los tiempos y costos de desarrollo.
- **Gastos operativos reducidos**
    Gracias a la infraestructura gestionada, la nube permite usar IA generativa sin tener que invertir en hardware propio, reduciendo gastos y simplificando la administración.
- **Un historial sólido de innovación continua**
    Las principales plataformas de nube mantienen un ritmo constante de innovación en inteligencia artificial, lanzando mejoras y nuevos servicios que ayudan a implementar soluciones más rápidas y eficientes.

### Creación de aplicaciones de IA generativa

Una aplicación de IA generativa incluye modelos generativos.

> 📌 **NOTA:** Generalmente, los proveedores de la nube ofrecen herramientas que empaquetan estas arquitecturas, como lo es CodeWhisper de AWS.

**Diagrama APP general**

<div align="center">

<img src="./imagenes/AppIA.jpeg" width="70%">

</div>

**Diagrama APP ejemplo en AWS**
<div align="center">
 <img src="./imagenes/AppIAAWS.jpeg" width="70%">
</div>


## 2. INGENIERÍA DE INDICACIONES Y APRENDIZAJE EN CONTEXTO 
Incluye métodos de código bajo para interactuar con modelos de IA generativa. *"Escribir indicaciones es tanto un arte como una ciencia"*.  
Aprendizaje en *contexto*: uso de pares de preguntas y respuestas.  
Ajuste de parámetros generativos, como la temperatura y *top-k*, para controlar la creatividad del modelo.
Componentes léxicos(tokens) de texto.

### Indicaciones y respuestas
Generalmente, las indicaciones se dan en texto y se da una respuesta en texto. En modelos multimodales, devuelve otro tipo de respuestas: la respuesta puede contener texto, imagen, audio o video. El modelo aprenderá a optimizar las respuestas para dar el mejor resultado.   


### Componentes léxicos
Los modelos de IA generativa entienden las instrucciones en contexto a través de tokens, en los cuales las palabras se fragmentan y combinan de diferentes maneras, integrando diversos componentes léxicos.

<div align="center">
 <img src="./imagenes/token.png" width="70%">
</div>

> **Token 🧩:** En el contexto de la inteligencia artificial y el procesamiento de lenguaje natural, un token es una unidad mínima de texto que el modelo utiliza para procesar y generar lenguaje.
Puede ser una palabra completa, parte de una palabra, un signo de puntuación o incluso un espacio, dependiendo del sistema de tokenización.
Los modelos transforman el texto en tokens para convertirlo en representaciones numéricas que pueden ser interpretadas y manipuladas mediante cálculos algebraicos y estadísticos.

> 📌 **Ventajas:**  Esta forma de estructurar el vocabulario permite que el modelo aprenda y comprenda el lenguaje humano durante la etapa de preentrenamiento. Además, facilita el cálculo de la respuesta, ya que esta es el resultado de operaciones algebraicas y estadísticas.


### Ingeniería de indicaciones 

Habilidad enfocada en comprender y aplicar modelos de IA generativa a tareas y casos de uso, con el objetivo de obtener el máximo provecho de los modelos y sus aplicaciones.
Generalmente, se itera múltiples veces antes de obtener la respuesta final, ya que los modelos suelen generar grandes volúmenes de texto.
La mayoría de los modelos de IA generativa han sido afinados con la ayuda de personas que etiquetan los resultados, en un proceso conocido como *aprendizaje por refuerzo*.

> **aprendizaje por refuerzo** 🎯 En inteligencia artificial, el aprendizaje por refuerzo es un enfoque en el que un agente aprende a tomar decisiones mediante la interacción con un entorno, recibiendo recompensas o penalizaciones según sus acciones.
En el caso de la IA generativa, este método se emplea para afinar modelos utilizando la retroalimentación de personas que evalúan y etiquetan las salidas del modelo, ajustando así su comportamiento para alinearlo con objetivos, valores o preferencias humanas.

En una charla es importante indicar las entradas, por ejemplo, del usuario como `Usuario:`, y para las salidas del modelo utilizar `Asistente:`. Esto le da una estructura clara que facilita la interacción.

### Estructura de indicaciones

Para mejorar la calidad de la respuesta de un modelo de IA generativa, es fundamental optimizar la estructura de la indicación.  
El modelo debe tener **clara la instrucción** y contar con **contexto suficiente** para interpretar correctamente la solicitud.

- **Instrucción:** Texto de entrada que describe de forma clara y precisa lo que se desea que el modelo realice.  
  Mientras más específica y detallada sea la instrucción, mejor será la calidad de la respuesta.

- **Contexto:** Información adicional y detalles relevantes que ayudan al modelo a comprender mejor la solicitud.  
  Este puede incluir datos previos, ejemplos o referencias específicas.

Además, se pueden incluir otros elementos para orientar la respuesta del modelo:

- **Tono:** Indica el estilo de comunicación que debe utilizar el modelo (formal, informal, técnico, amigable, persuasivo, etc.).

- **Restricciones:** Límites o condiciones que debe respetar la respuesta, como extensión máxima, uso de cierto vocabulario o evitar determinados temas.

### Inferencia con cero golpes
Pido al asistente: *“Escríbeme un haiku sobre la lluvia”*.  
No doy ejemplos, solo la instrucción, y espero la respuesta en el formato correcto.  

> 📌 **Descripción:** El modelo responde únicamente con lo aprendido en su entrenamiento, sin ejemplos adicionales.  
> Es útil cuando la tarea es sencilla o bien definida.  


### Inferencia con un golpe
Pido al asistente: *“Escríbeme un haiku sobre la lluvia”*  
y le muestro un ejemplo de la estructura:  

> *“Viejo estanque,  
salta una rana al agua,  
ruido de agua.”*  

> 📌 **Descripción:** El modelo recibe un ejemplo como referencia y lo usa para imitar la forma y el estilo esperados.  
> Es útil cuando se requiere un formato o tono específico.  


### Tipos de inferencia con ejemplos

**Inferencia con un solo golpe**
Se agrega una instrucción con un ejemplo de referencia.

Indicación:
Usuario: Responda utilizando el formato mostrado. ¿Quién ganó la serie mundial de béisbol en 2016?
Los Astros de Houston ganaron la serie mundial en 2022. Derrotaron a los Filis de Filadelfia.
¿Quién ganó la serie mundial de béisbol en 2016?

Respuesta: Los Cachorros de Chicago ganaron la serie mundial de 2016. Derrotaron a los Indios de Cleveland en siete partidos...

> 📌 **NOTA:** Respuesta más cercana a lo deseado, pero con demasiado detalle.

**Inferencia con pocos golpes**
Se proporcionan múltiples ejemplos para establecer un patrón claro.

**Cuando el aprendizaje sale mal**
Si se proporcionan ejemplos incorrectos, el modelo aprende temporalmente información errónea. Ejemplo: clasificar opiniones positivas como negativas y viceversa.

### Mejores prácticas de aprendizaje en contexto

- **Comience con cero golpes**, luego pruebe uno o pocos golpes si es necesario
- **Proporcione ejemplos consistentes** que representen bien el conjunto de datos
- **Límite: 5-6 ejemplos máximo**. Si necesita más, considere afinar el modelo
- **El aprendizaje en contexto varía** según el modelo utilizado

### Mejores prácticas de ingeniería de indicaciones

#### Estructura y claridad
- **Sea claro y conciso**: Evite ambigüedad. Si confunde a humanos, confundirá al modelo
- **Ser creativo**: Indicaciones reflexivas generan respuestas innovadoras
- **Instrucción al final**: Para textos largos, mueva la instrucción al final antes del indicador de salida

#### Especificaciones técnicas
- **Transmita el tema claramente**: Especifique quién, qué, dónde, cuándo, por qué, cómo
- **Directivas explícitas**: "Resuma en una sola frase" vs descripciones vagas
- **Evite formulaciones negativas**: Use "máximo 10 palabras" vs "no más de 10 palabras"
- **Especifique tamaño de respuesta**: Incluya límites de longitud específicos

#### Técnicas avanzadas
**Cadena de pensamientos (CoT)**
Para problemas complejos, agregue "piense paso a paso":

Indicación: ¿Qué vehículo necesita más pago inicial? (piense paso a paso)
Vehículo A: $40,000 con 30% inicial
Vehículo B: $50,000 con 20% inicial

Respuesta: Vehículo A necesita más pago inicial.
A: $40,000 × 30% = $12,000
B: $50,000 × 20% = $10,000
Por tanto, A requiere $2,000 más.

**Manejo de incertidumbre**
Defina qué hacer si el modelo no sabe: "Si no está seguro, responda 'No sé'"

**Restricciones de responsabilidad**
Para dominios especializados: "No tengo licencia médica. Consulte un profesional"

**Etiquetas XML/HTML**
Use `<text>...</text>` para estructurar indicaciones complejas y `<respuesta>...</respuesta>` para formatear salidas.

### Parámetros de configuración de inferencia

<div align="center">
    <img src="./imagenes/parametros-config.png" width="70%">
</div>

#### Parámetros principales

**Max new tokens**
- Limita componentes léxicos generados
- Controla longitud, no previene alucinaciones

**Estrategias de muestreo**
- **Muestreo codificioso**: Siempre elige palabra más probable (predeterminado)
- **Muestreo aleatorio**: Selección ponderada aleatoria, más natural

<div align="center">
    <img src="./imagenes/muestreo-comparacion.png" width="70%">
</div>

**Top-k**
Limita selección a los k componentes más probables. Si k=3, elige aleatoriamente entre las 3 opciones principales.

<div align="center">
    <img src="./imagenes/top-k-ejemplo.png" width="70%">
</div>

**Top-p**
Selecciona componentes cuyas probabilidades acumuladas no excedan p. Ejemplo: p=0.32 incluye componentes con probabilidades 0.30, 0.20, 0.10, 0.02.

<div align="center">
    <img src="./imagenes/top-p-ejemplo.png" width="70%">
</div>

**Temperatura**
Controla aleatoriedad modificando distribución de probabilidad:
- **Baja (<1)**: Más conservador, concentra probabilidades
- **Alta (>1)**: Más creativo, distribuye probabilidades uniformemente  
- **1**: Mantiene distribución original del modelo

<div align="center">
    <img src="./imagenes/temperatura-comparacion.png" width="70%">
</div>

> ⚠️ **Cuidado**: Temperatura muy baja = repeticiones. Temperatura muy alta = sin sentido.

### Resumen

La ingeniería de indicaciones combina arte y ciencia para optimizar respuestas de modelos generativos. Técnicas clave: indicaciones claras, ejemplos consistentes, cadena de pensamientos, y configuración apropiada de parámetros (temperatura, top-k, top-p). Estas técnicas no modifican pesos del modelo - para personalización profunda se requiere entrenamiento específico con datos propios.