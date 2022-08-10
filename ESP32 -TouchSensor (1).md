# ESP32 - Sensor de inclinacion


Esta Práctica explica cómo utilizar el Sensor de Inclinacion en el ESP32
## Hardware utilizado en esta práctica

- 1 módulo de desarrollo ESP-32
- 1 cable micro USB.
- 1 × placa de pruebas
- 6 × cables de puente
- 1 x KY-020 Tilt

## Especificacion tecnicas
- Voltaje de funcionamiento: 3.3 a 5 V
- Tipo de salida: Digital
- Dimensiones: 23 mm x 16 mm x 5 mm
- Vida mecánica: 100.000 ciclos
- Temperatura ambiente: -25 ºC a 105 ºC
- Peso: 2 g


## Usos
Los sensores de inclinación se utilizan en varias aplicaciones como pueden ser: protección de la inclinación en grúas y plataformas, maquinaria agrícola, naval (roll y pitch), nivelación de plataformas, monitorización del ángulo en brazos telescópicos en bombas de hormigón y aplicaciones de pesaje (en un ángulo).


## KY-020 Tilt Sensor
![figura](https://sensorkit.joy-it.net/files/files/sensors/KY-020/KY-020.png)
Dependiendo de la inclinación, un interruptor cierra brevemente los pines de entrada. Esto sucede debido a que una bola en el interior cortocircuita los contactos, dependiendo de la posición.

## Diagrama de cableado entrel el sensor touch, el esp32 y el led
![cablead](https://z-p3-scontent.fmex13-1.fna.fbcdn.net/v/t1.15752-9/296774085_768157667856191_4446002281098678837_n.png?_nc_cat=103&ccb=1-7&_nc_sid=ae9488&_nc_eui2=AeGp5Gl3u0gBNyBBNp9ubSPglVy0VwYnFICVXLRXBicUgJPDM81f7Js6AbGmRo4LX1d3QJodjBkvoy1VxCX-2PB_&_nc_ohc=bwNeit5PqDgAX-1VyOU&_nc_ht=z-p3-scontent.fmex13-1.fna&oh=03_AVLY4UjsiL2IhlPO3P3cYQBeGBMDDegMiUJLlx6MMPJnwg&oe=631966A9)


## ESP32 CODE
```c++
// DECLARAMOS LAS VARIABLES QUE VAMOS A UTILIZAR
int Pin_Led = 2;      // Este es el pin que tiene asociado un led en la propia placa del microcontrolador 
int Pin_Sensor = 5;  // INDICAMOS EL PIN POR DONDE RECIBIMOS LA SEÑAL DEL SENSOR
 
void setup()
{
  // DECLARAMOS LOS MODOS DE LOS PINES UTILIZADOS
  pinMode(Pin_Led, OUTPUT);
  pinMode(Pin_Sensor , INPUT);
}
 
void loop()
{
  int sensor = digitalRead(Pin_Sensor); // Recogemos la señal que se recibe por el pin del sensor
  if (sensor == HIGH)
  {
    digitalWrite(Pin_Led, HIGH);
    delay(1000); // Ponemos una pausa de 1 segundo cuando ha detectado inclinación
  }
  else
  {
    digitalWrite(Pin_Led, LOW);
  }
}

```

