
# COMPARACIÓN DE TECNOLOGÍA CMOS y TTL


## Comparacion de de especificaciones 

<p align="center">

| **Especificación**            | **CD4069 (CMOS)**                    | **74LS04 (TTL)**                     |
|--------------------------------|--------------------------------------|---------------------------------------|
| **Tecnología**                 | CMOS (Complementary Metal-Oxide Semiconductor) | TTL (Transistor-Transistor Logic)    |
| **Número de compuertas**       | 6 inversores                         | 6 inversores                          |
| **Tensión de alimentación ($V_{CC}$)** | 3 V a 15 V                          | 4.75 V a 5.25 V (típicamente 5 V)     |
| **Consumo de corriente**       | Muy bajo (µA en reposo)              | Mayor (mA en reposo)                  |
| **Velocidad de operación**     | Más lento que TTL                    | Más rápido que CMOS                   |
| **Corriente de salida**        | Baja (< 1 mA típicamente)            | Alta (hasta 24 mA máx. en salida baja)|
| **Margen de ruido**            | Mayor debido a la alta impedancia    | Menor debido a la baja impedancia     |
| **Tiempo de propagación ($t_{pd}$)**| Típicamente 50-200 ns                | Típicamente 10-25 ns                  |
| **Impedancia de entrada**      | Muy alta                             | Baja                                  |
| **Consumo dinámico**           | Bajo, depende de la frecuencia       | Alto, incluso a frecuencias bajas     |
| **Nivel lógico alto ($V_{OL}$)**   | ~70% de Vcc                          | 2.4 V mín.                            |
| **Nivel lógico bajo ($V_{OH}$)**   | ~30% de Vcc                          | 0.4 V máx.                            |
| **Compatibilidad lógica**      | Compatible con otras familias CMOS   | Compatible con otras familias TTL y algunas CMOS con adaptadores |
| **Aplicaciones típicas**       | Circuitos de bajo consumo, digitales simples | Circuitos de alta velocidad y cargas más pesadas |

</p>

## Circuitos equivalentes

1. Negador en BJT

Para este caso, se utilizo el modelo dado en la hoja de datos de la compuerta 74LS04, ya que el modelo más sencillo de compuerta negadora, apenas era notoria la caida de tensión debido a las resistencias. 

![EquivalenteTTL](./Imagenes/ModeloTTL.png)

![SeñalTTL](./Imagenes/SeñalequiTTL.png)


2. Negador en CMOS 

Se usa el modelo más comun de compuerta negadora en CMOS, donde en la salida esta la señal completa, no hay caida de tensión o es casi imperceptible.

![EquivalenteCMOS](./Imagenes/ModeloCMOS.png)

![SeñalCMOS](./Imagenes/SeñalequiCMOS.png)

## Señal cuadrada 1kHz

### Simulaciones

1. Negador TTL 74LS04 

El circuito que se uso para las distintas simulaciones se puede ver a continuación:

![CircuitoTTL](./Imagenes/Circuito%20TTL.png)

Al aplicarle una señal cuadrada con 1KHz de frecuencia y amplitud 5V, se obtuvo la siguiente gráfica que relaciona la salida con la entrada.

![Entrada-SalidaTTL](./Imagenes/Entrada-Salida%20TTL.png)

En la anterior imagen se puede dar uno cuenta que el circuito efectivamente corresponde al de una compuerta lógica NOT, es decir, que invierte el valor de la señal de entrada.
Ahora, se gráfica la función de transferencia de este circuito, la cual se puede ver en la siguiente imagen.

![FuncionTransferenciaTTL](./Imagenes/Función%20Transferencia%20TTL%205V.png)

De la función de transferencia se pueden obtener los siguientes valores:

+ $V_{IL} = 2.479V$
+ $V_{IH} = 2.509V$
+ $V_{OL} = 13.971mV$
+ $V_{OH} = 4.975V$

2. Negador CMOS CD4069

El circuito que se uso para las distintas simulaciones se puede ver a continuación:

![CircuitoCMOS](./Imagenes/Circuito%20CMOS.png)

Al aplicarle una señal cuadrada con 1KHz de frecuencia y amplitud 5V, se obtuvo la siguiente gráfica que relaciona la salida con la entrada.

![Entrada-SalidaCMOS](./Imagenes/Entrada-Salida%20CMOS.png)

En la anterior imagen se puede dar uno cuenta que el circuito efectivamente corresponde al de una compuerta lógica NOT, es decir, que invierte el valor de la señal de entrada.
Ahora, se gráfica la función de transferencia de este circuito, la cual se puede ver en la siguiente imagen.

![FuncionTransferenciaCMOS](./Imagenes/Función%20Transferencia%20CMOS%205-5V.png)

De la función de transferencia se pueden obtener los siguiente valores:

+ $V_{IL} = 2.508V$
+ $V_{IH} = 2.526V$
+ $V_{OL} = 2.524mV$
+ $V_{OH} = 5V$

### Experimentalmente 
1. Negador TTL 74LS04 

Al observar la salida de la compuerta es notorio que hay una caida de tensión bastante grande, lo que confirma el modelo equivalente de transistores usado anteriormente.

![SeñalCuadradaTTL](./Imagenes/SeñalCuadradaTTL.jpeg)

2. Negador CMOS CD4069

Para este caso, aún existe una pequeña caida de tensión a la salida de la compuerta, además de ser bastante menor comparada a la del negador en TTL, por lo que es un resultado aceptable.
Esto se sustenta con el $V_{OL}$ encontrado mediante la función de transferencia, el valor para este parámetro tiene un menor margen con respecto al negador en TTL dando como resultado que la caída de tensión observada sea menor

![SeñalcuadradaCMOS](./Imagenes/señalcuacmos.jpeg)

## Tiempos de subida y bajada, retardo y tiempos de almacenamiento

   - Tiempo de Retardo 

   El tiempo de retardo o tiempo o propagating delay ($t_p$), se refiere al tiempo que tarda una señal en propagarse en la compuerta, desde que entra hasta que sale, para esto se toman intervalos desde el momento en que la señal de entrada alcanza el 50% de la tensión, hasta que la señal de salida alcanza el nivel equivalente. 

   
   - Tiempos de almacenamiento

   Aplica especialmente a compuertas TTL, ya que son contruidas en BJT, se refiere al tiempo en el que el transistor deja totalmente la zona de saturancion antes de pasar a la zonas de corte, esto se debe a que el transistor no responde de forma inmediata y permanece en saturación antes de hacer el cambio, claro esta CMOS también se ve afectado por lo mismo, pero sus tiempos de respuesta son más rapidos. 

### Simulaciones 
1. Negador TTL 74LS04 

Para esto se usarón varias directivas en LTspice, las cuales se pueden ver a continuación:

![tr-tf-TTL](./Imagenes/tr-tf-TTL.png)

- Tiempo de subida

   El resultado obtenido mediante la simulación fue de:

   $t_{r} = 8.54511x10^{-7}s$

- Tiempo de bajada 

   El resultado obtenido mediante la simulación fue de:

   $t_{f} = 1.53357x10^{-7}s$

2. Negador CMOS CD4069

Al igual que en negador en TTL se usaron diversas directivas en LTspice con las que se obtuvieron los tiempos de subida y bajada.

![tr-tf-CMOS](./Imagenes/tr-tf-CMOS.png)

- Tiempo de subida

   El resultado obtenido mediante la simulación fue de:

   $t_{r} = 1.79417x10^{-7}s$

- Tiempo de bajada 

   El resultado obtenido mediante la simulación fue de:

   $t_{f} = 2.02093x10^{-7}s$


### Experimentalmente

1. Negador TTL 74LS04 

   - Tiempo de subida


   - Tiempo de bajada 


2. Negador CMOS CD4069

   - Tiempo de subida


   - Tiempo de bajada 



## Fan-In y Fan-Out 


1. Negador TTL 74LS04 
- Fan-In 



- Fan-Out 
   Se puede calcular usando los de su datasheet, en donde se divide la corriente de salida de nivel bajo  entre la corriente de entrada de nivel bajo. 

   
   $Fan-Out = \frac{I_{LO}}{I_{LI}} = \frac{8 mA}{0.36 mA} = 2$


2. Negador CMOS CD4069



## Determinación de potencia 



## Circuito propuesto

<iframe width="320" height="180" src="https://www.youtube.com/shorts/BrqkxL82p68" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="1"></iframe>


## Oscilador en anillo

Se montarón dos circuitos diferentes en anillo haciendo uso del negador CMOS, exactamente se realizó una configuración con tres y cinco puertas.
Sus respectivas simulaciones se pueden observar a continuación:

### Simulaciones

Se empleo una directa de LTspice en la que se indicaba una condición inicial en el circuito, está consistio en la alimentación inicial de un pulso de amplitud 5V. Posteriormente, el circuito oscilaría a partir de esta señal inicial. 

1. Oscilador con 3 compuertas

   El circuito empleado en la simulación fue el siguiente:

   ![Circuito3Puertas](./Imagenes/Circuito%20oscilador%20de%203.png)

   La frecuencia medida durante la ejecución de la simulación fue de $1.68MHz$, podemos verla en la siguiente imagen.

   ![Frecuencia3Puertas](./Imagenes/Oscilador%20de%203.png)

   Es bueno resaltar que la forma de onda en la simulación es cuadrada debido a la condición inicial mientras que en la prueba experimental dicha forma de onda será totalmente distinta debido a que no se alimentará al circuito con una señal inicial.
   Esta condición inicial se llevo a cabo en LTspice porque el tiempo de ejecución de la simulación era demasiado alto debido a que no había una señal inicial, sino que era solamente ruido.

2. Oscilador con 5 compuertas

   El circuito empleado en la simulación fue el siguiente:

   ![Circuito5Puertas](./Imagenes/Circuito%20oscilador%20de%205.png)

   La frecuencia medida durante la ejecución de la simulación fue de $751KHz$, podemos verla en la siguiente imagen.

   ![Frecuencia5Puertas](./Imagenes/Oscilador%20de%205.png)

   Al igual que en la anterior configuración la forma de onda en la simulación es cuadrada debido a la condición inicial; sin embargo, durante el montaje experimental la onda cambiará porque no se le colocará ninguna señal inicial.

### Resultados Experimentales

1. Oscilador con 3 compuertas


![3compuertas](./Imagenes/3compuertas.jpeg)

2. Oscilador con 5 compuertas 

![5compuertas](./Imagenes/5compuertas.jpeg)


