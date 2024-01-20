# Practica 6
## Introducción
En este repositorio se verá a detalle como programar LED indicadores de nivel para una bomba de agua.
## Materiales a utilizar
+ Wokwi
+ Leds
+ Resistencias
+ Ultrasonico
## Intrucciones
1. Como primer paso escribimos el código:
```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

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
if (safetyDistance>=1 && safetyDistance<=100)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=101 && safetyDistance<=201) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=202 && safetyDistance<=303) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=304 && safetyDistance<=395) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
 digitalWrite(led1,  HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}

// Prints the distance on the Serial Monitor
Serial.print("Litros: ");
Serial.println(distance);
delay (2000);
}

```
2. Como segundo paso, definimos los 4 pines y hacemos las conexiones
## Conexiones
Se realiza las conezciones de los LED´s y el ultrasonico de la siguiente forma:


![](https://github.com/AlejandroBarreraU/Practica-6/blob/main/New%20ESP32%20Project%20-%20Wokwi%20Simulator%20-%20Google%20Chrome%2019_01_2024%2006_42_16%20p.%20m..png?raw=true)

## Resultados
LED CON UN LITRO EN TANQUE


![](https://github.com/AlejandroBarreraU/Practica-6/blob/main/DiegoJm10_Node-red-instalacion%20-%20Google%20Chrome%2019_01_2024%2007_00_29%20p.%20m..png?raw=true)

LED CON 113 LITROS EN TANQUE


![](https://github.com/AlejandroBarreraU/Practica-6/blob/main/New%20ESP32%20Project%20-%20Wokwi%20Simulator%20-%20Google%20Chrome%2019_01_2024%2007_07_43%20p.%20m..png?raw=true)

LED CON 284 LITROS EN TANQUE


![](https://github.com/AlejandroBarreraU/Practica-6/blob/main/New%20ESP32%20Project%20-%20Wokwi%20Simulator%20-%20Google%20Chrome%2019_01_2024%2006_42_16%20p.%20m..png?raw=true)

LED CON 368 LITROS EN TANQUE


![](https://github.com/AlejandroBarreraU/Practica-6/blob/main/New%20ESP32%20Project%20-%20Wokwi%20Simulator%20-%20Google%20Chrome%2019_01_2024%2007_00_55%20p.%20m..png?raw=true)



## Créditos

Elaborado por el Ing. Alejandro Barrera
