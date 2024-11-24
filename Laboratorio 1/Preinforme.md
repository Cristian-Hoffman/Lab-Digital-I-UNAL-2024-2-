
# COMPARACIÓN DE TECNOLOGÍA CMOS y TTL


## Comparacion de de especificaciones 



## Circuitos equivalentes

1. Negador en BJT

Para este caso, si utilizo el modelo dado en la hoja de datos de la compuerta 74LS04, ya que el modelo mas sencillo de compuerta negadora, apenas era notoria la caida de tension debido a las resistencias. 

![EquivalenteTTL](./Imagenes/ModeloTTL.png)

![SeñalTTL](./Imagenes/SeñalequiTTL.png)


2. Negador en CMOS 

Se usa el modelo mas comun de compuerta negadora en CMOS, donde en la salida esta la señal completa, no hay caida de tension o es casi imperceptible.

![EquivalenteCMOS](./Imagenes/ModeloCMOS.png)

![SeñalCMOS](./Imagenes/SeñalequiCMOS.png)

## Señal cuadrada 1kHz


### Simulaciones

1. Negador TTL 74LS04 



2. Negador CMOS CD4069



### Experimentalmente 
1. Negador TTL 74LS04 

Al observar la salida de la compuerta es notorio que hay una caida de tension bastante grande, lo que confirma el modelo equivalente usado anteriormente.

![SeñalCuadradaTTL](./Imagenes/SeñalCuadradaTTL.jpeg)

2. Negador CMOS CD4069

Para este caso, aun existe una pequeña caida de tension a la salida de la compuerta, ademas de ser bastante menor comparada a la del negador en TTL, por lo que es un resultado aceptable.

![SeñalcuadradaCMOS](./Imagenes/señalcuacmos.jpeg)

## Tiempos de subida y bajada, retardo y tiempos de almacenamiento

   - Tiempo de Retardo 

   El tiempo de retardo o tiempo o propagatin delay ($t_p$), se refiere al tiempo que tarda una señal en propagarse en la compuerta, desde que entra hasta que sale, 

   
   - Tiempos de almacenamiento

### Simulaciones 
1. Negador TTL 74LS04 

   - Tiempo de subida


   - Tiempo de bajada 


2. Negador CMOS CD4069

### Experimentalmente

1. Negador TTL 74LS04 

   - Tiempo de subida


   - Tiempo de bajada 


2. Negador CMOS CD4069


## Fan-In y Fan-Out 


1. Negador TTL 74LS04 



2. Negador CMOS CD4069


## Determinacion de potencia 



## Circuito propuesto




## Oscilador en anillo

1. Oscilador con 3 compuertas


[3compuertas](./Imagenes/3compuertas.jpeg)

2. Oscilador con 5 compuertas 

[5compuertas](./Imagenes/5compuertas.jpeg)


