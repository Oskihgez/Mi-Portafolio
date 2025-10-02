## Control de Duty Cycle y Motor DC

---

Implementar un circuito con un motor DC controlado mediante PWM variando el duty cycle.

Usar 2 botones para seleccionar entre 3 velocidades predefinidas (baja, media y alta).

Documentar:

- Valores de duty usados, con el porque.

- Circuito

- Codigo

!!! tip "Recomendación"
    No olvidar que el microcontrolador no entrega suficiente potencia, se debe usar un puente H o driver de motor para conectar el motor DC.

---

### Valores del Duty

- Velocidad Baja: 255 Se usó este valor como el mínimo porque el motor funciona con minimo 3v a maximo 12v siendo 3v el 25% de 12v, lo que corresponde a 255 de 1023.

- Velocidad Media: 511 Este valor es la mitad del valor máximo.

- Velocidad Alta: 1023 Es el valor máximo del Duty.

---
#### Esquemático de conexión Control de Motor DC

Esquemático del circuito usado durante la actividad Control de Motor DC.

![Diagrama del sistema](../recursos/imgs/esquematico_tarea7,1.png)

---
### Código

```C++

#include "pico/stdlib.h"
#include "hardware/pwm.h"
 
 
#define BOTON1 16
#define BOTON2 19
#define MOTOR 0
#define F_PWM_HZ 2000   // 2 kHz: fuera del rango visible
#define TOP 1023        // 10 bits de resolución
 
int BOTON1ESTADO=0;
int BOTON2ESTADO=0;
 
 
int main() {
    stdio_init_all();
 
    gpio_set_function(MOTOR, GPIO_FUNC_PWM);
    uint slice = pwm_gpio_to_slice_num(MOTOR);
    uint chan  = pwm_gpio_to_channel(MOTOR);
 
    // Calcular divisor
    float f_clk = 150000000.0f; // 125 MHz
    float div = f_clk / (F_PWM_HZ * (TOP + 1));
    pwm_set_clkdiv(slice, div);
    pwm_set_wrap(slice, TOP);
 
    pwm_set_chan_level(slice, chan, 1023);
    pwm_set_enabled(slice, true);
 
 
    gpio_init(BOTON1); gpio_set_dir(BOTON1,0);
    gpio_init(BOTON2); gpio_set_dir(BOTON2,0);
 
    int velocidades[3]={250,512,1023};
    int velocidad_actual=0;
 
    while (true) {
        BOTON1ESTADO=gpio_get(BOTON1);
        BOTON2ESTADO=gpio_get(BOTON2);
 
        if (BOTON1ESTADO==1){
            velocidad_actual++;
            if (velocidad_actual>2){
                velocidad_actual=0;
            }
            pwm_set_chan_level(slice, chan, velocidades[velocidad_actual]);
            sleep_ms(300);
        }
 
        if (BOTON2ESTADO==1){
            velocidad_actual--;
            if (velocidad_actual<0){
                velocidad_actual=2;
            }
            pwm_set_chan_level(slice, chan, velocidades[velocidad_actual]);
            sleep_ms(300);
        }
 
        sleep_ms(10);
    }
}

```
---

#### Video del Funcionamiento: Control de Duty Cycle y Motor DC

<iframe width="560" height="315" src="https://www.youtube.com/embed/v5QQKKRf06g?si=Omj-1c1QOmUWDUwf" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>