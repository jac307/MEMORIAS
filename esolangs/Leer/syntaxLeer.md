# LEER

For speech patters in Spanish / Para patrones de voz en Español  
Parsing Tidal Cycles  

This [esolang](https://github.com/jac307/estuary/blob/master/client/src/Estuary/Languages/TiempoEspacio/Leer.hs) can be accesed through [Estuary](https://estuary.mcmaster.ca/), just look for it on the language's dropdown menu.  

Este [esolang](https://github.com/jac307/estuary/blob/master/client/src/Estuary/Languages/TiempoEspacio/Leer.hs) puede ser accesado a través de [Estuary](https://estuary.mcmaster.ca/), busca en el menú de opciones.  

____________________________________________

## Syntax / Sintaxis

This syntax uses words and structures in English / Esta sintaxis usa palabras y estructuras en Inglés.  

## Basic sentece to produce sound: Verb / Oración básica para producir sonido: Verbo
*verb* | Example:   
+ `hear` -- plays the first sample of the "oir" folder / reproduce el primer sample del folder "oir".

Options/Opciones:

| verb                                             | Files | Info                                                    |
| ------------------------------------------------ | ----- | ------------------------------------------------------- |
| `hear`, `hears`, `hearing`, `heard`              | 31    | plays [oir-folder](/samples/audioSamples/oir)           |
| `write`, `writes`, `writing`, `wrote`, `written` | 39    | plays [escribir-folder](/samples/audioSamples/escribir) |
| `watch`, `watches`, `watching`, `watched`        | 32    | plays [observar-folder](/samples/audioSamples/observar) |
| `read`, `reads`, `reading`                       | 18    | plays [leer-folder](/samples/audioSamples/leer)         |
| `see`, `sees`, `seeing`, `saw`, `seen`           | 20    | plays [ver-folder](/samples/audioSamples/ver)           |
| `listen`, `listens`, `listening`, `listened`     | 30    | plays [escuchar-folder](/samples/audioSamples/escuchar) |

## Changing the sample number / Cabiando el número de sample
*verb:#* | Example:  
+ `hear:2` -- plays the third sample (starting from 0) of the "oir" folder / reproduce el tercer sample (contando desde 0) del folder "oir".

You can access this [pdf file](/samples/audioSamples/MEMORIAS_audioSamples.pdf) for specific information about file number and the part of the sentence (of this story) that is played. / Puedes acceder a este [archivo pdf](/samples/audioSamples/MEMORIAS_audioSamples.pdf) para información específica sobre el número de archivo y las oraciones (de cada historia) que cada uno reproduce.

## Other variations for the basic sentence / Otras variaciones de oración básica
+ *verb verb verb* | Example: `hear reading listens` -- plays three samples in one cycle / reproduce tres samples en un ciclo. Cycle/ciclo=1seg
+ _verb*2 verb_ | Example: `hear*2 reading` -- plays te first sample twice / reproduce el primer sample dos veces
+ *verb <verb:# verb:#>* | Example: `hear <read:2 listen:3>` -- in one cycle plays `hear` and `read:2`, in the next cycle plays `hear` and `listen:3`; repeats / en un ciclo reproduce `hear` y `read:2`, en el siguiente ciclo reproduce `hear` y `listen:3`; se repite
+ *verb [verb:# verb:#]* | Example: `hear [read:2 listen:3]` -- divides the cicle in two: first part plays `hear`, in the second part plays `listen:3` and `read:2` / divide el ciclo en dos: en la primera parte reproduce `hear`, en la segunda parte reproduce `listen:3` y `read:2`
+ _[verb verb]*2_ | Example: `[read:2 listen:3]*2` -- plays both samples in double the time of the cycle / reproduce ambos samples en el doble del tiempo del ciclo
+ *[verb verb]/2* | Example: `[read:2 listen:3]/2` -- plays both samples in half the time of the cycle / reproduce ambos samples en la mitad del tiempo del ciclo
+ *verb empty verb* | Example: `read did watch` -- divides the cicle in three, the second space is empty / divide el ciclo en tres, el tercer espacio está vacío

Options for empty-space / Opciones para espacio vacío: `am`, `is`, `are`, `was`, `were`, `do`, `does`, `did`, `not`

## Sentece to silence everything / Oración para silenciar todo
+ `silence` -- evaluate just this word / evalúa únicamente esta palabra

## Tranformations 1: pre-verb / Transformaciones 1: previas al verbo

### Numbers / Números
*number* + *verb* | Example:  
+ `one_ hear hear:2` -- plays left and right channels. Must have two or more samples / reproduce en los canales izquierda y derecha. Debe tener más de dos samples.

Opciones / Options:  

| numbers                   | Info                                                                                 |
| ------------------------- | ------------------------------------------------------------------------------------ |
| `one_`, `two_`, `three_`  | plays left and right / reproduce izquierda y derecha                                 |
| `four_`, `five_`, `six_`  | needs a value (double), from then it pans / necesita un valor (doble), de ahí panea  |

+ `one_ hearing listening*3`
+ `four_ (0.2) hearing listening*3`

### Pronouns / Pronombres
*number* + *pronoun* + *verb* | Example:  
+ `one_ I(8) hear*8` -- acepts int. Makes a granulation efect cutting the samples in the value that is given / acepta un entero. Hace un efecto de granulación cortando los samples en el valor que le des.

Options / Opciones: `I`, `We`, `we`, `They`, `they`  

+ `We(18) <hearing*4 listening*4> watching*2`
+ `They(4) hear watch did listen not reading`

### Preference Verbs / Verbos de gusto
*numbers* + *pronoun* + *preference-verb* + *verb* | Example:  
+ `wanted(2.0) hearing listening not watching:5`  -- slows the cycle half the time / alenta el ciclo a mitad del tiempo  

Options / Opciones:  

| Preference-verb            | Info                                                                          |
| -------------------------- | ----------------------------------------------------------------------------- |
| `want`, `wants`, `wanted`  | slows a value(double) the whole cycle / alenta un valor(doble) todo el ciclo  |
| `like`, `likes`, `liked`   | fast a value(double) the whole cycle / fast un valor(doble) todo el ciclo     |

### Adverbs / Adverbios
*numbers* + *pronoun* + [*adverb* + *preference-verb*] + *verb* | Example:  
+ `sometimes(4) wanted(2.0) hearing listening not watching:5`  -- slows just every 4 cycles / alenta únicamente cada 4 ciclos

Options / Opciones: `always`, `Sometimes`, `sometimes`, `Often`, `often`, `rarely`  

## Tranformations 2: post-verb / Transformaciones 2: posteriores al verbo

### ing-verb(o)s
*Verb* + *ing-verb* | Examples:  
+ `hears multiplying(20)` -- plays a random sample of the *oir-folder* up to its 20th file (int value) / reproduce un sample de manera aleatoria del *folder-oir* hasta su archivo 20 (valor int)  
+ `hears watches multiplying(20)` -- same but now with two folder-samples / lo mismo pero ahora con dos folders the samples.  

Options / Opciones: `multiplying`, `imagining`, `swinging`, `lying`  

### Noun / Sustantivos
*verb* + *ing-verb* + *nouns* | Examples:  
+ `hears multiplying(20) lights(1.3)` -- highest the volume / sube el volumen
+ `hears watches multiplying(20) lights(1.3 0.8)` -- highest the volume of the first sample, lowest the volume of the second / sube el volumen del primer sample, baja el volumen del segundo

Options (all must have a double-value in parentesis) / Opciones (todos deben tener un valor-doble en paréntesis):  

| sustantivos        | Info                                           |
| ------------------ | ---------------------------------------------- |
| `sound`, `sounds`  | pitch: ++ high/agudo, --low/grave, 0=normal    |
| `light`, `lights`  | volume/volumen: 0.0 - 2.0, 1.0=normal          |
| `door`, `doors`    | pan(eo): 0.0=left/izq - 1.0=right/der          |
| `time`, `times`    | delay: 0.0=none/sin - 1.0                      |
| `space`, `spaces`  | delayfeedbak: 0.0=none/sin - 1.0               |
| `room`, `rooms`    | delaytime: 0.0=none/sin - 1.0                  |
| `word`, `words`    | cuts the begining / corta el inicio: 0.0 - 1.0 |
| `vowel`, `vowels`  | cuts the end / corta el final: 0.0 - 1.0       |
| `Fench`            | efecto/effect 1, no-value/sin-valor            |
| `English`          | efecto/effect 2, no-value/sin-valor            |
| `books`            | efecto/effect 3, no-value/sin-valor            |
| `bus`              | efecto/effect 4, no-value/sin-valor            |
| `swing`            | efecto/effect 5, no-value/sin-valor            |

Multiple nouns can be added (up to 5) / Multiples sustantivos pueden ser añadido (hasta 5)  

## Empty string / String vacíos
This is a list of words that can be added in-between words that produce an empty string.  
Esta es una lista de palabras que pueden ser añadidas entre palabras y producen un string vacío  

`myself`, `on`, `in`, `that`, `The`, `the`, `to`, `with`, `everything`, `anything`, `suspended`, `without`, `through`, `Through`, `down` | Example:  
+ `wanted(2.0) to hear listening not watching suspended multiplying (35) spaces (1) without sounds (-0.2)`

## Multiple sentences / Oraciones múltiples
To add multiple sentences, these are divided by `.` (dot) / Para añadir oraciones múltiples, éstas van separadas por `.` (punto) | Example:  
+ `hears multiplying(20) lights(1.3). watching*2 sounds (0.5) doors (0.0 1.0)`
