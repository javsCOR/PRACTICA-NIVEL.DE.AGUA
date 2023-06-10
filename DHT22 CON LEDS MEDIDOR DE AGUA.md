# Practica ESP32 CON Ultrasonic Distance Senso con medidor de agua con leds 
Este repositorio muestra como podemos programar una ESP32 con el sensor  y nos muestra  las distancias  en cm y mandar los resultados deacuerdo ala distancia con luces led  prendiendo deacuerdo ala distancia que va subiendo.


## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH11```) para adquirir la distancia y mandar las señales con el encendido de luces  LED ; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor ultrasonico
- 4 LEDS 
- 4 RESISTENCIAS 


## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

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
if (safetyDistance>=2 && safetyDistance<=10)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=10 && safetyDistance<=20) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=20 && safetyDistance<=30)
{
 digitalWrite(led1,  HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=30 && safetyDistance<=40)
{
 digitalWrite(led1,  HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else 
{
 digitalWrite(led1,  LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}

```
2. NO SE INSTALO NINGUNA LIBRERIA EXTRA

![]()

3. Hacer la conexion de **DHT11** a **Sensor Ultrasonico**  y conectar  **LAS LUCES LED** como se muestra en la siguente imagen.

![](https://github.com/javsCOR/PRACTICA-NIVEL.DE.AGUA/blob/main/leds.png?raw=true)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la distancia dando *doble click* al sensor **DHT11** 
4. tambien  agregamos comandos diferentes a los resultados  **Sensor Ultrasonico** COMO SE MUESTRA EN LA SIGUIENTE  IMAGEN 

![](https://github.com/javsCOR/PRACTICA-NIVEL.DE.AGUA/blob/main/EN%20ACCION.png?raw=true)


## Resultados

Cuando haya funcionado, verás COMO MODIFICANDO SE ENCIENDEN LOS 4 LEDS DEACUERDO ALA DISTANCIA MARCADA  como se muestra en la siguente imagen.

![](https://github.com/javsCOR/PRACTICA-NIVEL.DE.AGUA/blob/main/FUNCIONANDO.png?raw=true)







# Créditos

creado por ING javier cortes rojas
