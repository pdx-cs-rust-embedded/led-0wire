# led-0wire: "0Wire" RGB LED controller
Bart Massey 2023

This Rust crate provides control and voltage for a "0Wire"
"programmable" RGB LED using the [CZineLight control
protocol](https://cdn.sparkfun.com/assets/9/f/1/c/6/CZineLight_0-Wire_Communication_Protocol.pdf).
The control protocol signals the LED using short power drops
to get various power modes.

This crate has been tested with the SparkFun COM-21209 LED,
for which Mouser supplies the [CZINELIGHT YBR-43FMRGB-A8686
datasheet](https://www.mouser.com/datasheet/2/813/0_Wire_RGB_LED_Datasheet-3225050.pdf).

For 5V operation, nothing particularly special need be done:
the LED can be hooked directly to a push-pull GPIO pin
driven by this crate. The GPIO should be capable of
providing 15mA of current. Best practice would be to limit
the current to 18.5mA with a 270Ω resistor high-side.

For 3.3V operation, the requirement of 3.2V typical for the
green and blue components of the LED presents a
problem. With standard GPIO drive, the voltage may be pulled
down too far, leaving the green not so bright and the blue
not visible. Instead, an NMOS low-side switch can be used to
power the LED directly from 3.3V. This works.

# License

This work is licensed under the "MIT License". Please see the file
`LICENSE.txt` in this distribution for license terms.
