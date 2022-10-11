[back / regresar](README.md)   
[Esolangs](../README.md)   
[Home](../../README.md)  
------------------------------------------------------------------------------- 

# [JSOLANG] ESCUCHAR

For sound synthesis / Para síntesis sonora <br/>
Parsing Punctual <br/>

Instructions to use this jsolang:
1. Go to [Estuary](https://estuary.mcmaster.ca/)
2. Enter in *Solo* or *Collaborative* mode.
3. Copy [jsolangEscuchar](/esolangs/Escuchar/jsolangEscuchar.peg) info on one code-box and evaluate once.
4. On second box, write: *##escuchar* on the first line. Write your code on the rest. Evaluate to run.

IMPORTANT: In both, step 3 and 4, do not choose any language in the dropdown menu. This section must be empty (empty is the option by default). <br/>

Instrucciones para usar este jsolang:
1. Ve a [Estuary](https://estuary.mcmaster.ca/)
2. Entra en modo *Solo* o en *Colaborativo*.
3. Copia la info en el [jsolangEscuchar](/esolangs/Escuchar/jsolangEscuchar.peg) en una de las cajas de texto y evalúa una vez.
4. En una segunda caja de texto, escribe: *##escuchar* en la primera línea. Escribe tu código en el resto. Evalúa para correr.

IMPORTANTE: En ambos pasos, 3 y 4, no selecciones ningúna opción delenguaje en el menú. Este debe estár vacío (esta es la opción que aparece por defecto). <br/>

____________________________________________

## Syntax / Sintaxis

This syntax uses words and structures in Spanish / Esta sintaxis usa palabras y estructuras en Español.

## Basic sentece to play a video: Noun / Oración básica para reproducir un video: Suntantivo
*textos:* *sustantivo* | Example:   
+ `textos(aguas)` -- plays the video linked to this word / reproduce el video que está ligado a esta palabra.

To play videos, `textos` must be before the noun / Para reproducir videos, `textos` siempre debe ir antes del sustantivo.    

Options for *sustantivo* / Opciones para *sustantivo*:  

| sustantivos  | Video-still                                                                      | sustantivos  | Video-still                                                                                |
| ------------ | -------------------------------------------------------------------------------- | ------------ | ----------------------------------------------------------------------------------------- |
| `cuartos`    | <img src="https://jac307.github.io/MEMORIAS/img/cuartos-still.jpg" width="300">  | `aguas`      | <img src="https://jac307.github.io/MEMORIAS/img/aguas-still.jpg" width="300">     |
| `sonidos`    | <img src="https://jac307.github.io/MEMORIAS/img/sonidos-still.jpg" width="300">  | `cigarras`   | <img src="https://jac307.github.io/MEMORIAS/img/cigarras-still.jpg" width="300">  |
| `veranos`    | <img src="https://jac307.github.io/MEMORIAS/img/veranos-still.jpg" width="300">  | `cellos`     | <img src="https://jac307.github.io/MEMORIAS/img/cellos-still.jpg" width="300">    |
| `imágenes`   | <img src="https://jac307.github.io/MEMORIAS/img/imagenes-still.jpg" width="300"> | `noches`     | <img src="https://jac307.github.io/MEMORIAS/img/noches-still.jpg" width="300">    |


## Time for videos / Time para videos
*time* $ *imágenes:* *sustantivo* | Example:   
+ `Hoy 1 0.8 $ aguas` -- changes frame-rate fo the video / cambia el frame rate del video

Options / Opciones: `Ayer`, `Hoy`  
Must have two values: Dur Offset / Debe tener dos parámetros: Dur Offset  


## Verb ser-estar for videos / Verbo ser-estar para videos  
*time* $ *verboSerEstar* $ *imágenes:* *sustantivo* | Example:  
+ `estoy 0.5 $ textos(aguas)` -- creates a circle mask / crea una máscara circular  

Options / Opciones:  

| verboSerEstar | Mask-Info                                                                              |
| ------------- | -------------------------------------------------------------------------------------- |
| `estoy`       | circular, 1-value/valor: size/tamaño; 0.0 - 1.0                                        |
| `estamos`     | circular-2, 2-values/valores: size,anchor-point / tamaño-anclaje; 0.0 - 1.0            |
| `estábamos`   | cuadrada, 1-value/valor: size/tamaño; 0.0 - 1.0                                        |
| `estoy`       | rectangular: 4-values/valores: top,right,bottom,left / arriba,der,abajo,izq; 0.0 - 1.0 |

Negative numbers inside parenthesis  / Los números negativos van en paréntesis  


## Basic sentece to visualize text / Oración básica para visualizar texto
*imágenes:* *""* | Example:   
+ `imagen("I am here, alone")`  

For text, `imagen` must be written before the text you want to visualize. This text should be written inside quotation marks `"my text"`  
Para texto, `imagen` debe de estar escrito antes del texto que se quiere visualizar. Este texto debe ir entre comillas `"my text"`    


## Verb: for video & text / Verbo: para video & texto
*verbo* $ *textos:* *sustantivo* | Example:   
+ `haciendo 0.5 $ textos(aguas)` -- changes the size of the video / cambia el tamaño del video

*verbo* $ *imágenes:* *""* | Example:   
+ `atravezando 5 $ imagen("I am here, alone")` -- changes the size of the text / cambia el tamaño del texto

Options / Opciones:  

| verbos        | Apply-in /Aplicado-en | Info                                                     |
| ------------- | --------------------- | -------------------------------------------------------- |
| `sentada`     | videos, text(o)       | coord: 2-values/valores: x,y; (-1.0) - 1.0               |
| `escuchando`  | videos, text(o)       | pos-X: 1-value/valor: (-1.0) - 1.0                       |
| `recordando`  | videos, text(o)       | pos-Y: 1-value/valor: (-1.0) - 1.0                       |
| `haciendo`    | videos                | size/tam: 1-value/valor: 1++=bigger, --1=smaller         |
| `tocando`     | videos                | width/ancho: 1-value/valor: 1++=bigger, --1=smaller      |
| `imaginando`  | videos                | height/alto: 1-value/valor: 1++=bigger, --1=smaller      |
| `atravezando` | text                  | size/tam: 1-value/valor: 1++                             |
| `soñando`     | text                  | font: 1-string: `"name-nombre"`                          |


## Adjective: for video & text / Adjetivo: para video & texto
*verbo* $ *adjetivos* $ *textos:* *sustantivo* | Example:   
+ `tempestuosas 0.5 $ haciendo 0.5 $ textos(aguas)` -- changes the brightness of the video / cambia el brillo del video

*verbo* $ *adjetivos* $ *imágenes:* *""* | Example:   
+ `ruidosas $ atravezando 5 $ imagen("I am here, alone")` -- text in bold / texto en negritas

Options / Opciones:  

| adjectivos      | Apply-in /Aplicado-en | Info                                                      |
| --------------- | --------------------- | --------------------------------------------------------- |
| `tempestuosas`  | videos                | brightness/brillo: 1-value/valor: 1++=more, --1=less      |
| `transformadas` | videos                | blur: 1-value/valor: 1++=more, --1=less                   |
| `extrañas`      | videos                | opacity/opacidad: 1-value/valor: 0.0 - 1, 1=none/sin      |
| `diferentes`    | videos                | contrast(e): 1-value/valor: 1++=more, --1=less            |
| `oscuras`       | videos                | grayscale: 1-value/valor: 1++=more, --1=less              |
| `fuertes`       | text                  | rgba: 4-values/valores, each channel: 0.0 - 1, 0=none/sin |
| `aprendidas`    | text                  | strike/tachado: no value/valor                            |
| `ruidosas`      | text                  | bold/negritas: no value/valor                             |
| `silenciosas`   | text                  | italic(as): no value/valor                                |

## Special adjectives: dynamic values / Adjetivos especiales: valores dinámicos
They can be used in any function in replacement of a single value. They must be written inside parenthesis.
Pueden ser usados en cualquier función reemplazando un valor único. Deben ser escritos dentro de paréntesis.

### Option 1 / Opción 1
(*rápidas*)

| adj-esp-1      | Values                                    | Info                                                        |
| -------------- | ----------------------------------------- | ----------------------------------------------------------- |
| `rápidas`      | cycles(time) initial-value end-value      | in an specific time, it animates from one value to another  |
| `rápidas`      | ciclos(tiempo) valor-inicial valor-final  | en un tiempo específico, anima de un valor a otro           |

Examples:  
+ `tempestuosas (rápidas 5 0 1) $ haciendo 0.5 $ textos(aguas)` -- the brightness changes in 5 cycles / el brillo cambia en 5 ciclos
+ `ruidosas $ atravezando (rápidas 10 1 10) $ imagen("I am here, alone")"` -- text grows in 5 cycles / el texto crece en 5 ciclos


### Option 2 / Opción 2
(*lejanas* $ *claras*) -- These always go together / siempre van juntos

| adj-esp-2     | Values       | Info                                                        |
| ------------- | ------------ | ----------------------------------------------------------- |
| `lejanas`     | val-1 val-2  | comes and go / va y viene                                   |
| `claras`      | freq         | velocity of animation / velocidad de la animación           |

Examples:  
+ `tempestuosas (lejanas 0 1 $ claras 0.5) $ haciendo 0.5 $ textos(aguas)` -- brightness go up and down / el brillo sube y baja
+ `ruidosas $ atravezando (lejanas 1 10 $ claras 0.1) $ imagen("I am here, alone")` -- text goes bigger and smaller / el texto se agranda y se achica  

## Sentece to silence everything / Oración para silenciar todo
+ `silencio` -- evaluate just this word / evalúa únicamente esta palabra  

## Multiple sentences / Oraciones múltiples
To add multiple sentences, these are divided by `;` (semicolon) / Para añadir oraciones múltiples, éstas van separadas por `.` (punto) | Example:  
+ `tempestuosas (lejanas 0 1 $ claras 0.2) $ haciendo 0.5 $ textos(aguas); ruidosas $ atravezando (lejanas 1 10 $ claras 0.1) $ imagen("I am here, alone")`
