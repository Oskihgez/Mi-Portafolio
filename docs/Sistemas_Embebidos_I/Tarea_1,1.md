## Comparación de Microcontroladores

Como primera actividad se quiere comparar cuatro microcontroladores para la realización de un proyecto mecatrónico a elegir tomando en cuenta las siguientes características:

- Perifericos
- Memoria
- Ecosistema
- Costos
- Arquitectura
- Velocidad de trabajo
  
---

### Proyecto a Tener en Cuenta

`AirMouse`

Se tomó como referencia un proyecto ya realizado, porque es más sencillo conocer las necesidades que el proyecto le pide al microcontrolador. Como son unos perifericos adecuados y principalmente una velocidad de trabajo excepcional.

---

### Tabla Comparativa

Para elegir los microcontroladores a comparar, se tomó en cuenta la capacidad de conexión por medio de Wifi o Bluetooth y un tamaño compacto.

| **Microcontrolador**              | **Periféricos**                                    | **Memoria**                                       | **Ecosistema**                          | **Costos** | **Arquitectura**              | **Velocidad de trabajo** |
|--------------------------------|------------------------------------------------|-----------------------------------------------|--------------------------------------|-----------------|---------------------------|----------------------|
| **Seeed XIAO ESP32-C3**        | WiFi, BLE 5.0, UART, I2C, SPI, ADC, PWM        | 400 KB SRAM + 4 MB Flash                     | Arduino, ESP-IDF, MicroPython        | 180-300 MXN        | RISC-V 32-bit             | 160 MHz              |
| **Arduino Nano RP2040 Connect**| WiFi, BLE, IMU integrado, UART, I2C, SPI, ADC, PWM | 264 KB SRAM + 16 MB Flash                  | Arduino + Pico SDK, MicroPython      | 530-750 MXN      | Dual-core ARM Cortex-M0+  | 133 MHz              |
| **Adafruit Feather nRF52840**  | BLE 5.0, USB nativo, UART, I2C, SPI, ADC, PWM  | 256 KB RAM + 1 MB Flash                      | Arduino, CircuitPython, Zephyr       | 720-950 MXN     | ARM Cortex-M4F 32-bit     | 64 MHz               |
| **Seeed XIAO ESP32-S3**        | WiFi, BLE 5.0, USB-C nativo, UART, I2C, SPI, ADC, PWM | 512 KB SRAM + 8 MB PSRAM + 8 MB Flash (modelo con PSRAM) | Arduino, ESP-IDF, MicroPython | 210-330 MXN       | Xtensa LX7 dual-core 32-bit| 240 MHz    |

**1.- Seeed XIAO ESP32-S3:** Considero que este microcontrolador es la mejor opción por ser el controlador con mayor potencia, buen tamaño de memoria, un tamaño compacto, y un costo considerablemente bajo a pesar de no ser el más barato, teniendo capacidad de conexión via BLE y Wifi.

**2.- Seeed XIAO ESP32-C3:** Es una buena opción porque es muy barato y pequeño, con WiFi y BLE integrados. Aunque no tiene tanta potencia como el S3, cumple bien para un prototipo funcional.

**3.- Arduino Nano RP2040 Connect:** Es completo porque ya trae WiFi, BLE y un sensor IMU integrado. Sin embargo, es el más caro y más grande de todos, lo que lo hace menos cómodo para el guante.

**4.-Adafruit Feather nRF52840 Express:** Su ventaja es que tiene un buen Bluetooth y consume poca energía, pero es lento comparado con los demás y más caro de lo que debería, por eso queda en último lugar.

