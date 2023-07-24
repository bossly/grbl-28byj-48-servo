# GRBL 1.1h 28byj-48 + Servo Motor (pen plotter)

<a href="https://www.buymeacoffee.com/01eg" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>

This GRBL uses an ugly hack to control two motors unipolar steps as 28byj-48 and also supports a servo motor on pin 11

The motors (28byj-48) are connected to a controller card that uses the chip ULN2003. This board is connected to pins A0, A1, A2, A3 for the Y axis and 2,3,4,5 digital pins to the axis X. The servomotor connected to pin 11 h.

Credits to @ruizivo who modify grbl that I used as reference: https://github.com/ruizivo/GRBL-28byj-48-Servo

## grbl-servo

Servo support done by using https://github.com/lavolpecheprogramma/grbl-1-1h-servo code modification. Credits to @lavolpecheprogramma


`grbl-servo` can be used on Arduino to control an X-Y pen plotter, where the pen is operated by a small servo motor such as an SG90 micro servo.

## Servo details

The main idea is to use the PWM signal normally used for spindle control in `grbl` to send a PWM signal to the servo for up/down motion. NB: the added servo functionality will only operate in 'non laser' ($32=0) mode

Connect the servo PWM signal input to the `Z-` or `Z+` pin on the Arduino CNC shield (or the `D11` pin on the arduino).

G-code to operate the servo
```gcode
M3 S255     (turn servo full on)
M5          (turn servo off)
M3          (turn servo full on)
M5          (turn servo off)
M3 S127     (turn servo half way)
M5          (turn servo off)
M3          (turn servo half way)
M5          (turn servo off)
```