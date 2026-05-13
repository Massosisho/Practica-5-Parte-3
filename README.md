# SSD1306 OLED Graphics and Animation Demo

## Overview

This project is a complete graphics and animation demo for a 128x64 SSD1306 OLED display using an Arduino-compatible board.

The program uses the Adafruit SSD1306 and Adafruit GFX libraries to test the main drawing functions supported by the display, including pixels, lines, rectangles, circles, triangles, text rendering, scrolling text, and bitmaps.

In addition to the basic graphics tests, the project includes several custom animations that demonstrate how to create simple visual effects on a monochrome OLED screen.

This project is useful for testing an OLED display, learning how the Adafruit graphics library works, and using the screen as part of embedded systems, IoT devices, dashboards, or interactive electronics projects.

## Features

- Initializes a 128x64 SSD1306 OLED display through I2C
- Uses custom SDA and SCL pins
- Displays a startup message when the screen is detected
- Tests basic drawing functions:
  - Pixels
  - Lines
  - Rectangles
  - Filled rectangles
  - Circles
  - Filled circles
  - Rounded rectangles
  - Filled rounded rectangles
  - Triangles
  - Filled triangles
  - Characters
  - Text styles
  - Scrolling text
  - Bitmaps
- Includes custom OLED animations:
  - Bouncing logo
  - Boat moving over waves
  - Animated sine wave
  - Fourier-style waveform
  - Moving barcode effect
  - Simulated QR code animation
  - Volume bar animation
  - Animated smiling face with glasses
- Prints debug messages to the Serial Monitor
- Repeats the full demo sequence continuously

## Hardware Requirements

- Arduino-compatible development board
- 128x64 SSD1306 OLED display
- I2C OLED module with address 0x3C
- Jumper wires
- USB cable for programming and serial communication

## Wiring

The OLED display communicates using the I2C protocol.

Default pin configuration used in this project:

SDA -> GPIO 20
SCL -> GPIO 21

Typical OLED wiring:

VCC -> 3.3V or 5V
GND -> GND
SDA -> GPIO 20
SCL -> GPIO 21

The I2C pins are defined in the code as:

#define SDA_PIN 20
#define SCL_PIN 21

And initialized with:

Wire.begin(SDA_PIN, SCL_PIN);

If your board uses different I2C pins, update these values before uploading the code.

## Display Configuration

The project is configured for a 128x64 SSD1306 OLED display.

Display settings used in the code:

SCREEN_WIDTH: 128
SCREEN_HEIGHT: 64
OLED_RESET: -1
SCREEN_ADDRESS: 0x3C

The display object is created with:

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

Most common SSD1306 OLED modules use the I2C address 0x3C. If your screen uses another address, modify this line:

#define SCREEN_ADDRESS 0x3C

You can use an I2C scanner to check the correct address of your display.

## Software Requirements

This project requires:

- Arduino IDE or PlatformIO
- Arduino framework
- Wire library
- Adafruit GFX library
- Adafruit SSD1306 library

If you are using Arduino IDE, install the required libraries from the Library Manager:

1. Open Arduino IDE.
2. Go to Tools > Manage Libraries.
3. Search for Adafruit SSD1306.
4. Install the library.
5. Install any required dependencies, including Adafruit GFX.

## Installation

1. Clone this repository:

git clone https://github.com/your-username/ssd1306-oled-graphics-demo.git

2. Open the project in Arduino IDE or PlatformIO.

3. Install the required libraries.

4. Connect the OLED display to the board using the I2C pins.

5. Upload the code to the board.

6. Open the Serial Monitor at 115200 baud.

## Usage

After uploading the program, the board initializes the OLED display and prints status messages through the Serial Monitor.

If the OLED screen is detected correctly, the display shows a startup message:

OLED OK
Direccion 0x3C

The Serial Monitor will show:

Inicializando OLED SSD1306 en 0x3C...
OLED detectada correctamente

After the startup screen, the program begins running a continuous sequence of graphics tests and animations.

If the OLED display is not detected, the Serial Monitor will show:

Error: OLED no encontrada en 0x3C

The program will then stop in an infinite loop to avoid running the demo without a valid display.

## Demo Sequence

The project runs the following tests and animations in order:

1. Pixel drawing test
2. Line drawing test
3. Rectangle drawing test
4. Filled rectangle test
5. Circle drawing test
6. Filled circle test
7. Rounded rectangle test
8. Filled rounded rectangle test
9. Triangle drawing test
10. Filled triangle test
11. Character rendering test
12. Text style test
13. Scrolling text test
14. Bitmap drawing test
15. Bouncing logo animation
16. Boat and waves animation
17. Sine wave animation
18. Fourier-style wave animation
19. Barcode animation
20. Simulated QR code animation
21. Volume bar animation
22. Smiling face animation

Once the sequence finishes, it starts again automatically.

## How It Works

The program starts by opening serial communication at 115200 baud. It then initializes the I2C bus using the selected SDA and SCL pins.

Wire.begin(SDA_PIN, SCL_PIN);

After that, the OLED display is initialized with:

display.begin(SSD1306_SWITCHCAPVCC, SCREEN_ADDRESS);

If initialization succeeds, the program displays a startup message and then enters the main loop.

Inside the loop, each drawing test or animation is executed as a separate function. Each function clears the screen, draws a shape, text, bitmap, or animation frame, and then updates the display using:

display.display();

The screen must be updated with display.display() after drawing operations because the Adafruit SSD1306 library draws to an internal memory buffer first.

## Main Functions

setup()

Initializes the Serial Monitor, I2C communication, OLED display, random seed, and startup splash screen.

loop()

Runs all graphics tests and animations continuously.

splashMessage()

Shows a startup confirmation message on the OLED display.

testDrawPixel()

Draws individual pixels at fixed coordinates.

testDrawLine()

Draws animated lines from the corner of the screen.

testDrawRect()

Draws multiple nested rectangles.

testFillRect()

Draws filled rectangles using inverse color mode.

testDrawCircle()

Draws concentric circles from the center of the screen.

testFillCircle()

Draws filled circles using inverse color mode.

testDrawRoundRect()

Draws rounded rectangles.

testFillRoundRect()

Draws filled rounded rectangles.

testDrawTriangle()

Draws expanding triangles.

testFillTriangle()

Draws filled triangles using inverse color mode.

testDrawChar()

Displays printable ASCII characters.

testDrawStyles()

Demonstrates different text sizes, colors, and number formatting.

testScrollText()

Tests horizontal and diagonal hardware scrolling.

testDrawBitmap()

Draws a custom 16x16 bitmap logo stored in program memory.

animLogoBounce()

Animates the bitmap logo bouncing around the screen.

animBoatWaves()

Draws a small boat moving over animated sine-wave water.

animSineWave()

Displays an animated sine wave.

animFourierWave()

Displays a waveform made by combining multiple sine waves.

animBarcode()

Creates a moving barcode-style visual effect.

animFakeQR()

Generates a simulated QR-code-style animation.

animVolumeBar()

Displays an animated volume percentage and equalizer bars.

animSmilingBoy()

Draws an animated smiling face with glasses and blinking eyes.

## Project Structure

.
├── src
│   └── main.cpp
└── README.md

For Arduino IDE users, the code can also be used as a standard .ino sketch.

## Customization

You can easily modify this project to create your own OLED interface.

Common changes include:

- Changing the I2C pins
- Changing the OLED I2C address
- Replacing the bitmap logo
- Adding new animations
- Changing animation speed
- Displaying sensor values
- Creating a menu interface
- Showing WiFi, battery, or system status information

## Replacing the Bitmap Logo

The project includes a 16x16 bitmap stored in program memory:

static const unsigned char PROGMEM logo_bmp[]

To replace it, generate a monochrome bitmap array compatible with Adafruit GFX and update:

LOGO_WIDTH
LOGO_HEIGHT
logo_bmp

Make sure the bitmap dimensions match the width and height constants.

## Troubleshooting

If the OLED display is not detected:

- Check the SDA and SCL wiring.
- Confirm that VCC and GND are connected correctly.
- Make sure the display uses the address 0x3C.
- Try running an I2C scanner.
- Verify that the selected pins match your board.
- Install the required Adafruit libraries.
- Check whether your display requires 3.3V or 5V power.

If the display is blank:

- Confirm that the screen resolution is 128x64.
- Check the OLED I2C address.
- Make sure display.display() is called after drawing.
- Verify that the display object uses the correct width and height.
- Try reducing cable length if using long jumper wires.

If the animations are slow:

- Reduce the delay values inside the animation functions.
- Use fewer drawing operations per frame.
- Avoid unnecessary calls to display.display().
- Use simpler shapes or smaller bitmaps.

## Possible Improvements

- Add a menu system controlled by buttons
- Display real sensor data
- Add WiFi connection status
- Create a system dashboard
- Show battery level
- Add icons for embedded projects
- Store multiple bitmap images
- Add frame rate control
- Use the display for IoT device feedback
- Combine the OLED with temperature, humidity, or motion sensors

## Example Applications

- OLED display testing
- Embedded graphics learning
- IoT dashboard prototype
- Sensor data visualization
- Small device user interface
- Animation experiments
- Arduino graphics demonstration
- Wearable or portable device display

## License

This project is open-source and can be used, modified, and distributed freely for personal, educational, and professional purposes.
