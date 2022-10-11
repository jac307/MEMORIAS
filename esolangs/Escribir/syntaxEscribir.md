[back / regresar](../README.md)  
[Home](../../README.md)  
------------------------------------------------------------------------------- 

# ESCRIBIR

For speech patters in English / Para patrones de voz en Inglés <br/>
Parsing Tidal Cycles.  

This [esolang](https://github.com/dktr0/estuary/blob/dev/client/src/Estuary/Languages/TiempoEspacio/Escribir.hs) can be accesed through [Estuary](https://estuary.mcmaster.ca/), just look for it on the language's dropdown menu.  

Este [esolang](https://github.com/dktr0/estuary/blob/dev/client/src/Estuary/Languages/TiempoEspacio/Escribir.hs) puede ser accesado a través de [Estuary](https://estuary.mcmaster.ca/), busca en el menú de opciones.  

____________________________________________

# Syntax / Sintaxis

This syntax uses words and structures in Spanish / Esta sintaxis usa palabras y estructuras en Español.  

## Basic sentece to produce sound: Verb / Oración básica para producir sonido: Verbo
*verbo* | Example:   
+ `oir` -- plays the first sample of the "hear" folder / reproduce el primer sample del folder "hear".

Options/Opciones:

| verbo                                                   | Files | Info                                                    |
| ------------------------------------------------------- | ----- | ------------------------------------------------------- |
| `oir`, `oigo`, `oyen`, `oye`, `oí`                      | 32    | plays [hear-folder](/samples/audioSamples/hear)         |
| `escribir`, `escribo`, `escriben`, `escribe`, `escribí` | 28    | plays [write-folder](/samples/audioSamples/write)       |
| `observar`, `observo`, `observan`, `observa`, `observé` | 38    | plays [watch-folder](/samples/audioSamples/watch)       |
| `leer`, `leo`, `leen`, `lee`, `leí`                     | 27    | plays [read-folder](/samples/audioSamples/read)         |
| `ver`, `veo`, `ven`, `ve`, `ví`                         | 19    | plays [see-folder](/samples/audioSamples/see)           |
| `escuchar`, `escucho`, `escucha`, `escuché`             | 28    | plays [listen-folder](/samples/audioSamples/listen)     |

## Changing the sample number / Cabiando el número de sample
*verbo:#* | Example:  
+ `oir:2` -- plays the third sample (starting from 0) of the "hear" folder / reproduce el tercer sample (contando desde 0) del folder "hear".

You can access this [pdf file](/samples/audioSamples/MEMORIAS_audioSamples.pdf) for specific information about file number and the part of the sentence (of this story) that is played. / Puedes acceder a este [archivo pdf](/samples/audioSamples/MEMORIAS_audioSamples.pdf) para información específica sobre el número de archivo y las oraciones (de cada historia) que cada uno reproduce.

## Other variations for the basic sentence / Otras variaciones de oración básica
+ *verbo verbo verbo* | Example: `oigo observo escucho` -- plays three samples in one cycle / reproduce tres samples en un ciclo. Cycle/ciclo=1seg
+ _verbo*2 verbo_ | Example: `oir*2 leer` -- plays te first sample twice / reproduce el primer sample dos veces
+ *verbo <verbo:# verbo:#>* | Example: `oigo <leo:2 escucho:3>` -- in one cycle plays `oigo` and `leo:2`, in the next cycle plays `oigo` and `escucho:3`; repeats / en un ciclo reproduce `oigo` y `leo:2`, en el siguiente ciclo reproduce `oigo` y `escucho:3`; se repite
+ *verbo [verbo:# verbo:#]* | Example: `oir [leer:2 escuchar:3]` -- divides the cicle in two: first part plays `oir`, in the second part plays `leer:3` and `escuchar:2` / divide el ciclo en dos: en la primera parte reproduce `oir`, en la segunda parte reproduce `leer:3` y `escuchar:2`
+ _[verbo verbo]*2_ | Example: `[leí:2 escuché:3]*2` -- plays both samples in double the time of the cycle / reproduce ambos samples en el doble del tiempo del ciclo
+ *[verbo verbo]/2* | Example: `[leer:2 ver:3]/2` -- plays both samples in half the time of the cycle / reproduce ambos samples en la mitad del tiempo del ciclo
+ *verbo empty verbo* | Example: `ví no escuché` -- divides the cicle in three, the second space is empty / divide el ciclo en tres, el tercer espacio está vacío

Options for empty-space / Opciones para espacio vacío: `me`, `que`, `no`, `se`  

## Sentece to silence everything / Oración para silenciar todo
+ `silencio` -- evaluate just this word / evalúa únicamente esta palabra

## Tranformations 1: pre-verb / Transformaciones 1: previas al verbo

### Numbers / Números
*número* + *verbo* | Example:  
+ `uno_ oir:0 oir:2` -- plays left and right channels. Must have two or more samples / reproduce en los canales izquierda y derecha. Debe tener más de dos samples.

Opciones / Options:  

| numbers                      | Info                                                                                 |
| ---------------------------- | ------------------------------------------------------------------------------------ |
| `uno_`, `dos_`, `tres_`      | plays left and right / reproduce izquierda y derecha                                 |
| `cuatro_`, `cinco_`, `seis_` | needs a value (double), from then it pans / necesita un valor (doble), de ahí panea  |

+ `uno_ oyen escuchan*3`
+ `cuatro_ (0.2) oyen escuchan*3`

### Article / Artículo
*número* + *artículo* + *verbo* | Example:  
+ `uno_ El(8) escucha*8` -- acepts int. Makes a granulation efect cutting the samples in the value that is given / acepta un entero. Hace un efecto de granulación cortando los samples en el valor que le des.

Options / Opciones: `La`, `Las`, `la`, `las`, `El`, `el`, `Los`, `los`  

+ `Los(18) <escuchan*4 oyen*4> ven*2`
+ `El(4) ve escucha que oyen no observan`

### Preference Verbs / Verbos de gusto
*número* + *artículo* + *verbo-de-gusto* + *verbo* | Example:  
+ `amo(2.0) escuchar oir no ver:5`  -- slows the cycle half the time / alenta el ciclo a mitad del tiempo  

Options / Opciones:  

| Preference-verb                                      | Info                                                                          |
| ---------------------------------------------------- | ----------------------------------------------------------------------------- |
| `Amo`, `amo`, `ama`, `aman`, `amaba`, `amaban`       | slows a value(double) the whole cycle / alenta un valor(doble) todo el ciclo  |
| `Odio`, `odio`, `odia`, `odian`, `odiaba`, `odiaban` | fast a value(double) the whole cycle / fast un valor(doble) todo el ciclo     |

### Subject / Subjeto
*número* + *artículo* + [*sujeto* + *verbo-de-gusto*] + *verbo* | Example:  
+ `Palabras(4) aman(2.0) oir escuchar no escribir:5`  -- slows just every 4 cycles / alenta únicamente cada 4 ciclos

Options / Opciones: `Palabra`, `Palabras`, `Dedo`, `Dedos`, `Idioma`, `Idiomas`  

## Tranformations 2: post-verb / Transformaciones 2: posteriores al verbo

### Adjectives / Adjetivos
*verbo* + *adjetivo* | Examples:  
+ `oir vívidas(20)` -- plays a random sample of the *hear-folder* up to its 20th file (int value) / reproduce un sample de manera aleatoria del *folder-hear* hasta su archivo 20 (valor int)  
+ `oir ver vívidas(20)` -- same but now with two folder-samples / lo mismo pero ahora con dos folders the samples.  

Options / Opciones: `vívida`, `vívidas`, `vívido`, `vívidos`, `presurosa`, `presurosas`, `presuroso`, `presurosos`, `ansiosa`, `ansiosas`, `ansioso`, `ansiosos`  

### Noun / Sustantivos
*verbo* + *adjetivo* + *sustantivos* | Examples:  
+ `oir vívidas(20) formas(1.3)` -- highest the volume / sube el volumen
+ `oir ver vívidas(20) formas(1.3 0.8)` -- highest the volume of the first sample, lowest the volume of the second / sube el volumen del primer sample, baja el volumen del segundo

Options (all must have a double-value in parentesis) / Opciones (todos deben tener un valor-doble en paréntesis):  

| sustantivos           | Info                                           |
| --------------------- | ---------------------------------------------- |
| `sonido`, `sonidos`   | pitch: ++ high/agudo, --low/grave, 0=normal    |
| `forma`, `formas`     | volume/volumen: 0.0 - 2.0, 1.0=normal          |
| `textura`, `texturas` | pan(eo): 0.0=left/izq - 1.0=right/der          |
| `EGGPLANT`            | delay: 0.0=none/sin - 1.0                      |
| `eggPLANT`            | delayfeedbak: 0.0=none/sin - 1.0               |
| `EGGplant`            | delaytime: 0.0=none/sin - 1.0                  |
| `palabra`, `palabras` | cuts the begining / corta el inicio: 0.0 - 1.0 |
| `idioma`, `idiomas`   | cuts the end / corta el final: 0.0 - 1.0       |
| `México`              | efecto/effect 1, no-value/sin-valor            |
| `Colombia`            | efecto/effect 2, no-value/sin-valor            |
| `English`             | efecto/effect 3, no-value/sin-valor            |
| `Español`             | efecto/effect 4, no-value/sin-valor            |
| `Agosto`              | efecto/effect 5, no-value/sin-valor            |

Multiple nouns can be added (up to 5) / Multiples sustantivos pueden ser añadido (hasta 5)  

## Empty string / String vacíos
This is a list of words that can be added in-between words that produce an empty string.  
Esta es una lista de palabras que pueden ser añadidas entre palabras y producen un string vacío  

`Yo`, `mi`, `mis`, `su`, `sus`, `un`, `una`, `Un`, `Una`, `dedo`, `con`, `ajeno`, `ajenos` | Example:  
+ `Yo amo(2.0) escuchar oir no ver:5 presurosas (35) formas (0.8 1.0) ajenos sonidos (-0.2)`

## Multiple sentences / Oraciones múltiples
To add multiple sentences, these are divided by `,` (comma) / Para añadir oraciones múltiples, éstas van separadas por `,` (coma) | Example:  
+ `escucha vívidas(20) formas(1.3), observo*2 sonidos (0.5) texturas (0.0 1.0)`
