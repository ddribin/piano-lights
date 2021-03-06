# Piano Lights

Displays lights (LEDs) over piano keys as they are played in real-time. This runs on an Arduino Uno and lights up LEDs on an LED strip by listening for MIDI notes generated by the piano.

## Hardware

Here's the hardware used:

- [Arduino Uno](https://store-usa.arduino.cc/products/arduino-uno-rev3?selectedStore=us)
- [SparkFun MIDI Shield](https://www.sparkfun.com/products/12898)
- [BTF Lighting LED strip](https://www.btf-lighting.com/collections/sk9822/products/1-sk9822-led-pixel-strip-data-and-clock-dc5v?variant=25941426831460): SK9822 chipset, 5 volts, 50 LEDs/meter, black PCB
- A digital piano or keyboard that outputs MIDI

**Note:** This will *not* work with Neopixel LED strips (WS2811/WS2812/WS2812B), only APA102 LED strips (SK9822 is an APA102 clone). Neopixels require bit banging, which disables interrupts for too long, and interferes with the hardware UART used by the MIDI port. APA102 can use the hardware SPI of the AVR. See the [FastLED Wiki page about interrupt problems](https://github.com/FastLED/FastLED/wiki/Interrupt-problems) for more information.

## Software

Here's the software used:

- [Arduino MIDI Library](https://github.com/FortySevenEffects/arduino_midi_library)
- [FastLED](https://fastled.io)
- [PlatformIO](https://platformio.org)

## How It Works

All the heavy lifting is done by the two libraries. The code reads MIDI note on and off events and turns on a corresponding LED. The LED colors are set using the HSV color space. Each key is mapped the hue, with the low A0 mapped to 0 and high C8 mapped to 255. There are two potentiometers on the MIDI shield. One is mapped to the saturation, and the other the value (brightness).

## Demo Video

[![Demo Video](https://img.youtube.com/vi/pe3vuLcroIA/0.jpg)](https://www.youtube.com/watch?v=pe3vuLcroIA)
