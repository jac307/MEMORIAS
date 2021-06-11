# [JSOLANG] VER

For video sampling / Para sampling de video <br/>
Parsing CineCer0 <br/>

Instructions to use this jsolang:
1. Go to [Estuary](https://estuary.mcmaster.ca/)
2. Enter in *Solo* or *Collaborative* mode.
3. Copy [jsolangVer](/esolangs/Ver/jsolangVer.peg) info on one code-box and evaluate once.
4. On second box, write: *##escuchar* on the first line. Write your code on the rest. Evaluate to run.

IMPORTANT: In both, step 3 and 4, do not choose any language in the dropdown menu. This section must be empty (empty is the option by default). <br/>

Instrucciones para usar este jsolang:
1. Ve a [Estuary](https://estuary.mcmaster.ca/)
2. Entra en modo *Solo* o en *Colaborativo*.
3. Copia la info en el [jsolangVer](/esolangs/Ver/jsolangVer.peg) en una de las cajas de texto y evalúa una vez.
4. En una segunda caja de texto, escribe: *##escuchar* en la primera línea. Escribe tu código en el resto. Evalúa para correr.

IMPORTANTE: En ambos pasos, 3 y 4, no selecciones ningúna opción delenguaje en el menú. Este debe estár vacío (esta es la opción que aparece por defecto). <br/>

____________________________________________

## Basic sentece to play sound / Oración bñasica para reproducir sonido
*verb* >> *out* | Example:  
+ `traveling >> everything ` -- plays a frequency in both channels (left-right) / reproduce una frecuencia en ambos canales (izq-der)

Options for *out* / Opciones para *out*  

| out                        | Info           |
| -------------------------- | -------------- |
| `everything`, `everything` | centre/centro  |
| `some`, `here`             | rigth/derecha  |
| `others`, `there`          | left/izquierda |

Options for *verb* / Opciones para *verb*  

| verb         | Frequencies/Frecuencias                  | verb         | Frequencies/Frecuencias                  |
| ------------ | ---------------------------------------- | ------------ | ---------------------------------------- |
| `travel`     | sin [261.626, 262.079]                   | `go`         | sin [227.652, 208.012, 228.072]          |
| `travelled`  | sin [241.626, 242.079]                   | `went`       | sin [217.652, 198.012, 218.072]          |
| `travelling` | sin [231.626, 232.079]                   | `going`      | sin [218.012, 219.012, 237.652, 238.072] |
| `move`       | sin [349.228, 349.833, 466.163]          | `gone`       | sin [207.652, 188.012, 208.072]          |
| `moved`      | sin [339.228, 339.833, 366.163]          | `quit`       | saw [161.626, 162.079]                   |
| `moving`     | sin [329.228, 329.833, 400.163]          | `quitting`   | saw [121.626, 122.079]                   |
| `sit`        | sin [110, 110.190, 195.997]              | `leave`      | tri [107.652, 188.012, 108.072]          |
| `sat`        | sin [100, 100.190, 145.997]              | `left`       | tri [117.652, 168.012, 118.072]          |
| `sitting`    | sin [100, 100.190, 125.997]              | `leaving`    | tri [100.652, 110.012, 100.072]          |
| `happen`     | saw [70, 70.190, 80.997]                 | `scape`      | tri [100.626, 110.079]                   |
| `happened`   | saw [60, 60.190, 65.997]                 | `scaped`     | tri [90.626, 102.079]                    |
| `happening`  | saw [65, 65.190, 70.997]                 | `scaping`    | tri [120.626, 180.079]                   |

## Sum frequencies / Sumar frequencias
*verb* + *and* + *verb* >> *out* | Example:  
+ `traveling and moving >> everything ` -- sum operation of two frequencies / operación que suma dos frecuencias

Only option / Única opción: `and`  

## Noun / Sustantivo
*verb* + *noun* >> *out* | Example:  
+ `traveling places >> everything ` -- multiplies the frequency by *sin 0.2* / multiplica la frecuencia por *sin 0.2*  

Options / Opciones:  

| noun      | Multiplier/Multiplicador | noun        | Multiplier/Multiplicador |
| --------- | ------------------------ | ----------- | ------------------------ |
| `travel`  | * sin 0.2                | `lights`    | * tri 0.5                |
| `sounds`  | * sin 0.5                | `images`    | * tri 0.8                |
| `noises`  | * sin 1                  | `countries` | * saw 0.2                |
| `cities`  | * tri 0.2                | `textures`  | * saw 0-5                |


## HPF, LPF: special-Verb and ing-verb / HPF, LPF: verbo-especial y verbo-ing
*special-verb* + (*verb*) + *ing-verb* >> *out* | Example:  
+ `am (traveling) feeling >> everything` -- add a high-pass-filter to a single frequency / añade un high-pass-filter a una sóla frecuencia  
*special-verb* + (*verb* + *and* + *verb*) + *ing-verb* >> *out* | Example:
+ `am (traveling and moving) feeling >> everything` -- add the filter to the couple of frequencies / añade el filtro al par de frecuencias  
*special-verb* + (*verb* + *noun*) + *ing-verb* >> *out* | Example:  
+ `am (traveling places) feeling >> everything ` -- add the filter to the multiplied frequencies / añade el filtro a las frecuencias multiplicadas  

Everything in-between the *special-verb* and the *ing-verb* must be inside parenthesis / Todo lo que está entre el *special-verb* y el *ing-verb* debe ir entre paréntesis

Options for *special-verb* / Opciones para *special-verb*  

| special-Verb   | Filter | special-Verb  | Filter |
| -------------- | ------ | ------------- | ------ |
| `am`, `are`    | hpf    | `have`, `has` | lpf    |

Options for *ing-verb* / Opciones para *ing-verb*  

| ing-verb   | Filter-Values/Valores    | ing-verb   | Filter-Values/Valores    |
| ---------- | ------------------------ | ---------- | ------------------------ |
| `hating`   | (80 ~~ 120 $ sin 1) 1    | `loving`   | (100 ~~ 120 $ sin 1) 1   |
| `liking`   | (150 ~~ 160 $ sin 1) 1   | `falling`  | (180 ~~ 200 $ sin 1) 1   |
| `running`  | (200 ~~ 250 $ sin 1) 1   | `touching` | (250 ~~ 300 $ sin 1) 1   |
| `feeling`  | (100 ~~ 120 $ sin 1) 1   | `wanting`  | (60 ~~ 140 $ sin 1) 1    |


## Volume / Volumen
*verb* + *almost* >> *out* | Example:  
+ `traveling (-15)almost >> everything ` -- lowering volume / bajando el volumen  

Only option / Única opción: `almost`  
Must have a value before; negative numbers inside parenthesis  / Debe tener un valor antes; números negativos van en paréntesis  

## Numbers / Números
*verb* + *almost* >> *out* <> *number* | Example:  
+ `traveling (-15)almost >> everything <> _cinco ` -- when eval, this sound will fade-in in 5 seconds / cuando se evalúa, este sonido aparecerá en cinco segundos  

Options / Opciones  

| number     | Seconds |
| ---------- | ------- |
| `_cinco`   | 5       |
| `_diez`    | 10      |
| `_quince`  | 15      |
| `_veinte`  | 20      |

## Sentece to silence everything / Oración para silenciar todo
+ `silence` -- evaluate just this word / evalúa únicamente esta palabra

## Empty string / String vacíos
This is a list of words that can be added in-between words that produce an empty string.  
Esta es una lista de palabras que pueden ser añadidas entre palabras y producen un string vacío  

`I`, `They`, `Places`, `Sounds`, `Cities` | Example:  
+ `I am traveling feeling >> everything`  

## Multiple sentences / Oraciones múltiples
To add multiple sentences, these are divided by `;` (semicolon) / Para añadir oraciones múltiples, éstas van separadas por `.` (punto) | Example:  
+ `I am traveling feeling >> some; I have traveled running >> others`
