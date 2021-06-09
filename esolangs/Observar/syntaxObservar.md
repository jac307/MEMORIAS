# OBSERVAR

For sound patters with instruments / Para patrones sonoros con instrumentos <br/>
Parsing Tidal Cycles <br/>

This [esolang](https://github.com/dktr0/estuary/blob/dev/client/src/Estuary/Languages/TiempoEspacio/Observar.hs) can be accesed through [Estuary](https://estuary.mcmaster.ca/), just look for it on the language's dropdown menu.  

Este [esolang](https://github.com/dktr0/estuary/blob/dev/client/src/Estuary/Languages/TiempoEspacio/Observar.hs) puede ser accesado a través de [Estuary](https://estuary.mcmaster.ca/), busca en el menú de opciones.  

____________________________________________

## Syntax / Sintaxis

This syntax uses words and structures in Spanish / Esta sintaxis usa palabras y estructuras en Español.  

## Basic sentece to produce sound: Verb / Oración básica para producir sonido: Verbo
*verbo* | Example:   
+ `olvidar` -- plays the first sample of the "olvidar" folder / reproduce el primer sample del folder "olvidar".

Options/Opciones:

| verbo                                                                      | Files | Info                                                    |
| -------------------------------------------------------------------------- | ----- | ------------------------------------------------------- |
| `olvidar`, `olvido`, `olvida`, `olvidan`, `olvidado`, `olvidando`          | 6     | plays [olvidar-folder](/samples/audioSamples/olvidar)   |
| `pensar`, `pienso`, `piensa`, `pensaron`, `pensado`, `pensando`            | 4     | plays [pensar-folder](/samples/audioSamples/pensar)     |
| `soñar`, `sueño`, `sueña`, `sueñan`, `soñado`, `soñando`                   | 3     | plays [soñar-folder](/samples/audioSamples/sonar)       |
| `recordar`, `recuerdo`, `recuerda`, `recuerdan`, `recordado`, `recordando` | 7     | plays [recordar-folder](/samples/audioSamples/recordar) |
| `extrañar`, `extraño`, `extraña`, `extrañan`, `extrañado`, `extrañando`    | 4     | plays [extrañar-folder](/samples/audioSamples/extranar) |
| `mirar`, `miro`, `mira`, `miran`, `mirado`, `mirando`                      | 3     | plays [mirar-folder](/samples/audioSamples/mirar)       |
| `caminar`, `camino`, `camina`, `caminan`, `caminado`, `caminando`          | 4     | plays [caminar-folder](/samples/audioSamples/caminar)   |
| `reir`, `río`, `ríe`, `ríen`, `reído`, `riendo`                            | 3     | plays [reir-folder](/samples/audioSamples/reir)         |
| `aparecer`, `aparezco`, `aparece`, `aparecen`, `aparecido`, `aparenciendo` | 3     | plays [aparece-folder](/samples/audioSamples/aparece)   |
| `volver`, `vuelvo`, `vuelve`, `vuelven`, `vuelto`, `volviendo`             | 6     | plays [volver-folder](/samples/audioSamples/volver)     |
| `producir`, `produzco`, `produce`, `producen`, `producido`, `produciendo`  | 7     | plays [producir-folder](/samples/audioSamples/producir) |

## Changing the sample number / Cabiando el número de sample
*verbo:#* | Example:  
+ `olvidar:2` -- plays the third sample (starting from 0) of the "olvidar" folder / reproduce el tercer sample (contando desde 0) del folder "olvidar".

## Other variations for the basic sentence / Otras variaciones de oración básica
+ *verbo verbo verbo* | Example: `olvidar olvidar:2 olvidar:3` -- plays three samples in one cycle / reproduce tres samples en un ciclo. Cycle/ciclo=1seg
+ _verbo*2 verbo_ | Example: `olvidar*2 pensar` -- plays te first sample twice / reproduce el primer sample dos veces
+ *verbo <verbo:# verbo:#>* | Example: `olvidar <pensar:2 soñar:3>` -- in one cycle plays `olvidar` and `pensar:2`, in the next cycle plays `olvidar` and `soñar:3`; repeats / en un ciclo reproduce `olvidar` y `pensar:2`, en el siguiente ciclo reproduce `olvidar` y `soñar:3`; se repite
+ *verbo [verbo:# verbo:#]* | Example: `olvidar [pensar:2 soñar:3]` -- divides the cicle in two: first part plays `olvidar`, in the second part plays `pensar:2` and `soñar:3` / divide el ciclo en dos: en la primera parte reproduce `olvidar`, en la segunda parte reproduce `pensar:2` y `soñar:3`
+ _[verbo verbo]*2_ | Example: `[olvidar:2 mirar:3]*2` -- plays both samples in double the time of the cycle / reproduce ambos samples en el doble del tiempo del ciclo
+ *[verbo verbo]/2* | Example: `[olvidar:2 mirar:3]/2` -- plays both samples in half the time of the cycle / reproduce ambos samples en la mitad del tiempo del ciclo
+ *verbo empty verbo* | Example: `olvidando que recuerdan` -- divides the cicle in three, the second space is empty / divide el ciclo en tres, el tercer espacio está vacío

Options for empty-space / Opciones para espacio vacío: `no`, `si`, `que`, `sin`, `y`, `ni`   

## Sentece to silence everything / Oración para silenciar todo
+ `silencio` -- evaluate just this word / evalúa únicamente esta palabra

## Tranformations 1: pre-verb / Transformaciones 1: previas al verbo

### Numbers / Números
*número* + *verbo* | Example:  
+ `uno_ olvido olvido` -- plays left and right channels. Must have two or more samples / reproduce en los canales izquierda y derecha. Debe tener más de dos samples.

Opciones / Options:  

| numbers                      | Info                                                                                 |
| ---------------------------- | ------------------------------------------------------------------------------------ |
| `uno_`, `dos_`, `tres_`      | plays left and right / reproduce izquierda y derecha                                 |
| `cuatro_`, `cinco_`, `seis_` | needs a value (double), from then it pans / necesita un valor (doble), de ahí panea  |

+ `uno_ olvidando estrañando*3`
+ `cuatro_ (0.2) olvidando estrañando*3`

### Subject / Sujeto
*número* + *sujeto* + *verbo* | Example:  
+ `uno_ Ella(8) escucha*8` -- acepts int. Makes a granulation efect cutting the samples in the value that is given / acepta un entero. Hace un efecto de granulación cortando los samples en el valor que le des.

Options / Opciones: `Yo`, `yo`, `Ella`, `ella`, `Tu`, `tu`

+ `Yo(18) <recuerdo*4 olvido*4> pienso*2`
+ `Ella(4) no piensa sueña*4`

### Verb Estar / Verbo Estar
*número* + *sujeto* + *verbo-estar* + *verbo* | Example:  
+ `estoy(2.0) pensado olvidado:5`  -- slows the cycle half the time / alenta el ciclo a mitad del tiempo  

Options / Opciones:  

| Verbo-Estar                                 | Info                                                                          |
| ------------------------------------------- | ----------------------------------------------------------------------------- |
| `estar`, `estoy`, `está`, `están`, `estado` | slows a value(double) the whole cycle / alenta un valor(doble) todo el ciclo  |
| `Estar`, `Estoy`, `Está`, `Están`, `Estado` | fast a value(double) the whole cycle / fast un valor(doble) todo el ciclo     |

### Verb Haber / Verbo Haber
*número* + *sujeto* + [*verbo-haber* + *verbo-estar*] + *verbo* | Example:  
+ `he(4) estado(2.0) pensado olvidado:5`  -- slows just every 4 cycles / alenta únicamente cada 4 ciclos

Options / Opciones: `He`, `he`, `Ha`, `ha`, `Han`, `han`  

## Tranformations 2: post-verb / Transformaciones 2: posteriores al verbo

### Adjectives / Adjetivos
*verbo* + *adjetivo* | Examples:  
+ `olvidar blancos(4)` -- plays a random sample of the *olvidar-folder* up to its 4th file (int value) / reproduce un sample de manera aleatoria del *folder-olvidarr* hasta su archivo 4 (valor int)  
+ `olvidar soñar blancos(4)` -- same but now with two folder-samples / lo mismo pero ahora con dos folders the samples.  

Options / Opciones: `blanco`, `blancos`, `blanca`, `blancas`, `opaco`, `opacos`, `opaca`, `opacas`, `gris`, `grises`, `brillante`, `brillantes`

### Noun / Sustantivos
*verbo* + *adjetivo* + *sustantivos* | Examples:  
+ `olvidar blancos(4) sueños(1.3)` -- highest the volume / sube el volumen
+ `olvidar soñar blancos(4) sueños(1.3 0.8)` -- highest the volume of the first sample, lowest the volume of the second / sube el volumen del primer sample, baja el volumen del segundo

Options (all must have a double-value in parentesis) / Opciones (todos deben tener un valor-doble en paréntesis):  

| noun/sustantivo       | Info                                                     |
| --------------------- | -------------------------------------------------------- |
| `recuerdos`           | pitch: ++ high/agudo, --low/grave, 0=normal              |
| `sueño`, `sueños`     | volume/volumen: 0.0 - 2.0, 1.0=normal                    |
| `flor`, `flores`      | pan(eo): 0.0=left/izq - 1.0=right/der                    |
| `luz`, `luces`        | delay: 0.0=none/sin - 1.0                                |
| `rayo`, `rayos`       | delayfeedbak: 0.0=none/sin - 1.0                         |
| `brillo`, `brillos`   | delaytime: 0.0=none/sin - 1.0                            |
| `tiempo`, `tiempos`   | pitch: (-1.0) - 1.0  ++high/agudo, --low/grave, 0=normal |
| `cacahuates`          | distortion/distorsión: 0++                               |
| `venta`, `ventanas`   | cuts the begining / corta el inicio: 0.0 - 1.0           |
| `pasillo`, `pasillos` | cuts the end / corta el final: 0.0 - 1.0                 |
| `puerta`, `puertas`   | room-efect/efecto-room: 0.0=none/sin - 1.0               |
| `cuarto`, `cuartos`   | room-size/tamaño-room: 0.0=none/sin - 1.0                |
| `gato`                | efecto/effect 1, no-value/sin-valor                      |
| `gatos`               | efecto/effect 2, no-value/sin-valor                      |
| `felino`              | efecto/effect 3, no-value/sin-valor                      |
| `felinos`             | efecto/effect 4, no-value/sin-valor                      |
| `perro`               | efecto/effect 5, no-value/sin-valor                      |

Multiple nouns can be added (up to 5) / Multiples sustantivos pueden ser añadido (hasta 5)  

### Adjective-2 / Adjetivos-2
*verbo* + *adjetivo* + *sustantivo* + *adjetivo-2* | Examples:  
+ `olvidar sueños negros (1.0)` -- the value of sueños(volume) is now random (range: 0 - 2) / el valor de sueños(volumen) is ahora aleatorio (rango: 0 - 2)  

This is an alternative option to create random values to nouns, options: / Esta es una opción alternativa para crear valores aleatorios en los sustantivos, options  

`negro`, `negros`, `obscuro`, `obscuros`  

## Empty string / String vacios
This is a list of words that can be added in-between words that produce an empty string.  
Esta es una lista de paralabras que pueden ser añadidas entre palabras y producen un string vacío  

`en`, `sobre`, `el`, `El`, `la`, `las`, `Puerta`, `Puertas`, `Un`, `un`, `unos`, `Perro`, `también`, `mi`, `mis`, `con`, `a`, `A`, `veces`, `No`, `sobre`, `ajeno`, `ajenos` | Example:  
+ `las Palabras han(4) estado(2.0) pensado olvidado:5 sueños negros (1.0) ajenos`

## Multiple sentences / Oraciones múltiples
To add multiple senteces, these are divided by `,` (comma) / Para añadir oraciones múltiples, éstas van separadas por `,` (coma) | Example:  
+ `olvido brillantes(20) sueños(1.3), extraño*2 recuerdos (0.5) sobre pasillos (0.0 1.0)`
