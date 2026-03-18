# Componetes de HW

## MAX30102

El MAX30102 es un sensor óptico integrado para oximetría de pulso y medición de ritmo cardiaco. Integra LEDs rojo e infrarrojo, fotodetector, elementos ópticos y electrónica de bajo ruido, pensado para dispositivos wearables y móviles. Según el datasheet, trabaja con una alimentación de 1.8 V para la lógica interna y una alimentación separada para LEDs de 3.3 V nominal.

Referencia: MAX30102 datasheet, pp. 1-2, 28.

### Consumos de  Voltage y corriente 

#### Supply Current (IDD):
- 600 µA típico
- 1200 µA máximo

#### Voltaje y condiciones de ese consumo

Esas especificaciones están dadas bajo estas condiciones:
- VDD = 1.8 V
- VLED+ = 5.0 V
- TA = -40 °C a +85 °C
- Valores típicos a TA = +25 °C, salvo indicación contraria

#### Corriente en shutdown
- ISHDN = 0.7 µA típico
- 10 µA máximo

Condición:
- TA = +25 °C
- MODE = 0x80

#### Consumo de los leds

El consumo de alimentación del IC, el datasheet muestra que la corriente programable de cada LED puede llegar hasta:

- 51.0 mA típico por LED cuando LEDx_PA = 0xFF

Aquí hay una nota importante del propio datasheet: la corriente real de LED puede variar ampliamente entre partes por la metodología de trimming. En esa tabla no se especifica una condición explícita de temperatura/voltaje como en la tabla de supply current. Hasta 51.0 mA típico por LED programado, según el registro de amplitud de pulso.

Referencia: MAX30102 datasheet, pp. 2, 20.

### Comunicación 

El dispositivo MAX30102 utiliza I2C / SMBus-compatible.

#### Velocidad:

- 400 kHz fast mode

#### Dirección:

- I2C Write Address = AEh
- I2C Read Address = AFh

Eso corresponde, por inferencia estándar de direcciones I2C de 8 bits, a una dirección de 7 bits = 0x57.



## MPU6050

El MPU6050 es un sensor de movimiento de 6 ejes, que integra un acelerómetro de 3 ejes y un giroscopio de 3 ejes, además de un Digital Motion Processor (DMP) y sensor de temperatura interno. Está pensado para detección de movimiento, orientación y seguimiento de postura/movimiento.

Referencia: MPU-6000/MPU-6050 datasheet, pp. 7, 10, 24.

### Consumos de corriente y voltage

En el datasheet del MPU6050, la tabla de consumo no da un valor “máximo” garantizado; da valores típicos. Los principales son:

- 3.9 mA típico: Gyroscope + Accelerometer + DMP
- 3.8 mA típico: Gyroscope + Accelerometer, DMP deshabilitado
- 3.7 mA típico: Gyroscope + DMP, acelerómetro deshabilitado
- 3.6 mA típico: Gyroscope only
- 500 µA típico: Accelerometer only
- 10 µA típico: Accelerometer low power, 1.25 Hz
- 20 µA típico: Accelerometer low power, 5 Hz
- 70 µA típico: Accelerometer low power, 20 Hz
- 140 µA típico: Accelerometer low power, 40 Hz
- 5 µA típico: Full-chip idle mode

VLOGIC normal operating current = 100 µA típico

Estas corrientes están especificadas con:

- VDD = 2.375 V a 3.46 V
- VLOGIC = 1.8 V ±5% o VDD
- TA = 25 °C

### Comunicación 

El dispositivo MPU6050 utiliza únicamnete I2C.

#### Velocidad:

- 100 kHz standard mode
- 400 kHz fast mode

#### Dirección:

- AD0 = 0 -> 1101000 -> 0x68
- AD0 = 1 -> 1101001 -> 0x69


## Conclusiones



| Sensor   |                                                Corriente más alta reportada | Voltaje                                              | Condiciones                                                         | Comunicación                      | Dirección I2C                             |
| -------- | --------------------------------------------------------------------------: | ---------------------------------------------------- | ------------------------------------------------------------------- | --------------------------------- | ----------------------------------------- |
| MAX30102 | **IDD máx: 1200 µA**; además LEDs hasta **51.0 mA típ.** por LED programado | **VDD = 1.8 V**, **VLED+ = 5.0 V**                   | **TA = -40 a +85 °C**, modos SpO2/HR o IR only, PW = 215 µs, 50 sps | I2C/SMBus, 2 hilos, hasta 400 kHz | **AEh write / AFh read**, 7-bit: **0x57** |
| MPU6050  |                                                           **3.9 mA típico** | **VDD = 2.375–3.46 V**, **VLOGIC = 1.8 V ±5% o VDD** | **TA = 25 °C** para tabla de corriente                              | I2C, hasta 400 kHz                | **0x68** o **0x69** según AD0             |


Con base en los datasheets revisados, el consumo total del sistema formado por los sensores **MAX30102** y **MPU6050** puede analizarse en dos niveles. Considerando únicamente la corriente principal de alimentación de cada circuito integrado, el **MAX30102** presenta un consumo máximo de **1.2 mA** y el **MPU6050** un consumo típico máximo de **3.9 mA**, por lo que el consumo total base es de aproximadamente **5.1 mA**. En este caso, el **MPU6050** representa la mayor contribución al consumo total.

Por otro lado, si se considera también la corriente del LED del **MAX30102** en su ajuste más alto, el consumo total aumenta de forma importante. Sumando los **51.0 mA típicos** del LED, junto con los **1.2 mA** del MAX30102 y los **3.9 mA** del MPU6050, se obtiene un consumo aproximado de **56.1 mA**. En conclusión, el consumo total del sistema puede ir de **5.1 mA** a **56.1 mA**, dependiendo de si se contempla únicamente la alimentación de los sensores o también la corriente de excitación óptica del MAX30102.