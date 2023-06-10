# Practica ESP32 con HC-SR04
Este repositorio muestra como podemos programar una ESP32 con el sensor HC-SR04.

## Introducción

### Descripción

En esta practica utilizamos la ```Esp32```con un sensor ultrasonico para poder medir el nivel o la distancia que puede ir aumentado o disminuyendo, deacuerdo el nivel se acciona los led del sistema .

### Algunas aplicaciones para un DHT22
-para medir el nivel de agua de algun sistema

## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor HC-SR04
- LCD
- LED
- Resistencias



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1= 23;
const int led2= 22;
const int led3= 21;
const int led4= 19;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=2 && safetyDistance<=10)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=11 && safetyDistance<=20 ) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=21 && safetyDistance<=30 ) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=31) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay(2000);
}
```
2. Realizar la conecion del circuito

![](https://github.com/DavidVar95/Practica_Nivel_de_agua/blob/main/Captura%20de%20pantalla%202023-06-10%2012.58.28.png?raw=true)


### Instrucciónes de operación

1. Iniciar simulador.
2. Selecciona el sensor"HC-SR04" Y modifica la distancia.
3. los led enciende deacuerdo el aumento de distancia 

## Resultados

cuando la distancia es de 0 a 2 ningun led enciende.

![](https://github.com/DavidVar95/Practica_Nivel_de_agua/blob/main/Captura%20de%20pantalla%202023-06-10%2013.06.29.png?raw=true)


led 1 enciande con el nivel de 3 a 10


![](https://github.com/DavidVar95/Practica_Nivel_de_agua/blob/main/Captura%20de%20pantalla%202023-06-10%2013.08.14.png?raw=true))

led 1 y 2 enciande con el nivel de 11 a 20

![](https://github.com/DavidVar95/Practica_Nivel_de_agua/blob/main/Captura%20de%20pantalla%202023-06-10%2013.10.56.png?raw=true))

led 1,2 y 3 enciande con el nivel de 21 a 30

![](https://github.com/DavidVar95/Practica_Nivel_de_agua/blob/main/Captura%20de%20pantalla%202023-06-10%2013.12.48.png?raw=true))

led 1,2,3 y 4 enciande con el nivel de 31 o mas

![](https://github.com/DavidVar95/Practica_Nivel_de_agua/blob/main/Captura%20de%20pantalla%202023-06-10%2013.15.24.png?raw=true))

# Créditos

Desarrollado por Ing. David Vargas Gonzalez

