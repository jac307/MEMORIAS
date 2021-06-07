# [JSOLANG] OIR

For visual synthesis / Para síntesis visual  
Parsing Hydra  

Instructions to use this jsolang:
1. Go to [Estuary](https://estuary.mcmaster.ca/)
2. Enter in *Solo* or *Collaborative* mode.
3. Copy [jsolangOir](/esolangs/Oir/jsolangOir.peg) info on one code-box and evaluate once.
4. On second box, write: *##escuchar* on the first line. Write your code on the rest. Evaluate to run.

IMPORTANT: In both, step 3 and 4, do not choose any language in the dropdown menu. This section must be empty (empty is the option by default).  

Instrucciones para usar este jsolang:
1. Ve a [Estuary](https://estuary.mcmaster.ca/)
2. Entra en modo *Solo* o en *Colaborativo*.
3. Copia la info en el [jsolangOir](/esolangs/Oir/jsolangOir.peg) en una de las cajas de texto y evalúa una vez.
4. En una segunda caja de texto, escribe: *##escuchar* en la primera línea. Escribe tu código en el resto. Evalúa para correr.

IMPORTANTE: En ambos pasos, 3 y 4, no selecciones ningúna opción delenguaje en el menú. Este debe estár vacío (esta es la opción que aparece por defecto).  

____________________________________________

## Syntax / Sintaxis

This syntax uses words and structures in English / Esta sintaxis usa palabras y estructuras en Inglés.  


## Sentece to import multimedia sources / Oración para importar fuentes multimedia
*Verb(o) to-be* + *verb(o)-1* | Example:  
+ `am.vanished()` -- imports a screen as source-0 / importa la pantalla en la souce-0

Options/Opciones:  

| V to-be            | Info      | Verb(o)-1                          | Info                |
| ------------------ | --------- | ---------------------------------- | ------------------- |
| `am` or `are`      | source-0  | `.vanish()` or `.vanished()`       | import(ar) Screen   |
| `do` or `did`      | source-1  | `.open()` or `.opened()`           | import(ar) Video    |
| `arenT` or `amNot` | source-2  | `.crush()` or `.crushed()`         | import(ar) Cam      |
| `donT` or `didnT`  | source-3  | `.disappear()` or `.disappeared()` | import(ar) Image(n) |

+ `.crushed()`. Imports the default camera in your system. To import others you can add a number inside parentesis as a parameter: / Importa la cámara por defecto del sistema. Para importar otras debes añadir un número dentro de los paréntesis: `.crushed(1)`.

+ `.disappear()` and `.open()`. These need an extra parameter, the URL of the image or video in quotation marks inside the parentesis: / Estas funciones necesitan un parametro extra, la URL de la imagen o el video entre comillas y dentro de los paréntesis: `did.open("/myURL.mov")`


## Basic sentence to visualice source / Oración básica para visualizar source
*Subject/Sujeto(Verb(o) to-be)* + *out/salida* | Example:  
+ `am.vanished(); I(am).over()` -- visualizes imported screen / visualiza la pantalla importada  

Options/Opciones:  

| Subject   | Out/Salida  |
| --------- | ----------- |
| `I()`     | `.over()`   |
| `They()`  | `.out()`    |

The verb to-be used to import must be set as parameter of the subject, written inside parentesis. Both sentences are separated by semicolon: *;*  

El verbo to be usado para importar debe ser usado como parámetro en el sujeto, escrito dentro de los paréntesis. Ambas oraciones van separadas por un punto y coma: *;*  

## Sentence to go to black / Oración para ir a negros
+ `silence().over` or `silence().out`


## Transform source / Transformar fuente
Once you have a basic sentence, you can start adding transformations. These are nested between the Subject and the Out. / Una vez que tienes la oración básica puede empezar a añadir transformaciones. Estas van entre el Sujeto y la salida.  
*Subject/Sujeto(Verb(o) to-be)* + **LIST OF TRANSFORMATIONS** + *out/salida*

### Verb(o)s
*Subject/Sujeto(Verb(o) to-be)* + *verb(o)s-2* + *out/salida* | Example:  
+ `I(am).dreaming().over()` -- modify brightness / modifica el brillo

Options/Opciones:

| verb(o)-2                         | Info            |
| --------------------------------- | ---------------------------------- |
| `.dream()` or `.dreaming()`       | brightness/brillo (value/valor)    |
| `.swallow()` or `.swallowing()`   | contrast/contraste (value)         |
| `.scream()` or `.screaming()`     | pixelate/pixelado (value,value)    |
| `.run()` or `.running()`          | rotate/rotar (value)               |
| `.play()` or `.playing()`         | scale/escalar (value,value)        |
| `.have()` or `.having()`          | saturate/saturar (value)           |
| `.shine()` or `.shinning()`       | scrollX/desplazoX (value)          |
| `.miss()` or `.missing()`         | scrollY/desplazoY (value)          |

+ `I(am).dreaming().over()`. Changes the brightness will the default value, to change this default you add a valor. / Cambie el brillo con el valor por defecto, si quieres cambiar éste debes añadir un valor: `I(am).dreaming(0.5).over()`  

+ `I(am).playing(0.5,0.5).out()`. Some functions have two values, these must be separated with comma. / Algunas funciones tienen dos valores, éstos deben ir separados por comas.  

You can add as many verbs as you want: / Puedes añadir los verbos que quieras:  
+ `I(am).playing().missing().out()`
+ `They(did).run().playing(1,10).having(0.2).over()`

### Nouns / Sustantivos
*Subject/Sujeto(Verb(o) to-be)* + *verb(o)s-2* + *nouns/sust(various-words)* *out/salida* | Example:  
+ `I(am).dreaming().oceans(all).over()` -- this add a modulator / esto añade un modulador

Options/Opciones:  

| nouns/sust   | Info               | nouns/sust   | Info               |
| ------------ | ------------------ | ------------ | ------------------ |
| `.oceans()`  | modulate           | `.voices()`  | modulate scale     |
| `.songs()`   | modulate pixels    | `.sand()`    | modulate scrollX   |
| `.skies()`   | modulate rotation  | `.beds()`    | modulate scrollY   |
| `.deaths()`  | add/añadir         | `.noises()`  | layer/capa         |
| `.tales()`   | diff/diferencia    | `.mouths()`  | mult               |

Each of these functions has different amount of parameters but the first one is always the same: *various-words*. / Estas funciones tiene tienen differente cantidad de parámetros pero el primero siempre es el mismo: *various-words*  

| Various-words | Info          | Various-words | Info          |
| ------------- | ------------- | ------------- | ------------- |
| `all`         | out/salida-0  | `whole`       | out/salida-2  |
| `any`         | out/salida-1  | `vast`        | out/salida-3  |

These parameter is connected to *out/salida()*. By default, the value is out-0, so this can be use as a parameter in nouns. / Este parámetro está conectado con  *out/salida()*. Por defecto el valor es salida-0, este parámetro puede usarse también como valor en los sustantivos.  

Examples: Ejemplos:
+ `I(am).playing().missing().voices(all,100).mouths(all).out()`
+ `They(did).run().playing(1,10).having(0.2).mouths(whole).over(whole)`
