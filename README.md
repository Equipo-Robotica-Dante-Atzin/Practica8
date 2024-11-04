# Practica 8

## Integrantes

- Dante Mejía Silva
- Atzin Morales Alejandre

## Introducción 

En esta práctica de laboratorio de robótica, se utilizó un brazo robótico Epson C4 para llevar a cabo una tarea de manipulación de piezas, específicamente fusibles. El objetivo fue retomar y aplicar la función pallet, la cual permite organizar el movimiento del brazo en una matriz de posiciones predefinidas. En este caso, la configuración estableció una matriz de 3x2, con el propósito de recoger seis fusibles distribuidos en posiciones específicas dentro de dicha matriz.

El programa realizado es capaz de encender el motor y establecer una potencia baja para los movimientos iniciales. Luego, define la función pallet con las esquinas de la matriz y la cantidad de filas y columnas requeridas. El robot utiliza la función Jump3 para realizar movimientos verticales de posicionamiento y asegurar una operación precisa en cada uno de los fusibles, con la pinza activándose y desactivándose para recoger y colocar los fusibles en la ubicación correspondiente de la matriz.

La importancia de esta práctica radica en su aplicación directa a escenarios industriales reales, donde la automatización y precisión en la manipulación de piezas son esenciales para optimizar la productividad y reducir errores. Esto es fundamental en líneas de ensamblaje, donde la disposición ordenada y el manejo rápido de componentes incrementan la eficiencia operativa.

## Instrucciones

Primero, se definieron las coordenadas necesarias para recoger cada uno de los fusibles, además de los tres puntos clave requeridos por la función *pallet*. Esto resultó en un total de solo ocho puntos, optimizando la programación de posiciones y asegurando precisión en cada movimiento.

![image](https://github.com/user-attachments/assets/68ca98b1-9ee6-4295-a34c-e3e61e41fdee)

Una vez localizados e implementados los puntos en el software, se procedió a desarrollar el siguiente código:
```
Function main
	
	Motor On
	Power Low
		
	Home
	On 2
	Pallet 0, esq_inf_izq, esq_inf_der, esq_sup_izq, 3, 2
		    
	Jump3 Here +Z(30), fus_1 +Z(200), fus_1
    Off 2
	Jump3 Here +Z(200), Pallet(0, 1) +Z(200), Pallet(0, 1)
	On 2
	
	Jump3 Here +Z(200), fus_2 +Z(200), fus_2
	Off 2
	Jump3 Here +Z(200), Pallet(0, 2) +Z(200), Pallet(0, 2)
	On 2
	
		Jump3 Here +Z(200), fus_3 +Z(200), fus_3
	Off 2
	Jump3 Here +Z(200), Pallet(0, 3) +Z(200), Pallet(0, 3)
	On 2
	
		Jump3 Here +Z(200), fus_4 +Z(200), fus_4
	Off 2
	Jump3 Here +Z(200), Pallet(0, 4) +Z(200), Pallet(0, 4)
	On 2
	
		Jump3 Here +Z(200), fus_5 +Z(200), fus_5
	Off 2
	Jump3 Here +Z(200), Pallet(0, 5) +Z(200), Pallet(0, 5)
	On 2
	
		Jump3 Here +Z(200), fus_6 +Z(200), fus_6
	Off 2
	Jump3 Here +Z(200), Pallet(0, 6) +Z(200), Pallet(0, 6)
	On 2
	
	Home
	Motor Off
	
Fend
```
Este código controla el movimiento de un brazo robótico Epson C4 para recoger y organizar fusibles en una matriz usando la función *pallet*. A continuación, se explica cada sección del programa:

1. **Configuración inicial**:
   - `Motor On` y `Power Low`: Encienden el motor y establecen una baja potencia para los movimientos iniciales.
   - `Home`: Lleva al robot a su posición de inicio.
   - `On 2`: Abre la pinza para que esté lista para sujetar los fusibles.
   - `Pallet 0, esq_inf_izq, esq_inf_der, esq_sup_izq, 3, 2`: Define una matriz de 3x2 en la cual el robot colocará los fusibles. Las esquinas de la matriz se especifican con las posiciones *esq_inf_izq* (esquina inferior izquierda), *esq_inf_der* (esquina inferior derecha) y *esq_sup_izq* (esquina superior izquierda).

2. **Ciclo de recolección y colocación**:
   - Para cada fusible (`fus_1` a `fus_6`):
     - `Jump3 Here +Z(30), fus_n +Z(200), fus_n`: El robot se desplaza en una trayectoria hacia la posición del fusible, subiendo y luego bajando para recogerlo con precisión.
     - `Off 2`: Cierra la pinza.
     - `Jump3 Here +Z(200), Pallet(0, n) +Z(200), Pallet(0, n)`: Lleva el fusible a su posición en la matriz de destino, usando las coordenadas de *pallet*.
     - `On 2`: Abre la pinza nuevamente, para recoger el siguiente fusible y soltar el antiguo.

3. **Finalización**:
   - Después de colocar todos los fusibles, el robot regresa a su posición inicial con el comando `Home`.
   - `Motor Off`: Apaga el motor, indicando el final de la operación.

Antes de llevar a cabo la prueba física, se realizó una simulación para verificar el correcto funcionamiento del código. Para ello, se eliminaron las funciones de *On* y *Off*, evitando así posibles errores de ejecución, ya que el objetivo principal era observar y validar únicamente la trayectoria realizada por el brazo robótico. Esto permitió asegurar que los movimientos fueran precisos y que las posiciones fueran correctas.

![image](https://github.com/user-attachments/assets/b97d4c83-d13f-4fbd-897d-b20857d3ba3e)

Por último se llevo a cabo la prueba física que resultó de la siguiente forma:

![Imagen de WhatsApp 2024-11-03 a las 17 00 18_d3bdaca2](https://github.com/user-attachments/assets/d87ef01c-ad19-40d1-af99-7fa77512f8ac)

## Conclusiones

***Atzin Morales Alejandre:*** Esta práctica de laboratorio con el brazo robótico Epson C4 demostró la efectividad de la automatización en tareas como la manipulación y disposición precisa de piezas. La implementación de la función “pallet” y el uso de coordenadas predefinidas en una matriz de 3x2 facilitaron la organización sistemática de los fusibles, reduciendo la complejidad del código y optimizando la eficiencia en el movimiento del robot.

Durante el desarrollo, cada etapa fue planeada para maximizar la precisión, desde la configuración de potencia inicial hasta la coordinación detallada de movimientos verticales y horizontales mediante la función “Jump3” para el movimiento del brazo ahorrando lineas de código. Este control minucioso reflejó no solo el potencial del brazo robótico en ambientes de producción, sino también la capacidad del equipo para adaptar un sistema a requisitos industriales reales, como los de una línea de ensamblaje.

Por ultimo, la simulación previa fue esencial, ya que permitió identificar y corregir posibles inconsistencias en la trayectoria antes de la prueba física, reforzando la exactitud en cada posición de la matriz y asegurando una manipulación sin errores. Esta práctica subraya la importancia de la simulación en la robótica industrial y la programación estructurada para la mejora continua de procesos.




***Dante Mejía Silva:*** 

En conclusión, esta práctica proporcionó una valiosa oportunidad para profundizarar en la programación y control de un brazo robótico Epson C4, centrándose en la manipulación automatizada de piezas. A lo largo de la actividad, se exploraron conceptos fundamentales como la definición de coordenadas, el uso de la función pallet para organizar movimientos en una matriz, y la implementación de estrategias de simulación para garantizar la efectividad del código.

La decisión de realizar una simulación previa a la prueba física fue clave para asegurar el correcto funcionamiento del programa. Al eliminar las funciones de On y Off, se minimizó el riesgo de errores durante la ejecución, permitiendonos concentrarnos únicamnete en validar las trayectorias del brazo robótico. Este enfoque facilitó la identificación de ajustes necesarios en el código.

Durante la prueba física, el brazo robótico demostró su capacidad para recoger y colocar los fusibles en las posiciones correctas de la matriz de manera eficiente y precisa. Este resultado positivo subraya la importancia de la planificación meticulosa y la verificación de cada paso del proceso, elementos esenciales en cualquier proyecto de automatización.

## Referencias Bibliográficas 

[1] 	EpsonCompany, «Especialistas en automatización industrial». 2024, https://www.epson.es/es_ES/robots





























