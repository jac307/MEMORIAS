# [JSOLANG] OIR

For visual synthesis / Para síntesis visual <br/>
Parsing Hydra <br/>

Instructions to use this jsolang:
1. Go to [Estuary](https://estuary.mcmaster.ca/)
2. Enter in *Solo* or *Collaborative* mode.
3. Copy [jsolangOir](/esolangs/Oir/jsolangOir.peg) info on one code-box and evaluate once.
4. On second box, write: *##escuchar* on the first line. Write your code on the rest. Evaluate to run.

IMPORTANT: In both, step 3 and 4, do not choose any language in the dropdown menu. This section must be empty (empty is the option by default). <br/>

Instrucciones para usar este jsolang:
1. Ve a [Estuary](https://estuary.mcmaster.ca/)
2. Entra en modo *Solo* o en *Colaborativo*.
3. Copia la info en el [jsolangOir](/esolangs/Oir/jsolangOir.peg) en una de las cajas de texto y evalúa una vez.
4. En una segunda caja de texto, escribe: *##escuchar* en la primera línea. Escribe tu código en el resto. Evalúa para correr.

IMPORTANTE: En ambos pasos, 3 y 4, no selecciones ningúna opción delenguaje en el menú. Este debe estár vacío (esta es la opción que aparece por defecto). <br/>

____________________________________________

## Syntax / Sintaxis

This syntax uses words and structures in English / Esta sintaxis usa palabras y estructuras en Inglés.  


## Sentece to import multimedia sources / Oración para importat fuentes multimedia

*Verb(o) to-be* + *adjective/adjetivo* | Examples:  
+ `am.vanished()` -- imports a screen as source-0 / importa la pantalla en la souce-0

Options/Opciones:  

| V to-be  | Description   | Adjective/Adjetivo  | Description          |
| -------- | ------------  | ------------------  | -------------------  |
| `am`     | source-0      | `.vanished()`       | import(ar) Screen    |
| `are`    | source-1      | `.opened()`         | import(ar) Video     |
| `arenT`  | source-2      | `.crushed()`        | import(ar) Cam       |
| `amNot`  | source-3      | `.disappeared()`    | import(ar) Image(n)  |

+ `.crushed()`
Imports the default camera in your system. To import others you can add a number inside parentesis as a parameter: / Importa la cámara por defecto del sistema. Para importar otras debes añadir un número dentro de los paréntesis:  
+ `.crushed(1)`.

+ `.disappeared()` and `.opened()`
These need an extra parameter, the URL of the image or video in quotation marks inside the parentesis: / Estas funciones necesitan un parametro extra, la URL de la imagen o el video entre comillas y dentro de los paréntesis:  
+ `.opened("/myURL.mov")`


## Basic sentence to visualice source / Oración básica para visualizar source

*Subject/Sujeto(Verb(o) to-be)* + *out/salida* | Examples:  
+ `am.vanished(); I(am).over` -- visualizes imported screen / visualiza la pantalla importada

Options/Opciones:  

| Subject   | Out/Salida  |
| --------- | ----------- |
| `I()`     | `.over()`   |
| `They()`  | `.out()`    |

The verb to-be used to import must be set as parameter of the subject, written inside parentesis. Both sentences are separated by semicolon *;*  

El verbo to be usado para importar debe ser usado como parámetro en el sujeto, escrito dentro de los paréntesis. Ambas oraciones van separadas por un punto y coma *;*  


## Sentence to go to black / Oración para ir a negros
+ `silence().over` or `silence().out`
